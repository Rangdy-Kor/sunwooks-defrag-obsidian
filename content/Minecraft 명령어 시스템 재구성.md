---
publish: true
---

# Minecraft 명령어 시스템 재구성

---

## 명령어 종류

---

### 클라이언트

---

#### copy

---

#### empty

---

`/empty <Item:Item>`
`-as <Target:Entity>` => 플래그 생략 시 기본값 @self
`-limit <Value:Int>` => 플래그 생략 시 기본값 2147483647

#### let

---

`/let <Vriable:Variable>`
`-as <Target:Entity>` => 플래그 생략 시 기본값 @self
`[Operation:Flag] <Value:Float>` => 플래그 생략 시 기본값 `-be` (초기화)
`-be` -> 정의. 인자 생략 시 기본값 0
`-add` -> 덧셈. 인자 생략 시 기본값 1
`-sub` -> 뺄셈. 인자 생략 시 기본값 1
`-mul` -> 곱셈. 인자 생략 시 기본값 2
`-div` -> 나눗셈. 인자 생략 시 기본값 2
`-pow` -> 거듭제곱. 인자 생략 시 기본값 2
`-rem` -> 나머지. 인자 생략 시 기본값 2
`-cut` -> 몫. 인자 생략 시 기본값 2

#### print

---

`/print <Content:TextComponent>`
`-to <Receiver:Player>` => 플래그 생략 시 기본값 @player.all

#### send

---

`/send <Content:String>`
`-to <Receiver:Player>` => 플래그 생략 시 기본값 @player.all
