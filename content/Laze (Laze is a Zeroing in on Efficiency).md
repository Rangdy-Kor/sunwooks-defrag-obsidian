---
publish: true
---

# Laze (Laze is a Zeroing in on Efficiency)

---

- **언어 분류**: 인터페이스 명세 및 설계 언어
- **사용 대상**: 기획자
- **설계 목적**: 기획자의 비정형화된 아이디어를 빠르게 정형화된 텍스트로 변환하여 개발자에게 전달하는 의사소통 언어

## 문법

---

### 구분선

---

3개 이상의 하이픈 (`-`)으로 사용하며, 문서의 구역을 나눈다.

첫 번째 구분선 이전은 비정형적인 Plain Text 형식의 자유로운 제목 구역이기에 하나의 문자열 덩어리로 취급해 파싱을 하지 않는다.

두 번째 구분선 이전까지는 형식이 갖춰진 정의 구역이며, 각종 데이터와 이벤트, 아이템, 창을 정의한다.

두 번째 구분선 이후는 마찬가지로 형식이 갖춰진 선언 구역이며, 명시적인 객체 배치와 액션 정의가 통합된 자체 문법으로 본격적인 인터페이스와 로직을 선언한다. 세 번째 구분선부터는 단순히 가독성을 위한 역할을 한다.

### 들여쓰기

---

정의 구역과 선언 구역에서 계층 구조를 표현하며, 탭 문자나 2개 이상의 공백을 사용한다.

### 주석

---

해시 기호 (`#`)로 시작하는 코드 외적인 의미를 가지는 텍스트를 입력할 수 있다. 여러 줄을 차지하는 주석은 (`###`)로 단락을 감싸 사용할 수 있다. 여러 단락에 처리된 주석 내부에서 2개 이하의 해시 기호는 무시된다.

### 가이드

---

언더바 두 개 (`__`)로 텍스트를 감싸 실제 의미를 가지지 않는 가이드 데이터를 작성할 수 있다. 주석과의 차별점은, 주석은 코드 자체에 대해 메타적으로 설명한다면 가이드는 데이터 차원에서 해당 값에 대해 설명한다.

### 데이터 타입

---

- **String**: 큰따옴표 (`"`) / 작은따옴표 (`'`)로 감싸거나, 예약되지 않은 값을 작성하여 사용할 수 있다.
- **Number**: 숫자를 입력하여 사용할 수 있다. `N..M` 형식으로 범위를 지정할 수 있으며, `@ K`로 최소 간격을 지정할 수 있다. 범위 지정은 실제로 유효한 값으로 해석된다.
- **Boolean**: `yes` / `no`로 사용할 수 있다. `true` / `false`가 아닌 이유는 해당 문법이 기획자가 작성하고 사람이 읽도록 작성되었기 때문이다.
- **None**: `null`, `none`으로 사용할 수 있다.
- **Enum**: 타 타입의 값들을 파이프라인 (`|`)으로 구분하여 사용할 수 있다.
- **List**: 타 타입의 값들을 대괄호 쌍 (`[]`) 안에 넣고 쉼표로 구분하여 사용할 수 있다.

## 예시

---

```
Laze 문법 예시
- 워드프로세서 메뉴 구상

----

# 상태와 리소스를 모두 data namespace로 정의
# @는 item id를 참조

item.main: 
	type: window
    layout: 
    	- container stack-panel
    	- direction top-down
    	- layer.default 1

data.autosave = boolean (default no)
data.document-title = string (default 제목 없음)
data.favorites = boolean (default no)
data.login-state = enum (logged-in | loading | logged-out)
data.current-tabbar = item (default @edit)

data.home-icon = file
data.favorites-icon = file
data.profile-image = file
data.loading-icon = file

item.window.login
	type: window
	# 세부 내용은 생략, 아래 내용 포함
	action: set (data.login-state = logged-in)

item.ribbon-tab(menu-id, menu-label): 
	id: $menu-id
	type: button
		- label $menu-label
	action: set (data.current-tabbar = $menu-id)
	state: static readonly

----

# 속성의 순서는 정해지지 않음
# 개별 속성은 생략 가능하나, ui, action은 필수
# boolean은 yes/no만 사용 가능
# if 조건문은 런타임 계산이 아닌 단순 상태 묘사
# 값의 지정은 단일 값이면 한 줄, 여러 값이면 리스트
# binding은 양방향 동기화

item.title-bar:
	type: title-bar
	state: direction-order 1
	group.titlebar-left:
		type: layout
		state: align left
		item.home: 
			type: button
				- icon $data.home-icon
			action: navigate menu.home
			state: static readonly
		item.auto-save: 
			type: switch
			action: binding $data.autosave
			state: dynamic toggleable
		item.document-title: 
			type: text-box
				- placeholder "제목을 입력하세요"
				- default "제목 없음"
			action: binding $data.document-title
			state: dynamic editable
		item.favorites: 
			type: button
				- icon $data.profile-image
			action: binding $data.favorites
			state: dynamic toggleable
	group.titlebar-right: 
		type: layout
		state: align left
		group.logged-in: 
		 	type: condition
		 	test: when ($data.login-state = logged-in)
		 	item.profile: 
		 		type: button
		 		action: open $item.popup.profile
		 		state: static readonly
		group.logging-in: 
			type: condition
			test: when ($data.login-state = loading)
			item.loading: 
				type: display
					- icon $data.login-loading
				state: static readonly
		group.logged-out: 
			type: condition
			test: when ($data.login-state = logged-out)
			item.log-in: 
				type: button
					- label "로그인"
				action: open $item.window.login
				state: static readonly				

----

# state 생략 시 기본값은 언제나 static readonly

item.ribbon-menu: 
	type: tab-bar
	state: 
		- section direction-order 2
		- align justify
	item.file: 
	    type: button
	    	- label "파일" 
	    action: open sidebar.file
		item.file-sidebar:
			type: sidebar
	        section: 
	        	- direction-order/top-down 
	        	- section/layer-order/2
				# 세부 내용은 생략
	item.edit: item.ribbon-tab(edit, "편집")
	item.view: item.ribbon-tab(view, "보기")
	item.insert: item.ribbon-tab(insert, "삽입")
	item.reference: item.ribbon-tab(reference, "참조")
	item.style: item.ribbon-tab(style, "서식")
	item.pages: item.ribbon-tab(page, "페이지")
	item.review: item.ribbon-tab(review, "검토")
	item.tools: item.ribbon-tab(tools, "도구")
	item.extensions: item.ribbon-tab(extension, "확장")
```
