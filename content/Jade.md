---
publish: true
---

# Jade

---

> [!WARNING] 실제 개발 계획은 정해지지 않았으며, 개인 취미 활동 및 설계 연습 목적으로 작성되었습니다.

## 데이터 저장 및 파일 시스템 구조

---

**로컬 파일 시스템**

- **포맷**: `.md` (Markdown)
- **구조**: UUID 분할 디렉토리 (8/4/4/4 구조)
- **파일명**: UUID 마지막 12자리 고정
- **메타데이터**: 프론트매터에 기록

**로컬 SQLite**

- **매핑**: UUID와 실제 경로 간의 매핑 테이블 관리
- **그래프**: 프론트매터의 `parent` 메타데이터 기반으로 폴더 없는 논리적 트리 구조 계산
- **검색**: FTS5를 활용한 전면 텍스트 검색 및 제목 인덱싱

## 동기화 및 충돌 해결 전략

---

- **변경 추적**: 본문 (`Yjs`)와 프론트매터 (JSON CRDT)를 구분하여 구역별 CRDT 적용
  - 삭제 시 물리적 삭제 대신 삭제 마커 처리 후 휴지통에서만 노출
- **동기화 흐름**:
  - **Local**: 변경 사항 발생 시 SQLite의 미동기화 큐에 적재
  - **Remote**: WebSocket을 통해 CRDT 변경 이력 배포 및 중앙 서버 (PostgreSQL + Object Stroage) 스냅샷 업데이트
  - **Security**: 모든 과정은 E2EE (종단간 암호화) 적용

## 편집 환경

---

- **Editor**: Code Mirror 6 기반 WYSIWYG 구현
- **Token Management**: 비활성 상태에서 마크다운 토큰을 숨겨 시각적 노이즈 제거
- **Paresser**: Remark를 활용한 마크다운 파싱 및 렌더링

| **분류**       | **기술 스택**                           | **비고**          |
| ------------ | ----------------------------------- | --------------- |
| **Platform** | Electron, React, React Native       | 크로스 플랫폼 대응      |
| **Editor**   | Code Mirror 6, Remark               | WYSIWYG 및 MD 파싱 |
| **Database** | SQLite (Local), PostgreSQL (Server) | 로컬 우선 및 인덱싱     |
| **Sync**     | Yjs (CRDT), WebSocket               | 실시간 동기화 및 충돌 방지 |
| **Backend**  | Rust / Go, Object Storage           | 고성능 처리 및 파일 저장  |

**텍스트 편집 및 논리 계층**

- 마크다운 파일 저장: 언제나 최종 파일은 .md 포맷으로 저장
- WYSIWYG: Code Mirror 6를 통해 마우스 커서가 위치하지 않았을 때 토큰을 숨김
- 프론트매터 기반 계층 구조: 폴더 대신 parent 프론트매터에 기록된 링크 메타데이터로 논리 트리 구조 관리

**데이터 저장 및 동기화**

- 로컬 우선: 사용자의 작업 공간은 언제나 로컬 기기
- UUID 부여: 각 파일에 UUID를 부여하고 프론트매터에 기록
- UUID 기반 디렉토리 구조: UUID의 8/4/4/4 부분을 나눈 폴더 구조를 생성하며, 파일의 제목은 마지막 12자리 ID로 고정
- CRDT 변경 전파: 단순 파일 덮어쓰기가 아닌 변경 연산 자체를 병합
- 중앙 서버 동기화: 서버로 모인 로컬 변경분을 각 클라이언트로 다시 배포
- 삭제 마커: 로컬에서 파일이 삭제될 시 물리적으로 삭제하지 않고 삭제 마커 처리하여 앱 내부에서는 휴지통에 표시
- SQLite 단일 인덱스 DB:
  - 파일 UUID ←> 경로 매핑
  - 제목 인덱스
  - 링크 그래프 계산
  - 검색 인덱스 (FTS5)
  - 미동기화 변경 큐
  - 삭제 마커 관리
- 파일 내부 영역별 CRDT 전담:
  - 프론트매터 → JSON 문서 CRDT
  - 본문 → 텍스트 CRDT (Yjs)
  - metadata → 별도 레코드
- 서버 저장 요소: 최신 스냅샷 + CRDT 변경 이력 모두
- E2EE (종단간 암호화) 사용

**기술 스택**

- 클라이언트:
  - Electron + React (데스크톱) | React Native (모바일)
  - CodeMirror 6
  - SQLite | SQLite local DB
  - Yjs
  - Remark
- 서버:
  - Rust / Go
  - PostgreSQL (메타데이터)
  - Object Storage (파일 스냅샷)
  - WebSocket 실시간 동기화
