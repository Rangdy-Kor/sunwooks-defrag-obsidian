---
publish: true
---

# RUBIDIAN ULTRABOOK

---

```table-of-contents
```

## HARDWARE

---

### CENTRAL

---

|      제품군      |            모델             |
| :-----------: | :-----------------------: |
| **Main Unit** | Samsung Galaxy Book 6 Pro |
|    **CPU**    |    Intel Core Ultra 3     |
|    **GPU**    |      Intel Arc iGPU       |
|    **RAM**    |       32GB LPDDR5X        |
|    **SSD**    |      1TB NVMe Gen 5       |

### PERIPHERAL

---

|      제품군       |                                모델                                |          비고          |
| :------------: | :--------------------------------------------------------------: | :------------------: |
| **무선 네트워크 모듈** |                   AMD Wi-Fi 7 / Bluetooth 5.4                    |          -           |
|   **디스플레이**    |        16” Dynamic AMOLED 2X Touch 2880x1800 16:10 120Hz         |          -           |
|    **키보드**     | Built-in Full Size Keyboard with Per-Key Backlight & Copilot Key | US International ISO |
|    **마우스**     |                       Logitech MX Master 4                       |          -           |
|   **마우스 패드**   |                    Artisan Hayate Otsu Soft M                    |          -           |

## SOFTWARE

---

### SYSTEM / DRIVER & CONTROL

---

|        분류군        |                                        소프트웨어                                        |    라이선스     |      패키지 원본       | 비고  |
| :---------------: | :---------------------------------------------------------------------------------: | :---------: | :---------------: | :-: |
|     **운영체제**      |                                Microsoft Windows 11                                 | Windows Pro |   Pre-installed   |  -  |
|    **칩셋 드라이버**    | Intel Chipset Driver<br>Intel Management Engine Interface<br>Intel Serial IO Driver |      -      |  Samsung Update   |  -  |
|   **그래픽 드라이버**    |             Intel Arc Graphics Driver<br>Intel Graphics Command Center              |      -      |  Samsung Update   |  -  |
|    **관리 드라이버**    |                       Samsung Settings<br>Samsung Device Care                       |      -      |  Samsung Update   |  -  |
|    **AI 드라이버**    |                         Intel Gaussian & Neural Accelerator                         |      -      |  Samsung Update   |  -  |
|   **사운드 드라이버**    |                        Realtek High Definition Audio Driver                         |      -      |  Samsung Update   |  -  |
|                   |                                   Dolby Atmos SW                                    |      -      |  Samsung Update   |  -  |
| **유선 네트워크 드라이버**  |                       Realtek 2.5G Ethernet Controller Driver                       |      -      |  Samsung Update   |  -  |
| **무선 네트워크 드라이버**  |                    Intel Wi-Fi 7 (BE200) & Bluetooth 5.4 Driver                     |      -      |  Samsung Update   |  -  |
|  **SD 카드 드라이버**   |                         Genesys Logic SD Card Reader Driver                         |      -      |  Samsung Update   |  -  |
| **HID 드라이버 및 제어** |                                    Logi Option+                                     |      -      | Official Homepage |  -  |
|                   |                            Razer Synapse<br>Razer Chroma                            |      -      | Official Homepage |  -  |
|                   |                                Samsung Multi Control                                |      -      |  Samsung Update   |  -  |
|   **프린터 드라이버**    |                                  Epson EcoTank Pro                                  |      -      | Official Homepage |  -  |
|   **NVMe 드라이버**   |                           Samsung Magician & NVMe Driver                            |      -      |  Samsung Update   |  -  |
|  **생체 인식 드라이버**   |                              Goodix Fingerprint Driver                              |      -      |  Samsung Update   |  -  |

### SECURITY / PRIVACY & DATA PROTECTION

---

|         분류군         |             소프트웨어              |            라이선스            |      패키지 원본       |                                                          비고                                                          |
| :-----------------: | :----------------------------: | :------------------------: | :---------------: | :------------------------------------------------------------------------------------------------------------------: |
|  **안티 바이러스 소프트웨어**  |       ESET Home Security       | ESET Home Security Premium |      Winget       |                                       AppCheck 상호 예외 설정<br>WebProtection 비활성화                                        |
|  **안티 랜섬웨어 소프트웨어**  |       CheckMAL AppCheck        |        AppCheck Pro        |      Winget       |                                                    ESET 상호 예외 설정                                                     |
|  **네트워크 보안 소프트웨어**  |         ESET Firewall          | ESET Home Security Premium |      Module       |                                                       ESET 내장                                                        |
|  **네트워크 관제 소프트웨어**  |      SecureMix GlassWire       |     GlassWire Premium      |       Scoop       |                                                     방화벽 기능 비활성화                                                      |
|    **칩입 탐지 시스템**    | ESET Network Attack Protection | ESET Home Security Premium |      Module       |                                                       ESET 내장                                                        |
| **설치형 악성 코드 제거 도구** |          Malwarebytes          |    Malwarebytes Premium    |      Winget       |                                             실시간 보호 비활성화<br>주 1회 자동 전체 검사                                             |
| **포터블 악성 코드 제거 도구** |          Malware Zero          |             -              | Official Homepage |                                                    감염 의심 시 수동 검사                                                     |
|   **블로트웨어 소거 도구**   |             구라제거기              |             -              | Official Homepage |                                                 블로트웨어 설치 의심 시 수동 실행                                                  |
|     **VPN 서비스**     |           ProtonVPN            |       ProtonVPN Plus       |      Winget       | WireGuard UDP 프로토콜<br>Kill Switch Non-Permanent 활성화<br>NetShield 비활성화<br>VPN Accelerator 활성화<br>일부 VPN 차단 사이트 분할 터널링 |
|    **비밀번호 관리자**     |           Bitwarden            |             -              |       Scoop       |                                             Vaultwarden NAS Self-hosting                                             |
|     **컨텐츠 차단기**     |            AdGuard             |      AdGuard Familys       |      Winget       |                WFP 드라이버 모드 기능 사용<br>HTTPS 필터링 활성화<br>EV 인증서 웹사이트 필터링 활성화<br>AdGuard DNS-over-QUIC 사용                 |
|    **클라우드 아카이브**    |             IDrive             |   IDrive Personal 100TB    |      Winget       |                                                       분기 1회 백업                                                       |

### WORKSPACE / OFFICE

---

|      분류군      |           소프트웨어           |             라이선스              |      패키지 원본       |                   비고                    |
| :-----------: | :-----------------------: | :---------------------------: | :---------------: | :-------------------------------------: |
|  **워드프로세서**   |    Microsoft Word 2026    |     Microsoft 365 Premium     | Official Homepage |                    -                    |
|               |    Hancom Hangul 2024     |          Hancom Docs          |     Homepage      |                    -                    |
|  **프레젠테이션**   | Microsoft PowerPoint 2026 |     Microsoft 365 Premium     | Official Homepage |                    -                    |
|  **스프레드시트**   |   Microsoft Excel 2026    |     Microsoft 365 Premium     | Official Homepage |                    -                    |
|  **PDF 리더**   |     Adobe Acrobat Pro     | Adobe Creative Cloud All Apps | Official Homepage |                    -                    |
|   **간편 메모**   |        Google Keep        |        Google AI Ultra        |    Vivaldi PWA    |                    -                    |
|  **협업 프로젝트**  |          Notion           |          Notion Plus          |       Scoop       |                    -                    |
| **메일 클라이언트**  |          Outlook          |     Microsoft 365 Premium     | Official Homepage |                    -                    |
| **클라우드 스토리지** |          DropBox          |    DropBox Essentials 3TB     |       Scoop       | 파일 공유 & 동기화, 오피스 작업용<br>파일 저장 및 백업은 NAS |
|               |       Google Drive        |        Google AI Ultra        |      Winget       |   갤러리 동기화, 외부 협업용<br>미디어는 NAS에 추가 백업    |
|  **AI 서비스**   |          ChatGPT          |          ChatGPT Pro          |      Winget       |                    -                    |
|               |          Claude           |          Claude Max           |       Scoop       |                    -                    |
|               |          Gemini           |        Google AI Ultra        |    Vivaldi PWA    |                    -                    |

### CREATIVE / STUDIO

---

|          분류군           |       소프트웨어        |             라이선스              |      패키지 원본       |                 비고                 |
| :--------------------: | :----------------: | :---------------------------: | :---------------: | :--------------------------------: |
|     **데스크탑 퍼블리싱**      |   Adobe InDesign   | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |
|     **비트맵 그래픽 툴**      |  Adobe Photoshop   | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |
|      **벡터 그래픽 툴**      | Adobe Illustrator  | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |
| **영상 편집 / 영상 색상 보정 툴** |  DaVinci Resolve   |    DaVinci Resolve Studio     |      Winget       | XML/EDL 내보내기를 통한 Adobe CC와의 작업물 공유 |
|      **음향 편집 툴**       |   Adobe Audition   | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |
|   **특수 효과 / 모션 그래픽**   | Adobe After Effect | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |
|     **사진 색상 보정 툴**     |  Adobe Lightroom   | Adobe Creative Cloud All Apps | Official Homepage |                 -                  |

### DEV STACK / EDITOR

---

|       분류군        |              소프트웨어               |            라이선스             |      패키지 원본       |                                                                                             비고                                                                                             |
| :--------------: | :------------------------------: | :-------------------------: | :---------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|    **단순 메모장**    |             Notepads             |              -              |       Scoop       |                                                                                             -                                                                                              |
|   **마크다운 편집기**   |              Typora              |         Typora EULA         |       Scoop       |                                                                              단일 파일 마크다운 파일 편집 및 텍스트 기반 문서 작업                                                                               |
| **개인 지식 관리 시스템** |             Obsidian             |              -              |       Scoop       | 지식 관리 시스템 구축<br>Self-hosted Live Sync Plugin를 통해 NAS Container 동기화<br>Quartz & Quartz Syncer Plugin과 GitHub & Vercel 를 통해 정적 웹 게시<br>Obsidian-Remote NAS Container Package를 통해 외부 환경 웹 액세스 |
|   **텍스트 편집기**    |            Notepad++             |              -              |       Scoop       |                                                                                 대용량 텍스트 파일 분석 및 단순 텍스트 수정                                                                                  |
|    **코드 에디터**    |        Visual Studio Code        |              -              |       Scoop       |                                                               LaTeX 편집 (LaTeX Workshop Extension)<br>포맷팅 및 스크립팅<br>SSH 원격 접속                                                               |
|   **통합 개발 환경**   |        Visual Studio IDE         | Visual Studio Professional  |      Winget       |                                                                        C / C++ | Windows App | Native Programing                                                                         |
|                  |         JetBrains Rider          | JetBrains All Products Pack | JetBrains Toolbox |                                                                           C# / F# | Game Engine | .NET Backend                                                                           |
|                  |       JetBrains RustRover        | JetBrains All Products Pack | JetBrains Toolbox |                                                                       Pure Rust | Rust Backend | System Programing                                                                       |
|                  | JetBrains IntelliJ IDEA Ultimate | JetBrains All Products Pack | JetBrains Toolbox |                              Java / Kotlin | JVM Backend <br>Pure Python | Python Backend | Data Analysis | AI Model Training<br>JS / TS | Web Frontend                               |
|  **IDE 설치 관리**   |        JetBrains Toolbox         |              -              |      Winget       |                                                                                             -                                                                                              |
|   **LaTeX 엔진**   |             TeX Live             |              -              |       Scoop       |                                                                                             -                                                                                              |
|  **데이터베이스 관리**   |             Navicat              |       Navicat Premium       |       Scoop       |                                                                                         종합 설계 및 관리                                                                                         |
|                  |    JetBrains IDE 내장 DataGrip     | JetBrains All Products Pack |      Module       |                                                                                       개발 단계 조회 및 확인                                                                                        |
|   **버전 관리 엔진**   |               Git                |              -              |       Scoop       |                                                                                             -                                                                                              |
| **버전 관리 클라이언트**  |            GitKraken             |        GitKraken Pro        |       Scoop       |                                                                                     메인 레포지토리 / 브랜치 관리                                                                                      |
|                  |     IDE 내장 및 VS Code 확장 Git      |              -              |      Module       |                                                                                   단순 커밋 / 푸시 및 수정 이력 확인                                                                                    |

### UTILITY / EXTENTION

---

|        분류군        |        소프트웨어         |              라이선스              |   패키지 원본    |                            비고                            |
| :---------------: | :------------------: | :----------------------------: | :---------: | :------------------------------------------------------: |
| **디스크 복구 소프트웨어**  |       R-Studio       |       R-Studio Standard        |   Winget    |                            -                             |
|   **터미널 에뮬레이터**   |       WezTerm        |               -                |    Scoop    |                            -                             |
|   **CLI 유틸리티**    |         eza          |               -                |    Scoop    |                          ls 대체                           |
|                   |         bat          |               -                |    Scoop    |                          cat 대체                          |
|                   |         fzf          |               -                |    Scoop    |                       대화형 인터페이스 도구                       |
|                   |        zoxide        |               -                |    Scoop    |                          cd 대체                           |
|                   |       ripgrap        |               -                |    Scoop    |                          rg 대체                           |
|                   |          fd          |               -                |    Scoop    |                         find 대체                          |
|                   |        delta         |               -                |    Scoop    |                       git diff 대체                        |
|                   |         dust         |               -                |    Scoop    |                          du 대체                           |
|                   |        bottom        |               -                |    Scoop    |                       CLI용 작업 관리자                        |
|  **터미널 커스터마이징**   |       Starship       |               -                |    Scoop    |                            -                             |
|  **인라인 권한 부여자**   |        Gsudo         |               -                |    Scoop    | $PROFILE에 sudo 명칭으로 함수 등록<br>Windows 기본 개발자 기능 Sudo 비활성화 |
|    **패키지 관리자**    |        Scoop         |               -                |   GitHub    |                            -                             |
|   **IDE 설치 관리**   |  JetBrains Toolbox   |               -                |   Winget    |                            -                             |
|                   |       Innounp        |               -                |    Scoop    |                            -                             |
| **시스템 요약 정보 출력**  |      Fastfetch       |               -                |    Scoop    |                            -                             |
|    **파일 관리자**     |    Directory Opus    |  Directory Opus Professional   |   Winget    |                            -                             |
|   **드라이브 마운트**    |       RaiDrive       |     RaiDrive Professional      |   Winget    |                            -                             |
|   **압축 파일 관리자**   |       BandiZip       |          BandiZip Pro          |    Scoop    |                            -                             |
|                   |         7zip         |               -                |    Scoop    |                     Scoop 내부 패키지 관리용                     |
|    **파일 복사기**     |       FastCopy       |               -                |    Scoop    |                    Directory Opus 연동                     |
|    **파일 검색기**     |      Everything      |               -                |    Scoop    |                    Directory Opus 연동                     |
|    **작업 관리자**     |   System Informer    |               -                |    Scoop    |                            -                             |
| **하드웨어 진단 및 분석**  |       Hwinfo64       |               -                |    Scoop    |                            -                             |
| **디스크 모니터링 및 진단** |  Crystal Disk Info   |               -                |    Scoop    |                            -                             |
|    **운영체제 확장**    |      PowerToys       |               -                |    Scoop    |                            -                             |
|  **시스템 커스터마이징**   |   Winaero Tweaker    |               -                |    Scoop    |                            -                             |
|   **창 관리 프로그램**   |      WindowGrid      |               -                |   Winget    |                        격자 기반 창 관리                        |
|                   |       AltSnap        |               -                |   Winget    |                        스냅 기능 편의성                         |
|  **다크 모드 자동 전환**  |     AutoDarkMode     |               -                |    Scoop    |                            -                             |
|    **마우스 제스처**    |   StrokesPlus.net    |               -                |    Scoop    |                            -                             |
|   **클립보드 동기화**    |     ClipCascade      |               -                |   GitHub    |                      NAS 중심 P2S 방식                       |
|  **P2P 파일 전송기**   |  Google QuickShare   |               -                |   Winget    |                            -                             |
|  **입력 장치 에뮬레이터**  |    Unified Remote    |      Unified Remote Full       |   Winget    |                            -                             |
|  **화면 녹화 프로그램**   |      OBS Studio      |               -                |    Scoop    |                            -                             |
|     **캡처 도구**     |       Snipaste       |               -                |    Scoop    |                            -                             |
|    **이미지 뷰어**     |      BandiView       |         BandiView Pro          |   Winget    |                            -                             |
|   **미디어 플레이어**    |   PotPlayer Global   |               -                |   Winget    |                            -                             |
|      **번역기**      |  DeepL Translation   | DeepL Translation Pro Ultimate |   Winget    |                            -                             |
|    **문장 교정기**     |     DeepL Write      |    DeepL Write Pro Ultimate    |   Winget    |                            -                             |
|    **문법 검사기**     |      Grammarly       |         Grammarly Pro          |    Scoop    |                            -                             |
|                   | 바른한글 (구 부산대 맞춤법 검사기) |               -                | Vivaldi PWA |                            -                             |

### LIFE STYLE / COMMUNICATION & NETWORK

---

|      분류군      |     소프트웨어      |          라이선스           |   패키지 원본    |                                                                비고                                                                |
| :-----------: | :------------: | :---------------------: | :---------: | :------------------------------------------------------------------------------------------------------------------------------: |
|  **웹 브라우저**   |    Vivaldi     |            -            |   Winget    | 내장 마우스 제스처 비활성화<br>DarkReader / AdGuard Browser Assistant / Global Speed / Bitwarden Extension<br>Winget을 통한 운영체제 기본 프로그램 통합 최적화 |
| **인스턴트 메신저**  |    Discord     |      Discord Nitro      |    Scoop    |                                                                -                                                                 |
|               |   KakaoTalk    |      TalkCloud 1TB      |    Scoop    |                                                 TalkCloud는 대화, 사진, 동영상 백업용으로만 사용                                                 |
|               |     Slack      |        Slack Pro        |    Scoop    |                                                                -                                                                 |
| **화상 통화 서비스** | Zoom Workplace | Zoom Workplace Business |    Scoop    |                                                                -                                                                 |
|               |  Google Meet   |     Google AI Ultra     | Vivaldi PWA |                                                                -                                                                 |
|    **메시지**    | Google Message |     Google AI Ultra     | Vivaldi PWA |                                                                -                                                                 |
