---
publish: true
---

# Miencraft NEO Edition

---

## 프로필

---

| **프로필**    | **Minecraft: NEO Edition**                                                                                                                               |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **개발 언어**  | C++ (물리 연산 / 렌더링 엔진)<br>C# (인게임 콘텐츠 / 상위 차원 로직)                                                                                                          |
| **플랫폼 언어** | C# (데스크탑 전용)<br>TypeScript (데스크탑 및 모바일)                                                                                                                  |
| **플랫폼**    | Microsoft Windows | Xbox One | Xbox Series X|S<br>macOS | iPadOS | iOS<br>Linux | Android<br>Nintendo Switch | Nintendo Switch 2<br>PlayStation 5 |
| **장르**     | 오픈 월드 | 샌드박스 | 서바이벌                                                                                                                                    |

> [!IMPORTANT] IMPORTANT<br>실제 구현 계획은 현재까지 존재하지 않으며, 개인적 취미 활동 및 설계 연습 목적으로 작성되었습니다.

## 개요

---

Minecraft: NEO Edition은 이분화된 Minecraft의 생태계를 단일 생태계로 통합하며, 현대 시스템 공학의 정수를 Minecraft에 이식하겠다는 목적으로 설계된 가상의 Minecraft 신규 에디션 설계서이다.

## 시스템

---

### 개발

---

Minecraft: NEO Edition은 Bedrock Edition에서 사용한 자체 복셀 게임 엔진인 RenderDragon을 사용한다. Unity, Unreal 등 표준 사용 엔진은 폴리곤 기반 게임 엔진으로서 블록 (복셀) 기반 게임인 Minecraft에는 적합하지 않았다.

그래픽 렌더링, 물리 엔진 등 게임의 실행 속도를 결정하는 곳에는 Bedrock Edition과 같이 C++을 사용한다. C++은 Java와 달리 런타임이 없으면서도, 가비지 컬렉션 없이 메모리를 직접 조작할 수 있어 실행 속도와 최적화 측면에서 더 유리하기 때문이다.

반면 대부분이 C++로 제작된 Bedrock Edition과는 달리, 고차원 로직, 인게임 콘텐츠 등에는 C#을 사용한다. C#은 .NET 10 런타임을 사용하며, 가비지 컬렉션이 있어 최적화 측면에서는 C++보다 부족한 면이 분명히 존재하나, 그럼에도 불구하고 C#을 선택한 이유에는 크게 3가지가 존재한다.

첫째, 발전된 C#의 완성도이다. 2011년, Pocket Edition (Bedrock Edition의 전신)의 개발 당시에는 C#은 현재의 .NET이 아닌 .NET Framework라는 Windows에 종속된 전용 런타임에서 구동되었다. 또한 실행 속도가 현저히 느리고, 가비지 컬렉터 호출에 의한 끊김이 게임 개발에는 치명적인 요인으로 작용했다. 이 때문에 크로스 플랫폼과 저사양 기기 구동을 지원해야 하는 Bedrock Edition은 다른 선택지가 마땅치 않았기에 C++이라는 최적화와 디버깅의 양날의 검을 선택한 것이다. 그러나 15년이 지난 현재, 상황은 완전히 뒤바뀌었다. .NET은 .NET Core를 거쳐 크로스 플랫폼 언어로 성장하였으며, C# 또한 JIT 컴파일러의 발전과 저수준 메모리 제어 기능을 통해 Unity의 공식 언어가 될 만큼 대형 게임 개발에 사용할 정도로 성숙한 언어가 되었다. 이 시점에서 C#이 아닌 C++이라는 저수준 언어로 개발한다는 것은, 부분적으로 높은 성능을 확보할지 언정 프로젝트의 규모에 따라 기하급수적으로 상승하는 디버깅 난이도와 긴 개발 시간, 그리고 비용을 감수해야 하는 선택지이라 말해도 과언이 아니다. 물론 게임의 핵심 엔진과 물리 연산 측면에서는 런타임과 GC (가비지 컬렉션)이 없는 C++이 전체적으로 더 유리한 선택지이나, 고차원 로직의 경우 최적화 기법이 적용된 C#으로도 충분히 대형 게임을 개발할 수 있다는 것이 Unity를 통해 증명된 바가 있다.

둘째, Java와의 유사성이다. Minecraft의 문화적 중심인 Java Edition의 개발 언어인 Java는, 클래스 기반의 객체 지향성, 정적 타입 시스템, 가비지 컬렉션, 런타임 구동 등 대표적인 특징을 C#과 공유한다. 이 두 언어가 전체적으로 유사하다 말하기는 힘들 수도 있으나, C++ 등의 다른 언어에 비해서는 기존 Java Edition 모더 및 개발자들의 적응, 그리고 신규 생태계 구축에 도움을 줄 것이라 판단할 여지가 충분하다.

셋째, C++과의 연동성이다. 앞서 서술하였듯이 NEO Edition의 핵심 심장부는 여전히 C++로 개발된다. 이런 상황에서 C#은  역사적으로 개발 당시부터 C++과의 상호 운용성을 염두에 둔 언어이며, Unity라는 C++과 C#의 조합으로 개발된 상용 엔진의 선례까지 존재한다. 특히 이러한 점은 .NET의 최신 버전으로 향할 수록 더더욱 부각되는데, .NET 10 기준 `[LibraryImport]`와 함수 포인터를 통해 오버헤드 및 레이턴시 (지연 시간)을 최소화하여 개발할 수 있으며 NEO Edition은 그것을 사용한다. 이러한 점 때문에 NEO Edition은 핵심 개발 언어로 C++과 더불어 C#을 선택한 것이다.

C++의 사용 시 앞서 언급한 함수 포인터의 사용을 제외하고는 반드시 스마트 포인터를 사용한다. 이는 Null 포인터 역참조 등 심각한 메모리 오류를 방지하기 위함이다. 또한 메모리 풀링 (Pooling)과 단편화 방지를 위하여 최적화가 필요한 결정적인 부분에 커스텀 얼로케이터를 도입한다.

이외에도 실행 환경 별로 화면을 그리기 위한 그래픽 라이브러리를 전부 다른 것을 사용해야 한다는 문제가 있으며, Bedrock Edition은 실제로 각 실행 환경 별로 서로 다른 그래픽 라이브러리를 통해 개발하였다. 허나 이는 긴 개발 시간, 그리고 비용의 상승으로 이어진다. 때문에 NEO Edition은 BGFX라는 추상화 레이어를 더하여, DirectX (MS), Vulkan (Linux), Metal (Apple), AGC (PS), NVN (NS) 환경을 모두 하나의 통합된 코드 베이스로 개발한다.

### 배포

---

Minecraft: NEO Edition의 내부 아키텍처는 배포 단계에서부터 실행 파일 본체와 모딩 레이어를 철저히 분리한다. 게임 실행 파일이 위치한 본체는 .NET의 최신 기능인 Native AOT를 통해 기계어로 미리 컴파일된 상태로 배포하여 실행 성능과 메모리 효율, 그리고 역컴파일 방지라는 보안성을 확보한다. 모딩 레이어는 모딩 파일의 동적 로드 확장성이 필요하기에, 실시간으로 중간 언어로 변환 후 컴파일하는 전통적인 JIT 방식을 사용한다. 소스 코드는 난독화하지 않으나, `rd.xml`을 미포함함으로서 안정성을 떨어트리고 예기치 못한 크래시의 주범이 되는 리플렉션 지원을 제거한다.

Native AOT 위에 JIT를 임베디드 런타임으로 구동하여 이 둘을 공존시킨다. Native AOT 내부에서 `nethost.dll`을 사용하여 별도의 JIT 런타임을 구동하며, 게임 실행 시 모드 폴더를 스캔하고 `hostfxr` 라이브러리를 통해 JIT 런타임을 초기화하여 모드들을 로드하는 기법을 사용한다. 이는 Unity가 C++ 엔진 위에서 Mono/IL2CPP를 구동하는 방식과 유사하면서도, .NET 표준을 따른다는 장점이 존재한다. 이 두 실행 환경의 데이터 교환 시에는 단순 복사 (Copy)가 아닌 Zero-copy를 위하여 `Shared Memory`, 그리고 `Direct Pointers`를 사용하여 성능을 확보한다.

실행 파일의 크기를 줄이고 모바일 / 콘솔 환경에서 로딩 속도를 개선하기 위해 Native AOT 배포 시 사용하지 않는 코드를 최종 네이티브 바이너리에서 제거하는 Trimming 기술을 적용한다. Trimming의 부작용 중 하나인 리플렉션의 오인식 제거는, Native AOT 내부에서도 타입 리플렉션 대신 소스 생성기를 적극적으로 사용하여 해결한다.

허나 역컴파일과 리플렉션은 Java Edition 모딩 생태계의 핵심 기술이기에 이에 익숙한 모더들에게 큰 제약이 되어 생태계 구축이 어려워질 수 있다는 타당한 우려가 나올 수 있다는 점을 인지하고 있다. 때문에 NEO Edition은 이를 대체할 공식 SDK와 API, 모드 로더, 소스 생성기를 지원하며, 이는 아래 유저 모딩 부문에서 자세히 서술되어 있다.

### 유저 모딩

---

Minecraft: Java Edition의 모딩은 근본적으로 게임 소스 코드를 역컴파일하여 유저들이 제작한 모드 로더를 통해 모드 파일을 게임 로딩 직전 런타임 단계에서 주입하는 리플렉션 방식을 사용하였다. 허나 이는 모드 간의 충돌이 빈번하고 안정성이 떨어졌으며, 로딩 시간의 증가와 상당한 메모리 점유라는 단점까지 앓고 있었다. 이를 해결하기 위해, Minecraft: NEO Edition은 앞서 언급한데로 Native AOT로 역컴파일을 차단하고, 리플렉션의 지원을 제거하였으며, 이들의 대안으로 Minecraft .NET SDK와 MOM (Microsoft Open Modding) API, 그리고 내장된 모드 로더와 소스 생성기를 제시한다.

Minecraft .NET SDK에는 다양한 개발 편의성과 보안, 안정성을 위한 기능이 탑재되어 있다. 그 예시로는 모드마다 독립적인 `AssemblyLoadContext`를 부여하는 어셈블리 격리, 모드 별 행위 기반 권한 제어, NuGet 지원, Visual Studio 공식 템플릿, 게임의 재시작 없이 C# 코드 수정을 반영할 수 있는 .NET Hot Reloading 등이 존재한다.

MOM API에는 Event Bus 시스템과 IMC (Inter-Mod Communication) 통신 규격, 추상화 레이어의 지원이 포함되어 있다. 모드 로더의 경우 Java Edition의 Mixin과 달리 소스 생성기를 통해 런타임이 아닌 컴파일 단계에서 모드를 로딩하여 런타임 성능을 대폭 향상시킴은 물론, `INotifyPropertyChanged` 등을 구현할 때 코드 자동 생성, 잘못된 참조의 컴파일 단계 탐지, 로딩 시간의 개선 등 모더의 작업량을 줄이는 효과를 불러일으킨다.

C++ 기반의 모딩은 안정성의 하락과 보안 위험에 대한 우려에 따라 지원하지 않는다. C# 기반의 모드들도 각자의 격리된 샌드박스 환경에서 실행하고, MOM API로만 통신하여 게임 실행 환경을 탈출해 호스트 환경을 침범하는 일을 방지한다.

C# 모듈 (DLL)의 동적 로드가 허용되는 PC 환경에서는 C#을 통한 모딩이 지원되나, 운영체제의 특성 상 이가 지원되지 않는 모바일 / 콘솔에서는 TypeScript를 통한 애드온 스크립팅을 지원한다. 이에 대한 자세한 내용은 아래 유저 스크립팅 부문에 서술되어 있다.

### 유저 스크립팅

---

Minecraft: NEO Edition의 유저 콘텐츠는 Java Edition의 문화에 가까운 C# 모딩 이외에도, Bedrock Edition의 문화인 TypeScript 기반의 애드온 스크립팅을 지원한다. 이러한 선택을 하게 된 계기로는 크게 두 가지가 존재한다.

첫째, 모바일 / 콘솔의 지원이다. C# 모드는 강력한 수정 범위와 성능을 제공하나, Minecraft 사용자의 상당수를 차지하는 모바일 유저, 그리고 콘솔 유저는 OS 매커니즘 상 C#의 동적 로드가 허용되지 않아 사용이 불가능하다는 문제가 있었다. 그렇기에 Bedrock Edition에서도 사용된 자체 엔지인 Chakra JS 런타임 엔진을 게임 안에 직접 번들링한 후, TypeScript를 JavaScript로 컴파일하여 동적 로드를 진행해 모바일 / 콘솔에서 애드온 구동을 가능케 하였다.

둘째, 거대한 생태계와 개발 인력이다. TypeScript는 전세계 웹 개발의 표준이며, 웹 개발자는 전체 개발자 중 가장 많은 숫자를 자랑하는 직종이다. 또한 TypeScript는 MS 자사의 언어이기에, 게임을 통해 실무에 사용할 언어를 익힐 수 있다는 강력한 마케팅 포인트를 내세울 수 있으며, 일반 개발자나 입문자들이 가볍게 접근할 수 있는 게이트웨이 역할을 수행하여 생태계의 기반을 구축하는 효과를 수행한다.

정리하자면 이렇다. DLL 동적 로드가 허용되는 PC 환경에서는 C#을 통한 대규모 코드 개편을 허용한다. 반면 이가 허용되지 않는 모바일 환경에서는 TypeScript를 통한 애드온 스크립팅을 지원한다. PC에서는 애드온을 설치할 수 있으나, 반대로 모바일에서는 C# 모드를 설치할 수 없다. 또한 C# 모드와 TypeScript 애드온은 서로의 API를 호출하여 상호 운용할 수 있다.

TypeScript 애드온 개발을 위한 Minecraft TS Scripting Extension을 VS Code 확장으로 지원한다. 해당 Extension은 TypeScript Extension을 사전 요구하며, Minecraft용 API에 대한 문법 강조와 개발 지원을 제공하기 위해 고려되었다. 또한 Minecraft NEO CLI라는 터미널 시스템을 지원하며, 이를 통해 개발자들은 프로젝트를 생성하고 빌드할 수 있다.

### 인게임

---

전통적으로 Java Edition과 Bedrock Edition의 인게임 콘텐츠는 상당히 많은 차이를 보였다. NEO Edition은 이 둘을 통합하는 취지로 구상된 만큼, 그 배경과 환경에 따라 최선의 선택으로 로직과 콘텐츠를 통일하였다.

- **충돌 로직 / 콘텐츠 채택**
  - **Bedrock Edition 채택**
    - 가마솥에 물약을 넣을 수 있다. 단, 모든 유형의 물약이 허용되는 Bedrock Edition과는 달리 투척용, 잔류형을 제외한 일반 물약만 가마솥에 넣을 수 있다.
    - 가마솥에 채운 물약에 화살을 우클릭하여 화살에 상태 효과를 적용시킬 수 있다. 단, 이렇게 제작 할 시 지속 시간이 3분의 1로 줄어들며, 가마솥의 물 1칸을 소모한다.
    - 마녀의 집에 위치한 가마솥에 물약이 담겨있다. 담겨있는 물약은 마녀가 던지는 종류 (나약함, 독, 구속, 즉시 피해, 치유, 화염 저항, 신속, 수중 호흡) 중 하나이다.
    - 가마솥에 염료를 풀 수 있다. 단, 기존 물의 색상은 Java Edition과 동일하며, 파란색 염료를 풀 시 미세한 색상의 변화가 생긴다. 염료를 푸는 순서와 조합의 경우의 수도 물의 색상에 영향을 준다.
    - 아이템 액자 속 아이템을 회전할 때 팔을 휘두른다.
    - 갑옷 거치대에 팔이 있으며, 손에 아이템을 들게 할 수 있다. 웅크린 후 우클릭하여 왼손에도 아이템을 쥐어줄 수 있다. 단, 이로 인해 자세 바꾸기 키로 갑옷 거치대의 자세를 바꾸는 기능은 제거되며, 특정 단계의 레드스톤 신호 및 NBT로만 이를 수정할 수 있다.
    - 갑옷 거치대의 목 선과 어깨 선이 수평을 이룬다.
    - 3인칭, 혹은 다른 플레이어의 시점으로 봤을 때 음식 섭취, 낚시 등의 모션이 존재한다.
    - 크리에이티브 모드 및 평화로움 난이도일 때도 모든 음식을 섭취할 수 있다.
    - 켈프가 흔들리는 속도는 Bedrock Edition과 동일하다. 단, 이는 Tick Rate 설정에 영향을 받는다.
    - 크리에이티브 모드 한정 블록 파괴 / 설치 속도가 Bedrock Edition과 동일하게 빠르다. 비행 중 파괴 / 설치 키를 꾹 누르고 있어도 연달아 설치된다. 단, 서바이벌 모드에서는 Java Edition과 동일하게 설치 속도가 느려진다.
    - 눈이 내릴 시 랜덤 틱 속도에 따라 선택된 청크 내의 나뭇잎이 단계별로 변한다. 그 확률은 1%이며, 총 3단계가 존재, 단계가 높아질 수록 나뭇잎 텍스처의 비어있는 공간이 하얀색으로 채워진다. 눈이 그친다면 같은 로직으로 텍스처가 돌아오나, 그 확률이 선택될 시 5%로 눈이 내릴 시보다 빠르다.
    - 눈이 2단계 이상 채워진 나뭇잎, 혹은 눈이 쌓인 비고체 블록 (액체를 뜻하지 않으며, 인게인 판정 용어를 따름) 밑으로 눈 입자가 떨어진다. 반대로 물이 채워진 스펀지, 물이 채워진 계단 / 반블록 / 울타리 / 담장, 혹은 위에 물이 있는 고체 블록 밑으로는 떨어지는 물 입자 (입자명)이 떨어진다.
    - 눈이 무작위 방향으로 내리며, 블록에 닿았을 때만 사라진다.
    - 눈이 내릴 시 바닥에 다양한 높이로 쌓인다. 자연적으로 눈이 쌓이는 최대 높이는 위치 기반의 무작위 해시 함수로 결정된 난수 값으로 결정된다. 이 무작위 해시 함수는 블록이 설치될 시 무작위로 텍스처의 방향을 다르게 하는데 사용되는 함수이다.
    - 불이 붙는다면 플레이어 몸의 텍스처가 붉게 빛난다. 단, Bedrock Edition처럼 점멸하지는 않으며, 정적인 색상으로 빛난다.
    - 책을 펼칠 시 두 페이지 씩 펼쳐 보게 된다. 단, 이는 호환성 설정에서 변경할 수 있다.
    - 잔디, 균사체, 회백토 등의 일부 블록이 블록 위치에 따른 무작위 해시 함수에서 추출된 난수 값에 따라 텍스처의 밝기까지 변한다. 이는 자연스러운 잔디 표면을 만들기 위해서이다. 단, 바이옴에 의해 밝기 및 색상이 변한 블록은 추가로 밝기가 변한다.
  - **Java Edition 채택**
    - 잔류형 물약과 화살 8개의 조합은 유지된다. 단, 이 경우 화살이 떨어진 위치에 기존 잔류형 물약에 비례해서 4분의 1 넓이의 상태 효과 구름이 생성되며, 이 구름에 닿을 시 잔류형 물약의 상태 효과 지속 시간에서 절반이 줄어든 시간 동안 상태 효과가 적용된다.
    - 아이템 액자는 엔티티로 취급된다. 이로 인해 현수막, 블록 등과 아이템 액자를 겹쳐놓을 수 있으며, 블록 한 칸에 서로 다른 방향을 가진 복수의 아이템 액자를 설치할 수 있다. 단, 다른 엔티티로 취급되는 그림과도 겹쳐 설치할 수 있다.
    - 아이템 액자에 설치된 두께가 얇은 아이템은 가장자리에서 회전한다.
    - 레드스톤 신호의 판정은 대부분 Java Edition의 것을 따른다. 단, 레드스톤 신호가 통하고 있는 곳에 레드스톤 신호에 반응하는 블록을 설치할 시 1틱 동안 감지하는 시간을 가지게 된다.
    - 크리에이티브 모드에서 물약 / 물병을 마실 시 유리병이 생성되지 않는다.
    - 모든 아이템을 보조 무장 슬롯 (주로 왼손)에 들 수 있다.
    - 웅크리기가 아닌 아이템 사용 키 (주로 우클릭)을 통해 방패를 사용한다. 단, 방패 사용 시의 지연 시간이 3틱 (Java Edition은 5틱)이다.
    - 달리기 + 뒤로 키를 통해 뒤로 달리는 것이 불가능하다.
    - 크리에이티브 모드에서 비행 중 정지할 시 운동 관성이 존재한다. 단, 이는 호환성 설정에서 끌 수 있다.
    - 빈 지도와 빈 위치 정보 지도가 구분되지 않으며, 빈 지도 하나로 통합된다. 빈 지도를 통해 생성한 지도는 위치 정보가 표시된다.
    - 싱글플레이에서 게임 메뉴를 열 시 월드가 정지된다.
    - 쌓인 눈의 높이 판정이 시각적으로 보이는 높이보다 한 단계 낮은 판정으로 결정된다. 단, 1칸만 쌓인 눈에 갑옷 거치대 등을 설치해도 눈이 사라지지 않는다.
    - 색상 코드 (`§`)를 통한 텍스트 색상 지정은 지원되지 않으며, 표지판의 색상 지정은 염료로, 채팅창의 색상 문자열은 tellraw, title 명령어 등에 사용되는 JSON 문자열로만 가능하다.
    - 같은 종류의 버섯 블록끼리 연결할 시 접촉된 면의 텍스처가 하얗게 변한다. 이는 연결한 버섯 블록을 부수더라도 유지된다.
    - 문, 다락문 등을 열고 닫는 소리는 Java Edition의 것과 동일하다.
    - 문, 다락문 등이 열려있을 때 울타리 및 담장, 철창과 연결된다.
    - 지옥 천장 (Y 좌표 128 이상)에 블록을 설치할 수 있으며, 갈색 버섯이 생성된다.
    - 방패와 현수막의 조합을 통해 방패에 현수막 문양을 입힐 수 있다.
  - **NEO Edition 오리지널**
    - 비 / 눈 / 떨어지는 물 / 떨어지는 용암 입자가 가마솥에 닿을 시 5% 확률로 물이 한 칸 차게 된다. 기존 Bedrock Edition 및 Java Edition에서는 랜덤 틱에 영향을 받았으나, 이제 별도의 확률로 계산된다.
    - 공격 속도라는 개념은 존재하나, 공격 속도는 대미지가 아닌 공격 사거리에만 영향을 준다. 공격 속도에 따른 사거리 감소 비율은 대미지 감소 비율과 동일하다. 이렇게 결정한 이유는 전략 없는 연타를 막으면서도, 근접전 등 위급한 상황에서는 공격 속도의 제한 없이 오직 유저의 피지컬만으로 승부할 수 있도록 하기 위해서이다. 실제로 이는 Java Edition 전투 테스트 버전의 일부 로직에서 아이디어를 얻었다.

인터페이스 또한 Bedrock Edition과 Java Edition은 큰 차이를 보인다. Bedrock Edition의 Xbox 스타일 타일 메뉴, 그리고 Java Edition의 고전적인 마우스 지향 메뉴의 장점을 모두 취합하기 위해서, NEO Edition은 마치 웹 사이트처럼 모바일 / 콘솔, 태블릿, PC 환경을 디스플레이 크기에 따라 레이아웃을 유동적으로 변화시키는 적응형 레이아웃 시스템을 도입하였다. 전체적인 외형은 기존 Bedrock Edition의 좌측 세로 탭바 형식을 사용하되, 소히 일컫는 Xbox 스타일을 최소화하고 Minecraft 특유의 투박한 텍스처와 UI를 더한 형태이다. 설정 메뉴에서 클래식 레이아웃 (Java Edition)과 레거시 레이아웃 (Bedrock Edition)으로 레이아웃을 되돌릴  수 있다.

폰트의 경우 기존 GNU Unifont 기반을 사용하되, 최신 17.0.xx 버전을 사용한다. 글로벌 및 중국 본토판의 기본값은 순정 Unifont (간체자)이며, 일본에서는 JP 버전 (일본식 한자), 대만 및 홍콩, 한국 등 기타 한자권에서는 T 버전 (번체자)가 기본값으로 사용된다. 이는 설정 메뉴에서 한자 외형을 변경할 수 있다. 리소스팩 메뉴에서 불러오기 버튼을 누르거나, 파일을 드래그 앤 드롭함으로서 외부 ttf / otf 글꼴을 인게임에 적용 가능한 리소스팩으로 만들 수 있다.

인게임 명령어는 기존 Java Edition의 전체적인 형식과 구조를 따르되, Bedrock Edition의 전용 명령어 (`camerashake` 등)을 흡수하는 방향으로 적용된다. 서버 콘솔과 데이터팩 개발 환경에 한정되나, Minecraft: NEO Edition 용으로 새로 제작된 PowerShell 7 문법 구조의 MC PowerShell을 지원한다. .NET 기반으로 구동되나, 오직 인게임용으로 처음부터 다시 개발된 언어이기에 운영체제에 접근하는 것을 차단하였다. MC PowerShell의 문법 구조는 추후 부록에서 더 자세히 설명될 예정이다.

데이터팩과 리소스팩은 Bedrock Edition의 `.mcpack` 확장자를 선택하나, 내부 포맷은 완전히 다르기에 기존 Bedrock Edition 팩
은 추후 언급할 마이그레이션 툴을 거치지 않는다면 사용할 수 없다. 당연히 Java Edition의 포맷과도 다르기에 마찬가지로 마이그레이션 툴을 사용해야 한다.

### 데이터 저장 구조

---

Minecraft: Java Edition은 Anvil 저장 포맷을 채택하여 파편화된 파일들로 청크를 관리하였다. 허나 이는 청크 파일의 손상과 교체라는 외부 변수에 취약하였으며, 운영체제 단위에서 파일을 하나씩 읽는 방식이었기에 처리 속도 또한 떨어졌다. NEO Edition은 Bedrock Edition이 채택한 개별 차원별로 존재하는 LevelDB 데이터베이스 파일을 사용해 파일 손상과 외부 복제 / 교체 등 게임 외부적 개입을 방지한다.

렌더 거리 내부의 실제 청크를 로딩하는 데이터베이스 이외에도, 가상 렌더 거리 설정을 위한 LOD 기반 가성 청크인 `fake_chunks.db`로 시각적 렌더 거리를 크게 확장한다. 실 렌더링 거리 제한은 64청크, 시뮬레이션 거리 제한도 96청크까지 증가하나, LOD 가상 청크는 512청크까지 렌더링을 지원한다. 단, 명시적인 LOD 품질 설정과는 별개로 컴퓨터 사양을 자동으로 인식하여 계산한 임계 거리 이상부터는 강제적으로 단계별 품질 저하가 적용된다.

청크 단위 병렬 파이프라인을 도입하여 플레이어 주변의 핵심 영역은 여러 코어에 분산된 로직을 틱의 마지막에 합쳐 다음 틱으로 넘어가는 포크-조인 모델을 통해 메인 스레드와 동기화된 병렬 연산을 수행하여 논리적 일관성을 유지한다. 시뮬레이션 거리 내의 백그라운드 로직은 .NET의 `Task` 기반 비동기 스케줄러를 통해 메인 틱의 부하를 주지 않는 선에서 독립적으로 연산된다. 단, 모든 멀티 스레드 연산 중 쓰기 작업만큼은 반드시 메인 스레드의 통제하에 위치시킨다. 비동기 영역에서 발생한 변경 사항을 쓰기 대기 큐에 담겨 메인 틱의 특정 시점에 일괄 반영 시킴으로서 데이터 경합과 레이스 컨디션을 원천 차단한다.

엔티티와 아이템의 데이터 저장 방식은 컴포넌트 (구성 요소) 방식을 채택한다. 컴포넌트는 기존 NBT 방식이 사용하는 단일 참조 시에도 전체를 훑어보는 비효율적인 방식 대신, SQLite 데이터베이스와 JSON 칼럼을 통한 효율적인 스캔 방식을 사용한다. LevelDB를 사용하는 청크 저장과 달리 SQLite를 사용하는 이유는 SQL의 쿼리 능력이 필요하다 판단하였기 때문이다. UUID, 좌표, 타입 ID, 소유자 등의 핵심 필드는 SQL 컬링 방식으로 저장하며, 체력, 허기, 커스텀 이름, 마법 부여, 아이템, 인벤토리 슬롯 등의 상태 데이터는 JSON으로 직렬화하여 TEXT / BLOB 칼럼에 저장한다. 기존 파편화되있던 NBT, 아이템 구성 요소, 텍스트 구성요소, 월드 데이터가 모두 컴포넌트로 통합된다. 단, 블록은 개별 객체로 취급하지 않으며, `frilflo ECS` 라이브러리를 통한 데이터 중심 엔티티 컴포넌트 시스템을 도입하고, 해당 라이브러리의 SIMD를 적극적으로 활용하여 대량의 블록 데이터를 효율적으로 처리한다.

LevelDB와 SQLite 모두 갑작스러운 게임 종료 시 데이터 유실을 방지하기 위하여 WAL 모드를 활용해 데이터 무결성을 확보한다.

Scoreboard와 Storage가 각각 지역 변수 및 전역 변수라는 개념으로 대체된다.`$`를 사용하는 매크로 기능은 한층 강하되어 데이터팩이나 서버 관리 콘솔이 아닌 인게임 커맨드에서도 변수를 명령어 중간에 대입 및 참조할 수 있게 되었다. 변수 또한 컴포넌트 형식으로 관리되며, 컴포넌트가 존재하는 모든 객체에 변수를 할당할 수 있다. 전역 변수는 월드 데이터에 저장된다. 변수 타입으로는 Byte, Short, Int, Long, Float, Double, Char, String, List, Dictionary, Tuple, Object를 지원한다.

### 멀티플레이

---

Minecraft: Bedrock Edition의 Xbox 친구 추가 연동 기능을 지원하여 복잡한 포트포워딩이나 외부 서비스 없이 멀티플레이를 즐길 수 있도록 한다. Bedrock Edition은 내 월드에 친구를 추가하는 로컬 호스트 방식이나, 이는 호스트가 게임을 종료할 시 서버가 유지되지 못하는 치명적인 단점이 존재했다. 때문에 NEO Edition은 호스트의 컴퓨터 자원을 이용하는 것은 유지하되, 별도의 독립적으로 구동되는 서버 인스턴스를 위치시켜 호스트의 접속 여부에 상관없이 서버가 유지된다.

멀티플레이 동기화를 위한 네트워크 프로토콜은 QUIC를 사용하여 패킷 손실과 IP 변경 대응, 보안성을 확보한다. 그러나 기존 Bedrock Edition이 사용했던 RakNet 만의 장점을 흡수하기 위하여, 스트림 별로 `Reliable Ordered` (채팅, 아이템 이동), `Reliable Unordered` (청크 데이터), `Unreliable` (엔티티 움직임) 옵션을 동적으로 할당하며, Zstd 압축 알고리즘을 QUIC에 직접 통합해 기존 zlib 대비 CPU 점유율을 낮추고 압축률은 높이는 효과를 가져온다. 특히 지형 데이터의 전송 시 딕셔너리 압축을 통해 대역폭을 상당히 절감한다. 이외에도 Delta-Sync (증분 동기화)를 활용해 청크의 변경 사항만 압축해서 보내는 방식을 사용한다.

호스트의 서버 관리는 서버 구동 인스턴스의 GUI 창으로 가능하다. 해당 창에는 2D 월드 관전, 서버 규칙 변경, 서버 공지 등의 기능이 탑재되어 있다. 기존 Java Edition의 CLI 창이 익숙한 사용자들을 위해 CLI 콘솔을 띄우는 메뉴 또한 지원한다.

서버 권한 체계가 기존 OP / DEOP 이분화 체제에서 명령어 권한 체계와 합쳐진 Lv.0~Lv.4의 5단계로 체계화된다. 서버 관리 창에서 모든 권한의 행위별 상호작용 범위를 조절하거나, 새로운 권한을 생성하는 것도 가능하다. 아래에는 기본 권한들의 기본 설정만을 기재하였다.

- **Lv. 0 - Guest**: 한국어 명칭 참여자. 기본 명령어만을 사용할 수 있으며, 싱글 플레이의 치트 비허용 옵션 시 부여되는 권한과 본질적으로 같다.
- **Lv. 1 - User**: 한국어 명칭 사용자. 일반 명령어만을 사용할 수 있으며, 신규 플레이어에게 자동 부여되는 기본 권한이다.
- **Lv. 2 - Operator**: 한국어 명칭 운영자. 대부분의 명령어를 사용할 수 있으며, 신규 플레이어에게 자동 부여할 수 있는 기본 권한의 한계값이다. 커맨드 블록, 데이터 팩 함수의 권한 기본값이다.
- **Lv. 3 - Admin**: 한국어 명칭 관리자. 모든 클라이언트와 대부분의 서버 관리 명령어를 사용할 수 있으며, 호스트 플레이어에게 자동 부여되는 권한이다. 다른 플레이어에게 부여하려면 Lv. 4의 서버 콘솔을 사용해야 한다.
- **Lv. 4 - Owner**: 한국어 명칭 소유자. 인게임 플레이어가 가질 수 없으며, 서버 종료 등 모든 명령어를 사용할 수 있는 권한이다. 오직 서버 콘솔만이 가지고 있다.

PC와 콘솔, 모바일 간의 크로스 플랫폼은 완전하게 지원된다.

## 서비스

---

### 무료 마이그레이션

---

Minecraft: NEO Edition은 데이터 저장 방식이 대대적으로 개편된 만큼, Java Edition / Bedrock Edition의 맵 파일을 무료로 마이그레이션 해주는 공식적인 툴을 전 유저 대상 무료로 지원한다. 해당 툴은 웹사이트 형식으로 공개되며, 스팸 방지를 위해 Xbox 계정 로그인을 필수로 요구한다.

### 베타 테스터 혜택

---

Minecraft: NEO Edition의 개발 과정에 참여한 베타 테스터들에게는 다음과 같은 혜택이 적용된다.

- **베타 테스트 프로그램에 가입한 모든 유저**들에게는 특별 프로필 배지와 베타 테스터 칭호, 그리고 인게임 마인코인 300개가 지급된다.
- **위의 유저들 중에서 베타 버전에서 24시간 이상 플레이하였으며, 해당 Xbox 계정으로 양식에 맞춰진 중복되지 않으며 재현 가능한 버그 리포트, 혹은 새로운 건의 사항을 남긴 유저**들에게는 Microsoft Azure 클라우드 컴퓨팅 리소스로 서버를 구동하는 Realms의 일부 기능을 무료로 사용할 수 있는 라이선스 키가 Xbox 계정에 등록된 Email 주소로 발송되며, 추가적으로 인게임 마인코인 600개가 지급된다. 해당 라이선스 키로 구동되는 서버는 최대 수용 인원이 10명으로 제한되는 것 이외에는 그 어떠한 제한 사항도 존재하지 않으며, 마인코인을 300개에서 추가로 600개를 지급하는 것이기에 총 900개가 된다.
- **위의 유저들 중에서 버그 리포트 / 건의 사항을 포럼, 피드백 사이트 등에 제출하여 해당 사항이 수정 / 채택된 사례가 있는 유저**에게는 전용 망토가 지급되며, 엔딩 크레딧 명단에 기재되고, 추가적으로 마인코인 1600개가 지급된다.  망토는 3개 중에서 하나를 선택할 수 있으나, 추후 변경은 불가능하다.

### 콘텐츠 유통

---

Minecraft: NEO Edition의 모드, 애드온, 리소스팩, 데이터팩 등의 유저 콘텐츠를 유통할 수 있는 경로 중 공식적인 경로는 마켓플레이스가 존재한다. Bedrock Edition의 마켓플레이스 시스템을 가져왔으며, 실제 Mine Coin도 연동된다. 예외적으로 다음 EULA 조건만을 준수한다면 제3자 경로를 통한 외부 유통을 허용한다.

1. 유료 콘텐츠를 판매하여 금전적인 이득을 얻는 직접적인 수익 창출은 금지된다. 후원, 기부 등의 간접적인 수익 창출은 허용된다.
2. 모든 실행 로직 및 소스 코드는 접근성 높은 경로를 통해 공개되어야 하며, 승인된 오픈 소스 라이선스를 적용해야 한다. 텍스처, 모델, 음원, 영상, 브랜드 자산 등 비코드 창작물은 제작자가 별도 라이선스를 지정할 수 있다.
3. 공식 마켓플레이스 콘텐츠에 대한 불법 복제 및 지적 재산권 위반은 금지되며, 유통 관리자는 해당 콘텐츠에 대해 신고 접수 후 72시간 내 검토 및 임시 조치를 이루어야 한다.
4. 유통 플랫폼에 유저 콘텐츠를 업로드 시 개발자에게 Minecraft: NEO Edition EULA 조항에 대해 동의를 받는 과정이 필수적 절차로 포함되어야 한다.

## 부록

---

### 파일 구조

---

#### 실행 파일 구조

---

**Windows**

```
Program Files/
	XboxGames/
		MinecraftNeo/
			Minecraft.exe
			Minecraft.Server.exe
			assets/
				core.pak
				vanilla.pak
				lang.pak
			bin/
				client/
					Minecraft.Core.dll
					Microsoft.Minecraft.Game.dll
					Minecraft.Binding.dll
				server/
					Minecraft.Server.Management.GUI.exe
					Minecraft.Server.Management.CLI.exe
					Minecraft.Server.Core.dll
			config/
				Minecraft.RuntimeConfig.json
				Minecraft.GraphicConfig.json
				Minecraft.NetworkConfig.json
			engine/
				bgfx/
					bgfx.dll
					bgfx.dx12.dll
					bgfx.dx11.dll
					bgfx.vulkan.dll
				fmod/
					fmod.dll
					fmod_studio.dll
			internal_mods/
				(...)
			runtime/
				(...)
			ui/
				neo/
					(...)
				classic/
					(...)
				legacy/
					(...)
```

**macOS**

```
/Applications/
	Minecraft NEO Edition/
		Minecraft.app/
			Contents/
				MacOS/
					Minecraft
					Minecraft.Server
				Info.plist
				Resources/
					AppIcon.icns
		assets/
			core.pak
			vanilla.pak
			lang.pak
		bin/
			client/
				Minecraft.Core.dylib
				Microsoft.Minecraft.Game.dylib
				Minecraft.Binding.dylib
			server/
				Minecraft.Server.Management.GUI.app/
					(...)
				Minecraft.Server.Management.CLI
				Minecraft.Server.Core.dylib
		config/
			Minecraft.RuntimeConfig.json
			Minecraft.GraphicConfig.json
			Minecraft.NetworkConfig.json
		engine/
			bgfx/
				bgfx.dylib
				bgfx.metal.dylib
			fmod/
				fmod.dylib
				fmod_studio.dylib
		internal_mods/
			(...)
		runtime/
			(...)
		ui/
			neo/
				(...)
			classic/
				(...)
			legacy/
				(...)
```

**Linux**

```
/opt/
	minecraft-neo/
		minecraft
		minecraft.server
		assets/
			core.pak
			vanilla.pak
			lang.pak
		bin/
			client/
				Minecraft.Core.so
				Microsoft.Minecraft.Game.so
				Minecraft.Binding.so
			server/
				minecraft-server-gui
				minecraft-server-cli
				Minecraft.Server.Core.so
		config/
			Minecraft.RuntimeConfig.json
			Minecraft.GraphicConfig.json
			Minecraft.NetworkConfig.json
		engine/
			bgfx/
				bgfx.so
				bgfx.vulkan.so
				bgfx.opengl.so
			fmod/
				fmod.so
				fmod_studio.so
		internal_mods/
			(...)
		runtime/
			(...)
		ui/
			neo/
				(...)
			classic/
				(...)
			legacy/
				(...)
```

#### 데이터 저장 구조

---

**Windows**

```
%AppData%/
	.minecraft-neo
		launcher/
			accounts/
				accounts.json5
				{AccountName}/
					config/
						settings.json5
					auth_cache.bin
			cache/
				web_cache/
					(...)
				skins/
					(...)
				downloads/
					(...)
			logs/
				session_{YYYYMMDD}_{HHMMSS}.jsonl
			metadata/
				versions.json5
				index.db
		client/
			common/
				mods/
					(...)
				datapacks/
					(...)
				resourcepacks/
					(...)
				shaderpacks/
					(...)
				user_data/
					option.json5
			shared_saves/
				{SharedWorldName}/
					(...)
			instances/
				profiles.json5
				{ProfileName}/
					cache/
						(...)
					crash_reports/
						(...)
					default_config/
						(...)
					downloads/
						(...)
					logs/
						(...)
					mods/
						{ModName}/
							{ModName}.dll
							metadata.json5
							icon.png
							assets/
								fonts/
									(...)
								materials/
									(...)
								models/
									(...)
								textures/
									(...)
								shaders/
									(...)
								sounds/
									(...)
							script/
								{ModName}.*.ts
							data/
								{ModName}.config.json5
					datapacks/
						{DatapackName}
							metadata.json5
							icon.png
							data/
								{Namespace}/
									game_data/
										advancement/
											(...)
										chat_type/
											(...)
										damage_type/
											(...)
										dimension/
											(...)
										dimension_type/
											(...)
										dialog/
											(...)
										enchantment/
											(...)
										enchantment_provider/
											(...)
										function/
											{FunctionName}.mcps1
										instrument/
											(...)
										loot_table/
											(...)
										predicate/
											(...)
										recipe/
											(...)
										structure/
											(...)
										tags/
											(...)
										test_environment/
											(...)
										test_instance/
											(...)
										timeline/
											(...)
										trial_spawner/
											(...)
										trim_material/
											(...)
										trim_pattern/
											(...)
										worldgen/
											biome/
												(...)
											configured_carver/
												(...)
											configured_feature/
												(...)
											density_function/
												(...)
											noise/
												(...)
											noise_setting/
												(...)
											placed_feature/
												(...)
											processor_list/
												(...)
											structure/
												(...)
											structure_set/
												(...)
											template_pool/
												(...)
											world_preset/
												(...)
									item_data/
										banner_pattern/
											(...)
										item_modifier/
											(...)
										jukebox_song/
											(...)
									entity_data/
										cat_variant/
											(...)
										chicken_variant/
											(...)
										cow_variant/
											(...)
										frog_variant/
											(...)
										painting_variant/
											(...)
										pig_variant/
											(...)
										wolf_variant/
											(...)
							config/
								{DatapackName}.config.json5
					resourcepacks/
						{ResourcepackName}/
							metadata.json5
							icon.png
							assets/
								minecraft/
									fonts/
										(...)
									materials/
										(...)
									models/
										(...)
									textures/
										(...)
									sounds/
										(...)
					downloads/
						(...)
					shaderpacks/
						{ShaderpackName}/
							metadata.json5
							icon.png
							shaders/
								shaders.json5
								entity.json5
								block.json5
								item.json5
								dimension.json5
								nether/
									(...)
								ender/
									(...)
								overworld/
									(...)
								lang/
									(...)
								lib/
									(...)
								program/
									(...)
					screenshots/
					saves/
						{WorldName}/
							icon.png
							level/
								(...)
							level_old/
								(...)
							session.lock
							advancements/
								{UUID}.json5
							data/
								globals/
									random_sequences.db
									global_variable.db
									local_variable.db
								ender/
									chunks/
										(...)
									fake_chunks/
										(...)
									world_data.db
								overworld/
									chunks/
										(...)
									fake_chunks/
										(...)
									world_data.db
								nether/
									chunks/
										(...)
									fake_chunks/
										(...)
									world_data.db
							datapacks/
								importer.json5
							entities/
								registry.db
								players.db
								mobs.db
								vehicles.db
								projectiles.db
							playerdata/
								{UUID}.db
								{UUID}.db_old
							poi/
								registry.db
								poi.db
							region/
								registry.db
								ender.db
								overworld.db
								nether.db
							stats/
								{UUID}.json5
					servers/
						{ServerName}/
							icon.png
							config/
								server.toml
								permissions.json5
								whitelist.json5
								banned-ips.json
								banned-players.json
								permission-interaction-range.json
							logs/
								server_{YYMMDD}_{HHMMSS}.jsonl
							temps/
								(...)
							mods/
								(...)
							datapacks/
								(...)
							resourcepacks/
								(...)
							shaderpacks/
								(...)
							saves/
								level/
									(...)
								level_old/
									(...)
								advancements/
									{UUID}.json5
								data/
									globals/
										random_sequences.db
										global_variable.db
										local_variable.db
									ender/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									overworld/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									nether/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
								entities/
									registry.db
									players.db
									mobs.db
									vehicles.db
									projectiles.db
								playerdata/
									{UUID}.db
									{UUID}.db_old
								poi/
									registry.db
									poi.db
								region/
									registry.db
									ender.db
									overworld.db
									nether.db
								stats/
									{UUID}.json5
					temps/
					user_data/
						command_history.jsonl
						debug_profile.json5
						hotbar.json5
						option.json5
```

**macOS**

```
~/Library/
	Application Support/
		minecraft-neo/
			launcher/
				accounts/
					accounts.json5
					{AccountName}/
						config/
							settings.json5
						auth_cache.bin
				cache/
					web_cache/
						(...)
					skins/
						(...)
					downloads/
						(...)
				logs/
					session_{YYYYMMDD}_{HHMMSS}.jsonl
				metadata/
					versions.json5
					index.db
			client/
				common/
					mods/
						(...)
					datapacks/
						(...)
					resourcepacks/
						(...)
					shaderpacks/
						(...)
					user_data/
						option.json5
				shared_saves/
					{SharedWorldName}/
						(...)
				instances/
					profiles.json5
					{ProfileName}/
						cache/
							(...)
						crash_reports/
							(...)
						default_config/
							(...)
						downloads/
							(...)
						logs/
							(...)
						mods/
							{ModName}/
								{ModName}.dll
								metadata.json5
								icon.png
								assets/
									fonts/
										(...)
									materials/
										(...)
									models/
										(...)
									textures/
										(...)
									shaders/
										(...)
									sounds/
										(...)
								script/
									{ModName}.*.ts
								data/
									{ModName}.config.json5
						datapacks/
							{DatapackName}
								metadata.json5
								icon.png
								data/
									{Namespace}/
										game_data/
											advancement/
												(...)
											chat_type/
												(...)
											damage_type/
												(...)
											dimension/
												(...)
											dimension_type/
												(...)
											dialog/
												(...)
											enchantment/
												(...)
											enchantment_provider/
												(...)
											function/
												{FunctionName}.mcps1
											instrument/
												(...)
											loot_table/
												(...)
											predicate/
												(...)
											recipe/
												(...)
											structure/
												(...)
											tags/
												(...)
											test_environment/
												(...)
											test_instance/
												(...)
											timeline/
												(...)
											trial_spawner/
												(...)
											trim_material/
												(...)
											trim_pattern/
												(...)
											worldgen/
												biome/
													(...)
												configured_carver/
													(...)
												configured_feature/
													(...)
												density_function/
													(...)
												noise/
													(...)
												noise_setting/
													(...)
												placed_feature/
													(...)
												processor_list/
													(...)
												structure/
													(...)
												structure_set/
													(...)
												template_pool/
													(...)
												world_preset/
													(...)
										item_data/
											banner_pattern/
												(...)
											item_modifier/
												(...)
											jukebox_song/
												(...)
										entity_data/
											cat_variant/
												(...)
											chicken_variant/
												(...)
											cow_variant/
												(...)
											frog_variant/
												(...)
											painting_variant/
												(...)
											pig_variant/
												(...)
											wolf_variant/
												(...)
								config/
									{DatapackName}.config.json5
						resourcepacks/
							{ResourcepackName}/
								metadata.json5
								icon.png
								assets/
									minecraft/
										fonts/
											(...)
										materials/
											(...)
										models/
											(...)
										textures/
											(...)
										sounds/
											(...)
						downloads/
							(...)
						shaderpacks/
							{ShaderpackName}/
								metadata.json5
								icon.png
								shaders/
									shaders.json5
									entity.json5
									block.json5
									item.json5
									dimension.json5
									nether/
										(...)
									ender/
										(...)
									overworld/
										(...)
									lang/
										(...)
									lib/
										(...)
									program/
										(...)
						screenshots/
						saves/
							{WorldName}/
								icon.png
								level/
									(...)
								level_old/
									(...)
								session.lock
								advancements/
									{UUID}.json5
								data/
									globals/
										random_sequences.db
										global_variable.db
										local_variable.db
									ender/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									overworld/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									nether/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
								datapacks/
									importer.json5
								entities/
									registry.db
									players.db
									mobs.db
									vehicles.db
									projectiles.db
								playerdata/
									{UUID}.db
									{UUID}.db_old
								poi/
									registry.db
									poi.db
								region/
									registry.db
									ender.db
									overworld.db
									nether.db
								stats/
									{UUID}.json5
						servers/
							{ServerName}/
								icon.png
								config/
									server.toml
									permissions.json5
									whitelist.json5
									banned-ips.json
									banned-players.json
									permission-interaction-range.json
								logs/
									server_{YYMMDD}_{HHMMSS}.jsonl
								temps/
									(...)
								mods/
									(...)
								datapacks/
									(...)
								resourcepacks/
									(...)
								shaderpacks/
									(...)
								saves/
									level/
										(...)
									level_old/
										(...)
									advancements/
										{UUID}.json5
									data/
										globals/
											random_sequences.db
											global_variable.db
											local_variable.db
										ender/
											chunks/
												(...)
											fake_chunks/
												(...)/
											world_data.db
										overworld/
											chunks/
												(...)
											fake_chunks/
												(...)
											world_data.db
										nether/
											chunks/
												(...)
											fake_chunks/
												(...)
											world_data.db
									entities/
										registry.db
										players.db
										mobs.db
										vehicles.db
										projectiles.db
									playerdata/
										{UUID}.db
										{UUID}.db_old
									poi/
										registry.db
										poi.db
									region/
										registry.db
										ender.db
										overworld.db
										nether.db
									stats/
										{UUID}.json5
						temps/
						user_data/
							command_history.jsonl
							debug_profile.json5
							hotbar.json5
							option.json5

```

**Linux**

```
~/.config/
	minecraft-neo/
		launcher/
			accounts/
				accounts.json5
				{AccountName}/
					config/
						settings.json5
					auth_cache.bin
			metadata/
				versions.json5
				index.db
		client/
			common/
				user_data/
					option.json5
			instances/
				profiles.json5
				{ProfileName}/
					default_config/
						(...)
					user_data/
						command_history.jsonl
						debug_profile.json5
						hotbar.json5
						option.json5

~/.local/
	share/
		minecraft-neo/
			launcher/
				logs/
					session_{YYYYMMDD}_{HHMMSS}.jsonl
			client/
				common/
					mods/
						(...)
					datapacks/
						(...)
					resourcepacks/
						(...)
					shaderpacks/
						(...)
					shared_saves/
						{SharedWorldName}/
							(...)
				instances/
					{ProfileName}/
						mods/
							{ModName}/
								{ModName}.dll
								metadata.json5
								icon.png
								assets/
									fonts/
										(...)
									materials/
										(...)
									models/
										(...)
									textures/
										(...)
									shaders/
										(...)
									sounds/
										(...)
								script/
									{ModName}.*.ts
								data/
									{ModName}.config.json5
						datapacks/
							{DatapackName}/
								metadata.json5
								icon.png
								data/
									{Namespace}/
										game_data/
											advancement/
												(...)
											chat_type/
												(...)
											damage_type/
												(...)
											dimension/
												(...)
											dimension_type/
												(...)
											dialog/
												(...)
											enchantment/
												(...)
											enchantment_provider/
												(...)
											function/
												{FunctionName}.mcps1
											instrument/
												(...)
											loot_table/
												(...)
											predicate/
												(...)
											recipe/
												(...)
											structure/
												(...)
											tags/
												(...)
											test_environment/
												(...)
											test_instance/
												(...)
											timeline/
												(...)
											trial_spawner/
												(...)
											trim_material/
												(...)
											trim_pattern/
												(...)
											worldgen/
												biome/
													(...)
												configured_carver/
													(...)
												configured_feature/
													(...)
												density_function/
													(...)
												noise/
													(...)
												noise_setting/
													(...)
												placed_feature/
													(...)
												processor_list/
													(...)
												structure/
													(...)
												structure_set/
													(...)
												template_pool/
													(...)
												world_preset/
													(...)
										item_data/
											banner_pattern/
												(...)
											item_modifier/
												(...)
											jukebox_song/
												(...)
										entity_data/
											cat_variant/
												(...)
											chicken_variant/
												(...)
											cow_variant/
												(...)
											frog_variant/
												(...)
											painting_variant/
												(...)
											pig_variant/
												(...)
											wolf_variant/
												(...)
								config/
									{DatapackName}.config.json5
						resourcepacks/
							{ResourcepackName}/
								metadata.json5
								icon.png
								assets/
									minecraft/
										fonts/
											(...)
										materials/
											(...)
										models/
											(...)
										textures/
											(...)
										sounds/
											(...)
						shaderpacks/
							{ShaderpackName}/
								metadata.json5
								icon.png
								shaders/
									shaders.json5
									entity.json5
									block.json5
									item.json5
									dimension.json5
									nether/
										(...)
									ender/
										(...)
									overworld/
										(...)
									lang/
										(...)
									lib/
										(...)
									program/
										(...)
						screenshots/
						saves/
							{WorldName}/
								icon.png
								level/
									(...)
								level_old/
									(...)
								session.lock
								advancements/
									{UUID}.json5
								data/
									globals/
										random_sequences.db
										global_variable.db
										local_variable.db
									ender/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									overworld/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
									nether/
										chunks/
											(...)
										fake_chunks/
											(...)
										world_data.db
								datapacks/
									importer.json5
								entities/
									registry.db
									players.db
									mobs.db
									vehicles.db
									projectiles.db
								playerdata/
									{UUID}.db
									{UUID}.db_old
								poi/
									registry.db
									poi.db
								region/
									registry.db
									ender.db
									overworld.db
									nether.db
								stats/
									{UUID}.json5
						servers/
							{ServerName}/
								icon.png
								config/
									server.toml
									permissions.json5
									whitelist.json5
									banned-ips.json
									banned-players.json
									permission-interaction-range.json
								logs/
									server_{YYMMDD}_{HHMMSS}.jsonl
								temps/
									(...)
								mods/
									(...)
								datapacks/
									(...)
								resourcepacks/
									(...)
								shaderpacks/
									(...)
								saves/
									level/
										(...)
									level_old/
										(...)
									advancements/
										{UUID}.json5
									data/
										globals/
											random_sequences.db
											global_variable.db
											local_variable.db
										ender/
											chunks/
												(...)
											fake_chunks/
												(...)
											world_data.db
										overworld/
											chunks/
												(...)
											fake_chunks/
												(...)
											world_data.db
										nether/
											chunks/
												(...)
											fake_chunks/
												(...)
											world_data.db
									entities/
										registry.db
										players.db
										mobs.db
										vehicles.db
										projectiles.db
									playerdata/
										{UUID}.db
										{UUID}.db_old
									poi/
										registry.db
										poi.db
									region/
										registry.db
										ender.db
										overworld.db
										nether.db
									stats/
										{UUID}.json5
						logs/
							(...)
						crash_reports/
							(...)
						downloads/
							(...)

~/.cache/
	minecraft-neo/
		launcher/
			web_cache/
				(...)
			skins/
				(...)
			downloads/
				(...)
		client/
			instances/
				{ProfileName}/
					cache/
						(...)
					downloads/
						(...)
					temps/
						(...)
```

### MC PowerShell 문법

---

#### 동사

---

```
# 객체 생성
New-
Remove-

# 상태 정의
Get-
Set-
Enable-
Disable-
Start-
Stop-
Show-
Hide-

# 동작
Reload-
Move-
Clone-
Mount-
Unmount-
Give-
Save-
Lock-
Unlock-

# 처리
Select-
Where-
Sort-
Find-
Write-
```

#### 명사

---

```
# 엔티티
Entity
Mob
Player
Self
Attribute

# 환경
Block
Chunk
Region
Biome
Structure
Poi
Dimension
Time
Weather
Position
Angle
Distance

# 아이템
Component
Enchantment
Inventory

# 인터페이스
Title
SubTitle
ActoinBar
BossBar
Dialog

# 게임 규칙
Advancement
Difficulty
GameMode
GameRule
Recipe
ForceLoad
SpawnPoint
WayPoint

# 비주얼 / 사운드
Motion
CameraEffect
CameraFilter
CameraShake
CameraZoom
Effect
Fog
Particle
Sound

# 데이터
BlockState
Event
Object
Tag
Team
Variable
Experience

# 로직
Random
Seed
Datapack
StopWatch
Trigger

# 서버
AllowList
AutoBackup
AutoSave
BackupCopy
BlockList
DefaultGameMode
DefaultWorldSpawn
IdleTimeOut
Log
Capacity
ClientConnection
ServerData
Permission
PlayerList
Runtime
Properties
```

#### 예약어

---

```
# 반복문
For
ForEach
Break
Continue

# 조건문
If
ElseIf
Else

# 함수
Function
Parameter
Return

# 에러 처리
Try
Catch
```

#### 예시

---

```
# 가장 가까운 좀비 10마리를 스티브에게로 TP
Get-Mob | 
	Where-Object -Property Type -eq "Zombie" | 
	Sort-Object { Get-Distance -To "Steve" } | 
	Select-Object -First 10 | 
	Move-Entity -Destination "Steve"
```
