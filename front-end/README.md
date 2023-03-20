#### 프론트 엔드 (Front-end) 설명

- 인터페이스, 사용자가 볼 수 있는 화면
  - 웹사이트에서 나타나는 텍스트나 이미지 그리고 버튼을 클릭하는 것 등 사용자가 마주하는 앞단의 것들.
  - 인터페이스 (슬라이더, 드롭다운 메뉴, 레이아웃, 폰트 등) 개발하는 것

#### 홈페이지가 사용자에게 보이는 순서 (브라우저 렌더링 과정) 설명

- **[키워드-흐름]**
  - HTML
  - DOM
  - CSSOM
  - Render Tree
  - Rendering
- **[간략흐름]**
  - [불러오기-단계] 주소 입력 후 서버로부터 HTML 파일 입수
  - [파싱-단계] HTML 문서 파싱하여 DOM 객체 생성
  - [파싱-단계] CSS 파싱하여 CSSOM 객체 생성
  - [렌더링-트리-생성-단계] DOM과 CSSOM 을 렌더 트리로 결합 (렌더링 목적)
  - [렌더링-단계] 렌더링 트리를 탐색하면서 렌더링 시작
- **[상세내용]**
  - [불러오기-단계] 주소창에 입력된 주소로 서버 찾기
  - [불러오기-단계] DNS가 도메인 name 부분을 DNS 서버에서 해당하는 IP 검색
  - [불러오기-단계] 서버에서 HTML 파일을 클라이언트로 송신
  - [파싱-단계] 웹 엔진의 파서가 HTML 문서는 파싱되어 DOM 객체를 생성.
  - [파싱-단계][css] 중간에 CSS 파일을 로드하는 link 태그 또는 style 태그를 만나면 DOM 생성 중지
  - [파싱-단계][css] CSS를 파싱하고 CSSOM을 생성
  - [렌더링-트리-생성-단계] 만들어진 DOM, CSSOM은 렌더링을 위해 렌더 트리로 결합
    - [참고내용] 렌더링: 브라우저에 시각적으로 출력하는 것
  - 만약 script 태그를 만나면 CSS와 동일하게 JS 코드를 실행하기 위해 파싱을 중단
  - JS 엔진 실행하고 JS 코드 파싱
  - [렌더링-단계] 렌더링 트리를 탐색하면서 렌더링 시작
  - 참고
    - [참고내용] 자바스크립트가 DOM, CSSOM 을 변경하는 경우 리렌더링을 하게 됨.
      - 리플로우: 레이아웃 재 계산
      - 리페인트: 재결합된 렌더 트리를 기반으로 다시 페인트
    - [참고내용] script 태그를 만날 때마다 파싱이 중단되는 문제를 async 나 defer를 붙여줌으로써 해결 가능
      - [async]: HTML 파싱, JS 파일 로드가 동시에 진행
      - [defer]:
        - DOM 생성이 완료된 직후, JS의 파싱과 실행이 진행
        - JS 파일을 HTML 문서 분석 이후에 실행하도록 지시하는 HTML 속성 (Attribute)
        - 자바스크립트 안에서 HTML 요소에 접근하는 코드가 있는 경우 사용

#### DNS 설명

- Domain Name System.
- **사람이 읽을 수 있는 도메인 이름을 머신이 읽을 수 있는 IP 주소로 변환해주는 시스템**
- 상세 설명
  - 인터넷 연결되면 IP를 항당해주는 통신사에 해당하는 각 통신사의 DNS 서버가 등록됨. (Ex. KT DND or SK DNS)
    - 기지국 DNS 서버 (Local DNS Server)
  - 주소창에 도매인 주소를 입력 시 통신사 DNS는 해당 도메인을 검색 시도
  - 기지국 서버에 없으면 Root DNS 서버로 검색 요청
    - 모든 DNS 서버들은 Root DNS Server 주소를 기본적으로 가지고 있음.
  - Root DNS 에도 해당 IP가 없다면 TLD (Top Level Domain) 주소를 넘겨줌.
    - Ex. www.xxx.co.kr: kr.
  - Recursive Query

#### 변수 생성 단계 설명

- **선언** 단계 (Declaration Phase): 변수 객체를 실행 컨텍스트에 등록
- **초기화** 단계 (Initialization Phase): 등록된 변수의 메모리를 확보.
- **할당** 단계 (Assignment Phase): 초기화된 변수에 실제 값을 할당

#### 호이스팅에 대한 설명

- 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것.
- 코드 실행 전 변수/함수 선언이 해당 스코프의 최상단으로 끌어 올려진 것 같은 현상.
- 변수, 함수의 선언부가 위치한 인접 스코프의 시작 시점에서 해당 식별자의 관측이 가능한 현상.
- 코드 실행 전 이미 변수/함수 선언이 저장되어 있기 때문에 선언문보다 참조/호출이 먼저 나와도 오류 없이 동작함.

#### 렉시컬 스코프 (Lexical scoping) 설명

- 함수를 어디서 호출하는지가 아닌 어디에 선언하였는지에 따라 결정되는 것
- 함수의 선언에 따라 상위 스코프를 결정
- 정적 스코프 (Static scope)

#### 스코프 체인 (Scope chain) 설명

- 일종의 리스트.
- 전역 객체와 중첩된 함수의 스코프 레퍼런스를 차례로 저장하고 각각의 스코프가 어떻게 연결(Chain) 되고 있는지 보여주는 것
- 자기 자신의 스코프를 제외하고 자신과 가장 가까운 변수 객체의 모든 스코프들
- 개발자 도구 내 console.dir() 사용 (Ex. [[Scopes]])

#### 실행 컨텍스트 (Execution Context) 설명

- 작성한 코드가 실행되는 환경.
- 자바스크립트의 핵심원리
- LIFO(Last In, First Out) 구조 스택
- 실행되면 엔진이 스코프 체인을 통해 렉시컬 스코프를 먼저 파악 시도.
- 2가지의 실행 컨텍스트 존재
  - 글로벌 실행 컨텍스트 (Global Execution Context)
    - 코드 실행되기 전에 생성
    - 하나의 전역 실행 컨텍스트 만이 존재 (앱 종료될 때까지 유지)
  - 함수 실행 컨텍스트 (Functional Execution Context)
    - 전역 실행 컨텍스트가 생성된 이후 함수가 실행(호출)될 때마다 새로운 실행 컨텍스트가 작성됨.

#### 클로저란, 원리와 사용 이유, 사용법

- 반환된 내부함수가 자신이 선언됐을 때의 환경(렉시컬 환경)인 스코프를 기억하여 자신이 선언됐을 때의 환경 (스코프) 밖에서 호출되어도 그 환경(스코프)에 접근할 수 있는 함수.
- 자신이 생성될 때의 환경(렉시컬 환경)을 기억하는 함수
- 함수 안의 함수
- 클로저 모듈 패턴 활용한 캡슐화 구현 가능
- 데이터 보존 가능
  - 외부 함수의 실행이 끝나더라도 외부 함수 내 변수 사용 가능
- 모듈화에 유리
  - 데이터와 메소드를 묶어다닐 수 있으므로

#### 함수가 할당된 객체 데이터의 속성 (Property)을 무엇이라 부르는가?

- Ex. const funcConst = { getUserName: function () {} }
  - funcConst 내 getUserName 속성은 함수가 할당되었으므로 **메소드** 라 부름

#### 비동기 처리 방식의 차이점 (Promise vs Async + Await)

- [에러-핸들링-측면]
  - Promise: .catch() 문을 통해 에러 핸들링 가능
  - Async + Await: 별도로 try-catch() 문 사용 필요
- [코드-가독성-측면]
  - Promise: .then() 지옥 가능성
  - 코드가 길어지면 길어질수록 Async + Await 활용한 코드가 가독성 높음
  - Async + Await 는 비동기이지만 마치 동기 코드처럼 읽히게 해주므로 코드 흐름 이해에 용이함.

#### 자바스크립트가 동적 언어인 이유에 대한 설명

- 컴파일 시가 아닌 런타임 시 변수의 타입이 결정
  - 고정된 타입이 없어서 같은 변수에 여러 타입의 값을 자유롭게 할당 가능
  - 컴파일 시 타입 명시 작업이 필요없으므로 개발 속도 향상
- 자바스크립트는 컴파일되지만 문맥상 인터프리터 언어로 분류됨
- 모던 자바스크립트 컴파일러는 거의 런타임 내에서 빠르게 컴파일 수행

#### 자바스크립트 형변환 설명

- 암시적 변환: 자바스크립트 엔진이 필요에 따라 자동으로 데이터 타입을 변환
  - 산술연산자
    - 더하기 연산자: 숫자보다 문자열이 우선시
      - "10" + false => "100"
        - false = 0
      - 99 + true => 100
        - true = 1
    - 타 연산자(-, \*, /, %): 문자형보다 숫자형이 우선시
      - "2" \* false => 0
      - 2 \* true => 2
  - 동치 비교
    - == vs ===
- 명시적 변환: 개발자가 의도적으로 데이터 타입을 변환
  - => Number Type
    - Number()
    - parseInt()
    - parseFloat()
  - => String Type
    - String()
    - toString()
    - toFixed()
  - => Boolean Type
    - Boolean()

#### GET, POST 개념

- [GET]: 가져온다는 개념
  - 서버로부터 어떤 데이터를 가져와서 보여줄 때 사용
  - 값, 내용, 상태 등을 바꾸지 않는 경우에 사용
  - 서버의 어떠한 리소스로부터 정보를 요청하기 위해 사용되는 메소드
  - 멱등성 O
  - Ex. 게시판 글 목록 보기
- [POST]: 수행한다는 개념
  - 서버 상의 데이터 값이나 상태를 바꾸기 위해 사용
  - 리소스를 생성 / 업데이트하기 위해 서버에 데이터를 보내는 데에 사용
  - 멱등성 X
  - Ex. 게시판 글 수정 / 저장

#### 멱등성 뜻

- 기본 뜻
  - 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질
- 웹 용어의 관점
  - 동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 서버의 상태도 동일하게 유지될 때 해당 HTTP 메서드가 멱등성을 가진다라 볼 수 있음

#### 자바스크립트 함수 호출시 전달되는 값들 종류

- 함수 내 명시된 인자값
- arguments 객체
- this

#### 자바스크립트의 this에 대한 설명

- 자바스크립트는 this에 바인딩할 객체가 동적으로 바인딩
  - 함수가 호출될 때 함수가 어떻게 호출되었는지에 따라 객체 동적 바인딩
  - 함수호출, 메소드 호출, 생성자 함수 호출, apply/call/bind 호출

#### 크로스 브라우징 설명

- 웹 표준에 따라 개발을 하여 서로 다른 OS 또는 플랫폼에 대응하는 것을 의미
  - 브라우저의 렌더링 엔진이 다른 경우에 인터넷이 이상없이 구현되도록 하는 기술
  - 어느 한 플랫폼 또는 OS 쪽에 최적화되어 치우치지 않도록 공통요소를 사용하여 웹 페이지를 제작하는 방법
- 목적
  - 웹 사이트를 서로 비슷하게 만들어서 어떤 환경에서도 이상없이 작동되게 하기 위함.

#### 크로스 브라우징 이슈 대처 방법

- 적용 기능의 지원 브라우저 파악
  - 핵심적인 내용은 동일하게 유지, 조금 다르게 보여주더라도 추후를 위해 최신 기술 사용 지향
- 모든 환경에서 지원해야 한다면 라이브러리를 사용
  - 라이브러리 사용에 있어서 의존성이 비대해지면 라이브러리 자체를 관리하는 Cost가 발생할 가능성도 있음.
  - 각 브라우저마다 코드를 각각 따로 작성하는 일보다는 공수가 덜 들것으로 판단
- 브라우저 종류에 대한 분기가 아닌 Feature 에 대한 분기 처리 지향 (Feature Detection)
  - Worst Ex. if (isIE) { xxx() }
  - Best Ex. if (element.addEventListener) { xxx() }
- 각종 툴 사용
  - reset.css (normalize.css)
    - 브라우저의 고유 기본값 초기화
    - Ex. reset.css cdn 으로 검색하여 link 태그를 index.html 헤더 부분에 설정
  - Prefix 작성
    - 모든 브라우저에서 지원하는 호환 프로퍼티를 먼저 정의하고 CSS3에서 지원하는 프로퍼티를 나중에 정의하는 방법을 사용해야 함.
    - 접두어가 없는 속성은 가장 나중에 추가 필요.
      - Ex. -webkit-border-radius: 15px; border-radius: 10px;

#### HTTP, HTTPS 포트 번호

- HTTP: 80
- HTTPS: 443

#### SOP 설명

- Same-Origin Policy
- 같은 출처에서만 리소스를 공유할 수 있다 라는 규칙을 가진 정책
- 출처가 다르더라도 CORS 정책을 지킨 리소스 요청은 허용

#### CORS (Cross-Origin Resource Sharing) 정책 설명

- 다른 출처간의 리소스 공유
- 브라우저 구현 스펙에 포함되는 정책
  - 브라우저 없이 서버 간 통신 시에는 이 정책이 적용되지 않음
- 참고. URL 내 3가지 요소만 같으면 같은 출처라고 판단
  - Scheme
  - Host
  - Port
- 클라이언트 측에서 다른 출처 리소스 요청 시
  - 브라우저는 요청 헤더 내 Origin 필드에 요청을 보내는 출처를 함께 담아서 송신

#### CORS 해결 방법

- [서버]: Access-Control-Allow-Origin 헤더에 값 (Ex. \* 또는 명시적 도메인 URL) 세팅하거나 보통은 CORS 관련 미들웨어 라이브러리 사용한 해결
- [클라이언트]: 대부분 로컬 개발 시 webpack-dev-server 사용하는 것이 관례적.
  - http-proxy-middleware 라이브러리 사용 통한 CORS 문제 우회 가능
  - 로컬 환경에서 /api로 시작하는 URL로 보내는 요청에 대해 브라우저는 localhost:8000/api 로 요청을 보낸 것으로 알고 있지만 뒤에서는 웹팩이 다른 출처로 요청을 프록싱해주기 때문에 마치 CORS 정책을 지킨 것처럼 보이게 만들 수 있음.
  - 권장되는 사용 상황
    - 클라이언트 앱 소스를 서빙하는 출처와 API 서버의 출처가 같은 경우에 사용

#### 브라우저 저장소 종류와 차이점

- [Web-Storage] <-- HTML5에서 추가된 스펙, 아래 2가지 존재
  - [공통]
    - 단순 문자열 뿐만 아니라 객체 정보 저장 가능
    - 용량 제한 없음
    - 영구 데이터 저장 가능
  - [Local] Storage
    - 명시적으로 지우지 않는 이상 영구적인 데이터 보관 가능
    - 브라우저 종료해도 데이터 보관 유지
    - 도메인마다 별도로 로컬 스토리지 생성
      - 도메인만 같으면 전역적으로 공유 가능
    - Windows 전역 객체의 LocalStorage 라는 컬렉션을 통해 저장과 조회 가능
  - [Session] Storage
    - 데이터의 지속성과 액세스 범위에 특수한 제한 존재
    - 도메인별로 별도로 생성
      - 같은 사이트의 같은 도메인이라도 브라우저가 다르면 서로 다른 영역임.
      - 탭 브라우징 또는 브라우저 하나 더 실행했을 때 이 2개는 별개의 영역
    - 지속적인 데이터 보관 불가능
      - 쿠키와 비슷한 성질
      - 현재 브라우징되고 있는 브라우저 컨텍스트 내에서만 데이터 유지
      - 브라우저 종료 시 데이터 소멸
    - Windows 전역 객체의 SessionStorage 라는 컬렉션을 통해 저장과 조회 가능
- [Cookie]
  - 하나의 사이트에서 저장할 수 있는 최대 쿠키 수는 20개
  - 저장할 수 있는 최대 쿠키 크기 4KB
  - 쿠키 설정 이후 모든 웹 요청은 쿠키정보를 포함하여 서버로 전송

#### 이벤트 버블링 설명

- **하위요소에서 상위요소로의** 이벤트 전파 방식
- HTML 구조상 자식요소에 발생한 이벤트가 상위의 부모요소에까지 영향을 미치는 것
- 한 요소에 이벤트가 발생하면 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러가 동작하고 최상단의 부모 요소를 만날 때까지 반복되면서 핸들러가 동작하는 현상
- 코드 구현 예제
  - 모든 요소에 click 에 대한 addEventListener 장착

#### 이벤트 캡쳐링 설명

- **상위요소에서 하위요소로의** 이벤트 전파 방식
- 최상위 태그에서 해당 태그를 찾아 내려가는 방식
- 코드 구현 예제
  - 모든 요소에 click 에 대한 addEventListener 장착
  - 이벤트 리스너 장착 시점에 capture: true 옵션 지정

#### 이벤트 버블링 / 캡쳐링 막는 방법 설명

- **이벤트 리스너 구현체 내 e.stopPropagation() 추가** (참고. 번식, 포교의 뜻)

#### 렌더링 방식 종류와 각각에 대한 설명

- 클라이언트 사이드 렌더링 (CSR)
- 서버 사이드 렌더링 (SSR)

#### SPA (Single Page Application) 설명

- **단일 페이지**로 구성된 웹앱 의미
- 화면 이동 시 필요한 데이터를 서버로부터 HTML로 전달받지 않고 필요한 데이터만 JSON 형태로 전달 받아 동적으로 렌더링 (로딩 시간 빠름)
  - 네이티브 앱과 유사한 사용자 경험 제공 가능
- 초기 렌더링 시에만 HTML 구성, 이 후에는 필요한 데이터만 JSON 형태로 서버에서 전달 받으므로 속도 빠름
- 장점 정리
  - 빠른 로딩 시간
  - 캐싱 작업 적합 (서버로부터 받은 모든 데이터를 저장 가능하므로 사용자가 OFFLINE 상태일지라도 동작)
  - 사용자 경험 개선 (로딩 X)
  - 빠른 개발 속도 (확실한 프론트 / 백엔드 간의 업무 분리)
    - 프론트엔드 독립적으로 빌드 / 테스트 / 배포 가능
- 단점 정리
  - 검색 엔진 최적화 어려움, SEO 대응 문제
  - 잘못된 구조의 SPA 는 로딩 시간의 이점을 가져가지 못함

#### 매개변수(Parameters)와 인수(Arguments) 설명

- 매개변수 (Parameters)
  - 함수의 정의에서 전달받은 인수를 **함수 내부로 전달하기 위해 사용**하는 변수
  - 함수 등에서 사용되는 전달된 값을 받는 변수
- 인수 (Arguments)
  - 함수가 호출될 때 **함수로 값을 전달해주는 값**
  - 값, 변수, 참조 등 전달되는 값

#### HTML에 대한 설명

- [Hypertext-Markup-Language], 하이퍼텍스트를 작성하기 위해 개발되었음
- 웹 문서를 만들기 위한 기본적인 웹 언어
- 웹의 구조를 담당 (구조 구성, 예: 제목, 문단, 표, 이미지, 동영상 등의 구조 구성)
  - [html-태그]: HTML 문서의 최상위 Root, head와 body 태그 포함
  - [head-태그]: 문서에 대한 메타데이터(HTML 문서에 대한 정보) 정의
    - style, script, link, meta 태그 등
  - [body-태그]: 본격적으로 브라우저에 표현되어야 할 태그들이 들어가는 부분.
- HTML (기획자)
- 코드를 위에서 아래에서 순차적으로 처리
  - 그래서 script 태그 처리 방식 변경이 필요 (async or defer)

#### HTML 태그 (TAG) 자체에 대한 설명

- HTML의 요소 (Element)
- HTML 문서를 구성하는 기본 단위.
- 웹 문서에 어떤 표시를 해주는 것.
  - (예. 글 작성, 크기 변경, 모양 지정 등)

#### 빈 태그 (Empty Tag)에 대한 설명

- 종료되는 닫히는 태그가 존재하지 않는 태그.
  - (태그 사이에 내용을 넣을 수 없다.)
- 되도록이면 종료 태그를 붙이는 연습 필요.
  - (HTML5 에서는 붙이지 않아도 정상 동작, 혼용되어 사용되는 상황)
- 빈 태그들은 그 자체로는 역할을 하지 못함.
- 주로 속성과 값을 입력하는 것이 기본적인 사용법.

#### HTML 글자 (Inline), 상자 (Block) 개념 설명

- 요소가 화면에 출력되는 특성
  - 인라인, 블록, 인라인 블록 그리고 테이블 요소 존재.
  - 상세 설명
    - [인라인-요소]: 글자를 만들기 위한 요소들.
      - 포함한 컨텐츠 크기에 따라 자동으로 줄어드는 성질
      - 글자 요소는 가로, 세로 사이즈 지정 불가
      - 가로에 대한 패딩, 마진만 지정 가능
        - 예. span, img, a(anchor), br(break), span, label
    - [블록-요소]: 레이아웃을 만들기 위한 요소들.
      - 부모 요소의 크기만큼 자동으로 늘어남. (가로 너비로)
      - 세로 넓이는 컨텐츠 크기 만큼 줄어드는 성질.
      - 블록 / 글자 요소 포함 가능
      - 가로, 세로에 대한 패딩, 마진 지정 가능
        - 예. div, h1~6, ul(unordered), li, ol(ordered), p
    - [인라인-블록-요소]
      - 수평으로 쌓이는 특성
      - 가로, 세로 크기 지정 가능
      - 예. input, label 안의 input
    - [테이블-요소] (크게는 블록 요소, 테이블 요소는 조금 더 세부적인 블록 요소)
      - [tr](table row): 행, [td](table data): 열
      - 예. table

#### HTML 태그의 class 와 id 설명

- [class] 요소를 지칭하는 중복 가능한 이름
  - 태그 내에 클래스 이름 지정, CSS 파일 내에서 .클래스 이름으로 속성 지정 가능
- [id] 요소를 지칭하는 고유한 이름
  - 태그 내에 아이디 지정, CSS 파일 내에서 #아이디 이름으로 속성 지정 가능
- [data-이름] 요소에 데이터를 지정
  - 예. [html] data-dummy-data --> [js] element.dataset.dummyData

#### CSS 기본 문법

- 선택자 { 속성: 값; }
  - 선택자: 스타일(CSS)을 적용할 대상(Selector), HTML의 특정한 요소 (태그).
  - 속성: 스타일(CSS)의 종류(Property)

#### CSS 작성 방식 종류 및 설명

- [내장-방식]
  - 유지보수 측면에서 좋지 않음.
  - 선택자 (태그) 존재
- [인라인-방식]
  - 선택자 (태그) 없음 (원하는 요소에 직접적으로 스타일을 작성하므로)
  - 태그의 style 속성에 직접 스타일을 작성하는 방식
  - 유지보수 측면에서 좋지 않음.
- [링크-방식]
  - link 태그 사용하여 외부 CSS 문서를 연결하는 방식
  - 병렬 연결 방식
    - 여러 개의 link 태그 활용한 다수의 css 파일 로드
- [@import-방식]
  - 'import 규칙'이라 명명됨.
  - CSS 문서 안에서 또 다른 CSS 문서를 가져와 연결하는 방식
  - 직렬 연결 방식 (html --> main.css --> main2.css)
    - import 를 하는 css 코드 해석이 완료된 후에 수행 되므로 처리 지연이 발생할 수 있음.
    - 이를 활용해서 일부러 지연 처리를 할 수도 있음.

#### CSS 선택자 종류 설명

- 일반
  - 전체 선택자 (Universal Selector): '\*'
    - Ex. \* { color: darkblue; }
  - 태그 선택자 (Type Selector): 태그
    - Ex. div { color: red !important; }
  - 클래스 선택자 (Class Selector): .클래스
    - Ex. .color_green { color: green; }
  - 아이디 선택자 (ID Selector): #아이디
    - Ex. #color_yellow { color: yellow; }
- 복합
  - 일치 선택자 (Basic Combinator): 태그.클래스
  - 자식 선택자 (Child Combinator): 태그 > .클래스
    - Ex. ul, li 관계 내 ul > .orange
  - 하위(후손) 선택자 (Descendant Combinator): 태그 .클래스
    - Ex. div .container
    - Ex. .list li.item
  - 인접 형제 선택자 (Adjacent Sibling Combinator): .클래스 + 태그
    - 다음 형재 요소 1개 선택 (아래쪽)
  - 일반 형제 선택자 (General Sibling Combinator): .클래스 ~ 태그
    - 다음 형제 요소 모두 선택 (아래쪽)

#### CSS 가상 클래스 선택자 (Pseudo-Classes) 종류 및 설명

- [:hover]
  - 참고) 전환효과: transition 1s;
- [:active]
  - 마우스 클릭하고 있는 동안에만 효과 처리
- [:focus]
  - select, textarea, input 등 포커스 가능한 태그에만 가능.
  - 포커스를 강제로 넣고 싶다면 원하는 태그의 글로벌 속성 tabIndex 값을 -1로 설정.
- [:first-child]
  - 내부 형제 요소 중 첫째 선택.
- [:last-child]
  - 내부 형제 요소 중 막내 선택.
- [:nth-child(n)]
  - 내부 형제 요소 중 n째라면 선택.
  - 다른 Ex.
    - nth-child(2n) <-- n은 0부터 시작 (Zero-based numbering)
      - 0, 2, 4, 6...
    - nth-child(2n+1)
      - 1, 3, 5, 7...
- [:not(span)] - 부정선택자
  - span 이 아닌 요소 선택

#### CSS 가상 요소 선택자 (Pseudo-Elements) 종류 및 설명

- [::before]
  - 태그 내부 앞에 내용(Content)을 삽입.
  - 인라인(글자) 요소 (가로, 세로 지정 불가)
    - 참고. display: block 으로 지정하면 블록 요소로 변경 가능
  - ::before 라는 가상의 요소를 만들어서 내용 삽입
  - Ex. ::before { content: "삽입할 내용"}
- [::after]
  - 태그 내부 요소들의 뒤에 내용(Content)을 삽입.
  - Ex. ::after { content: "삽입할 내용"}

#### CSS 속성 선택자 (Attribute, ATTR) 설명

- 속성을 포함한 요소 선택
  - Ex. [disabled] { color: red; }
- 속성을 포함하고 명시된 값에 해당하는 요소 선택
  - Ex. [type="password"] { color: red; }

#### CSS 스타일 상속 설명

- 적용된 내용이 해당하는 요소의 자식요소 (하위요소)에 영향을 미치는 것을 상속이라고 함.
- [강제-상속]
  - 참고. height는 원래 상속되는 속성이 아님. inherit를 지정하면 강제로 상속받게 됨.
    - Ex. height, background-color 등

#### 패럴랙스 스크롤링 설명

- 주로 웹사이트에서 사용되는 기술. 스크롤에 따라 오브젝트와 배경 이미지가 시간차를 두고 변하는 기법
- 마우스를 스크롤할 때 원거리에 있는 배경 이미지는 느리게 움직이게 하고 근거리에 있는 사물 이미지는 빠르게 움직이도록 함으로써 입체감을 느낄 수 있게 만든 디자인 기법

#### CSS 선택자 우선순위에 대한 설명

- 같은 요소가 여러 선언의 대상이 된 경우, 어떤 선언의 CSS 속성을 우선 적용할 지 결정하는 방법
  - 1. 점수가 높은 선언 우선
    - style 인라인 선언 방식: 1000점
    - !important: 무한대 점수
      - Ex. div { color: red !important; }
    - 아이디 선택자: 100점
    - 클래스 선택자: 10점
    - 태그 선택자: 1점
    - 전체 선택자: 0점
      - body로 지정한 속성, 즉 상속으로 인한 속성 지정은 점수가 없음.
  - 2. 동 점수면 가장 마지막에 해석된 선언 우선
- 선언에 대한 우선순위 점수 계산법
  - [예시]
    - .list li.item: 클래스 2개, 태그 1개 => 21점
    - .list li:hover: 클래스 1개, 태그 1개, 가상클래스 1개 => 21점
    - .tile::before: 클래스 1개, 가상 요소 선택자 1개 => 11점
    - #submit span: 아이디 선택자 1개, 태그 선택자 1개 => 101점
    - :not(.box): 클래스 선택자 (부정 선택자) 1개, 클래스 선택자 1개 => 10점

#### CSS 속성 용어 (Properties)

- 속성
  - 용어 용법
    - HTML: Attributes
    - CSS & JS: Properties
  - 속성 & 속성값
    - [width-height]
      - 속성 기본값: auto
    - [auto-값]: 요소에 이미 들어있는 속성의 값 (브라우저가 너비를 계산)
      - 참고. **span** <-- 대표적인 인라인 요소 (글자 요소)
        - 가로, 세로 너비는 콘텐츠 크기만큼 줄어듬.
        - 가로, 세로 너비 지정 불가 (글자 요소이므로)
      - 참고. div에 height를 지정하지 않으면 표시되지 않음.
        - **div** <-- 대표적인 블록 요소
        - 가로는 부모 요소의 크기만큼 최대한 늘어남
        - 세로는 포함한 콘텐츠 크기만큼 자동으로 줄어듬.
    - [max]
      - max-width, max-height 속성 기본값: none
    - [min]
      - min-width, min-height 속성 기본값: 0 (단위 불필요)
    - [margin]
      - 요소의 외부 여백(공간)을 지정하는 **단축 속성**
      - 참고. 음수값 지정 가능.
        - Ex. margin: 10px; / margin: 10px 15px; / margin: 10px 20px 30px; / margin: 10px 20px 30px 40px (시계 방향);
    - [padding]
      - 요소의 내부 여백(공간)을 지정하는 **단축 속성**
      - 내부 여백 주는 경우 요소 내 여백이 생기는 것이므로 요소의 크기가 늘어남
    - [border]
      - 테두리 선 지정하는 **단축 속성**
      - 테두리 두께가 증가하면 요소의 크기가 커짐
      - Ex. border: 4px solid yellow; / none으로 설정하면 표시되지 않음.
      - **border-width**
        - 기본값: medium 중간두께 / **개별속성이자 단축속성**
        - Ex. border-width: 10px 20px 30px 40px
      - **border-style**
        - 기본값: none (선 없음) / **개별속성이자 단축속성**
      - **border-color**
        - 기본값: black / **개별속성이자 단축속성**
        - transparent 투명도 지정 가능
        - 색상 지정 방법
          - 브라우저 제공 색상 (Ex. red, yellow 등)
            - 실제 개발 시에는 브라우저마다 제공 색상이 조금씩 다를 가능성이 있으므로 16진수 색상으로 정확하게 지정하는 것이 권장.
          - 16진수 색상
          - 삼원색 (RGB): Ex. rgb(255, 255, 255)
          - 삼원색 + 투명도 (RGBA): rgba(0, 0, 0, 0.3)
          - HSL (색상, 채도, 명도): hsl(120, 100%, 50%)
          - HSLA (색상, 채도, 명도 + 투명도): hsla(120, 100%, 50%, 0.3)
      - **border-radius**
        - 기본값: 0 / **개별속성이자 단축속성**
          - 왼쪽 상단 ~ 왼쪽 하단까지 시계 방향
      - **box-sizing**
        - 요소의 크기 계산 기준을 지정
        - **content-box**: **기본값**, 요소의 내용으로 크기 계산
        - **border-box**: 요소의 내용 + padding + border로 크기 계산
          - 요소에 지정한 가로, 세로 너비만큼 정확한 크기로 내부 여백과 테두리선을 추가하고 싶을 때 사용
    - [overflow]
      - 요소의 크기 이상으로 내용이 넘쳤을 때 보여짐을 제어하는 단축 속성
      - 기본값: visible
        - visible: 그대로 보여줌
        - hidden: 넘친 내용을 잘라냄
        - scroll: 넘치는 경우 스크롤 표시 (가로, 세로를 무조건 표시)
        - auto: 넘치는 부분 (세로 또는 가로)에 대해서만 스크롤 표시
      - child 요소가 넘쳤을 때 parent 요소에서 overflow를 지정 가능
      - overflow-x / overflow-y
    - [display]
      - block: 상자 요소
      - inline: 글자 요소
        - Ex. span CSS 에서 display 를 block 으로 변경하면 가로, 세로값 지정이 가능
      - inline-block : 베이스는 글자이나 가로/세로값 지정 가능
      - flex
      - grid
      - none
      - table / table-row / table-cell 등
    - [opacity]
      - 1: 불투명 (기본값)
      - 0: 완전 투명
        - 참고. .5 = 0.5 와 동일
    - [글꼴]
      - **line-height**: 한 줄의 높이 (행간)
        - 기본값: normal (1)
        - 숫자 (권장): 요소가 가지고 있는 폰트 사이즈의 배수
          - 2배의 높이를 지정하려면?
            - 2 또는 200% 로 지정한다.
      - **font-family**: 글꼴(서체) 지정
        - 글꼴계열 필수 작성해야 함. (Ex. serif - 바탕체 계열)
          - serif 바탕체 계열
          - sans-serif 고딕체 계열
          - monospace (고정너비(가로폭 동등))
      - **font-style**
      - **font-weigth**: 기본값 normal (400)
        - bolder / lighter는 상대적인 속성 (부모요소보다 더 진하게 / 얇게)
    - [문자]
      - **text-decoration**
        - 기본값: none
        - a 태그의 경우 기본적으로 text-decoration이 지정되어 있음.
      - **text-align**
        - 기본값: left
      - **line-height** 에 요소의 height를 지정해주면 수직 가운데 정렬
      - **color**: 글자의 색상
        - 기본값: rgb(0,0,0)
      - **text-indent**: 들여쓰기
        - 기본값: 0 (들여쓰기 없음)
        - outdent 는 음수를 사용함으로써 구현 가능
    - [background]
      - **background-color**
        - 기본값: transparent
      - **background-image** : 요소의 배경 이미지 삽입
        - Ex. url("./images/image.png");
        - background-color 지정 후 background-image 를 지정하면 배경 색상은 이미지 뒤에 표시
      - **background-size**
        - Ex. 200px (바둑판식 배열 형태로 출력)
      - **background-repeat** : 이미지 반복 여부 결정
        - 기본값: repeat (이미지를 수직, 수평 반복)
        - Ex. background-repeat: no-repeat;
      - **background-position** : 이미지 위치 결정
        - 기본값: 0% 0%
        - Ex. background-position: center; / background-position: top right;
        - Ex. background-position: 100px 30px;
      - **background-size**
        - 기본값: auto (이미지 실제 크기)
        - cover: 요소의 X, Y 값 중 큰 쪽에 맞춰지는 속성값
        - contain: 요소의 X, Y 값 중 작은 쪽에 맞춰지는 속성값
      - **background-attachment** : 배경 이미지 스크롤 특성
        - 기본값: [scroll] (이미지가 요소를 따라 같이 스크롤)
          - 요소가 스크롤을 통해 위로 올라갈 때 배경 이미지도 같이 올라감
        - [fixed]: 이미지가 뷰포트에 고정, 스크롤 불가능
          - 요소는 올라가는데 이미지는 고정
          - 패럴렉스 (Parallax)
    - [요소-배치]
      - position: 요소의 위치 지정 기준
        - 기본값: [static] (기준 없음)
        - [relative]: 요소 자기 자신을 기준
          - relative를 지정한다고 해도 화면에는 아무런 변화 없음
          - 원래 자기 자신의 위치를 기준으로 위치 재산정
            - Ex. relative position 설정 후 top / left 지정하면 원래 자기가 있었던 위치를 기준으로 이동됨
            - 단독으로 배치하는 용도로는 잘 쓰이지 않음
            - 실제로는 원래 자리에 그대로 있는 것과 같다
        - [absolute]: 위치 상 부모 요소를 기준
          - absolute 를 지정하면 주변과의 상호관계가 무너짐.
          - 상위 요소 중 position 기준을 가지고 있는 요소가 부모 요소
            - 구조상의 부모 요소가 아닌 위치상의 부모 요소
          - 만약 부모 요소가 없다면 body => html => viewport 까지 찾는다.
          - display 속성이 자동으로 block 으로 변경
        - [fixed]: 뷰포트(브라우저) 기준
          - 지정하게 되면 주변과의 상호관계 무너짐.
          - 부모 요소에 위치 지정 값이 있더라도 무조건 뷰포트 기준으로 배치
          - 스크롤 하더라도 배치 유지됨 (헤더 / 배너 등)
          - display 속성이 자동으로 block 으로 변경
        - [sticky]: 스크롤 영역 기준
    - [Stack-Order]
      - 1. 요소에 position 값이 있는 경우 위에 쌓임
      - 2. position 값이 있는 상황 하 z-index 속성 값이 높을 수록 위에 쌓임
      - 3. 나중에 작성된 HTML 요소일수록 위에 쌓임
      - 참고
        - z-index 기본값: 0 (auto) => 부모 요소와 동일한 쌓임 정도
        - 음수도 가능하나 일반적으로 -1 이외의 다른 값은 사용하지 않음
    - [flex]
      - 속성 지정 => display: flex (일반적인 사용) / display: inline-flex 사용의 경우도 있음 => 아이템들이 수평으로 쌓임
        - Flex Container
          - flex-flow
          - flex-direction
            - 주 축(Main-axis)을 설정
            - 기본값: row (좌 => 우), row-reverse (우 => 좌)
          - flex-wrap
            - 줄 바꿈 여부
            - 기본값: nowrap (줄 바꿈 없음. 하나의 줄에 아이템들이 추가됨)
              - 기본값인 경우 한줄에 아이템을 다 표시하려다보니 아이템 너비가 찌그러기도 함.
            - wrap: 여러 줄로 묶겠다라는 의미. 칸이 모자라면 여러줄로 표현
          - justify-content
            - 주 축의 정렬 방법 (flex-direction에 따라 주 축은 변경됨)
            - 기본값: flex-start
          - align-content
            - 교차 축의 **여러 줄** 정렬 방법
            - 여러 줄일때에만 동작 (flex-wrap 이 wrap 인 경우)
            - 기본값: stretch
            - flex-start: 전체 컨텐츠가 교차축쪽으로 정렬
          - align-items
            - 교차 축의 **한 줄** 정렬 방법
            - 기본값: stretch
              - 참고. stretch 는 아이템의 width / height가 없을 때만 동작
        - Flex Items
          - order
            - 기본값: 0 (순서없음)
            - 숫자가 작을수록 앞 순서로 배치
          - flex
          - flex-grow
            - 아이템의 증가 너비 비율
            - 기본값: 0 (증가 비율 없음)
            - 참고. 증가비율이 없는 아이템 2개와 증가비율 1인 아이템 1개가 있다면.
              - 증가 비율이 없는 아이템 2개의 너비는 그대로 유지
              - 증가비율 1인 아이템이 나머지 공간을 차지
              - 즉, 증가비율이 있는 아이템들끼리 공간을 나눠가진다.
          - flex-shrink
            - 아이템의 감소 너비 비율
            - 기본값: 1 (Flex Container 너비에 따라 감소 비율 적용)
            - 0으로 지정하면 Flex Container 너비와 상관없이 원래 아이템 크기를 유지
          - flex-basis
            - 0 을 지정하고 flex-grow 값을 지정하면 비율 정상 적용됨
            - 기본값: auto (요소의 내용 너비, Ex. 내용: 요소 내 글자 크기)
          - align-self
    - [전환-효과]
      - transition
        - 요소의 전환(시작과 끝) 효과를 지정하는 단축 속성
        - 기본값: all (모든 속성에 적용, 사용할 수 있는 모든 CSS 속성에 적용된다라는 의미)
        - Ex.
          - transition: all 300ms ease-in;
          - transition: width 1s;
          - 속성 개별적으로 지정 가능
            - Ex. transition: width .5s, background-color 2s;
            - Ex. transition: transform .1s, background-color .6s;
      - transition-duration
        - 전환 효과 지속 시간
        - 기본값: 0s (전환 효과 X)
      - transition-timing-function
        - 타이밍(easing) 함수 지정
          - ease: 느리게 - 빠르게 - 느리게
          - linear: 일정하게
          - ease-in: 느리게 - 빠르게
          - ease-out: 빠르게 - 느리게
          - ease-in-out: 느리게 - 빠르게 - 느리게
      - transition-delay
        - 전환 대기 시간
        - 기본값: 0s (대기시간 없음)
        - Ex. transition: 1s .5s;
    - [변환-효과]
      - Ex. transform: rotate(45deg) scale(1.3)
        - 45도 각도 회전, 요소 크기 1.3배 증가
      - 2D 변환 함수
        - translate(x, y) <= 이동
          - Ex. transform: translate(40px, 40px)
        - scale(x, y) <= 크기 증가, Ex. 1.3
        - rotate(degree) <= 회전, Ex. 45deg
        - skew(x, y) <= 기울임, Ex. 45deg
      - 3D 변환 함수
        - translateZ(z) <= 이동(z축)
        - perspective(n) <= 원근법(거리)
        - rotateX(x) <= 회전 (x축 기준)
        - rotateY(y) <= 회전 (y축 기준)
          - rotateX, rotateY는 원근법 지정이 없으면 회전 속성을 주더라도 변화 없음
          - perspective 까지 같이 지정하면 변화 있음
            - perspective 함수는 transform 에 제일 앞부분에 작성해야 함
            - Ex. transform: perspective(500px) rotateX(45deg);
      - perspective 속성과 함수 간 차이점
        - 적용 대상
          - 속성: 관찰 대상의 부모 요소에 지정 (부모 요소의 정가운데 기준)
          - 함수: 관찰 대상 자체에 지정 (관찰 대상의 정가운데 기준)
      - backface-visibility
        - 3D 변환으로 회전된 요소의 뒷면 숨김 여부
        - 기본값: visible (뒷면 보임)
        - Ex. transform: rotateY(180deg); backface-visibily: hidden;

#### Display 속성이 Block 값으로 자동으로 바뀌는 Position 속성의 값 설명

- absolute
- fixed

#### CSS 단위 종류와 각각에 대한 설명

- [px] : pixel
- [%] : 백분율 (상대적)
- [em] : 요소의 글꼴 크기 (상대적)
  - 기본값: 1em
  - em 단위의 기준: 해당하는 요소의 글꼴 크기
- [rem] : 루트 최상위 요소(html)의 글꼴 크기
  - 참고. 부모 요소의 폰트 사이즈를 변경해도 자식 요소에 영향 없음.
  - 참고. html 요소 자체의 폰트 사이즈를 변경해야만 영향이 있음.
- [vw] : 뷰포트 가로 너비의 백분율
  - 뷰포트: 브라우저 화면의 출력되는 페이지 전체의 영역.
  - Ex. 1vw: 뷰포트 가로 너비의 1/100 크기
- [vh] : 뷰포트 세로 너비의 백분율
- [참고]. html은 기본적으로 폰트 크기를 16px로 지정.
  - 10em: 16 X 10 = 160px
  - 20em: 16 X 20 = 320px
    - 참고. 만약 부모 요소의 폰트 사이즈를 10px로 지정한다면?
      - 10em: 10 X 10 = 100px
      - 20em: 10 X 20 = 200px

#### 0px, 0vw, 0 중 더 큰 값

- 0이라는 수치는 단위에 상관없이 모두 같은 값임.

#### 자바스크립트 라이브러리 종류

- jQuery, Umbrella JS
- Chart.js, Apexcharts, Algolia Places
- D3.js
- TaffyDB, ActiveRecord.js
- wForms, LiveValidation, Validanguage, qForms
- Anime.js, JSTweener
- ImageFX, Reflection.js
- typeface.js
- Date.js, Sylvester
- ReactJS, Glimmer.js
- underscore.js, lodash

#### Axios 예외처리 방법 설명

- 1. Axios를 감싸는 함수 제작
- 2. **Interceptor** 사용

#### 요소 가운데 정렬 방법 설명

- 1. 부모 요소 display: flex 설정 후 justifyContent, alignItems 모두 center 지정
- 2. block 부모 요소의 경우 margin: 0 auto; 설정
  - 위, 아래: 0, 좌, 우: auto
  - 기본적으로 블록 요소에 가로 사이즈가 있는 상태에서 마진 값의 좌우가 auto 라면 가운데 정렬이 됨.
- 3. inline 자식 요소의 경우 부모 요소에서 text-align: center; 설정

#### 리액티브 프로그래밍 설명

- 이벤트나 배열 같은 데이터 스트림을 비동기로 처리하여 변화에 유연하게 반응하는 프로그래밍 패러다임
- **Push** 시나리오 사용
  - 참고:
    - Pull 시나리오: 데이터를 가지고 오기 위해서 계속 호출 필요
    - Push 시나리오: 응답이 오면 그때 반응하여 처리, 데이터를 가지고 오기 위해서 구독 필요

#### RxJs 사용법 / 설명

- Reactive Extensions For Javascript 라이브러리
  - ReactiveX 는 Observer, Iterator 패턴, 함수형 프로그래밍을 조합하여 제공
- 이벤트 Stream => Observable 객체로 표현
- Observer에는 3가지 메서드 존재
  - next
  - complete
  - error
- 이벤트 다룰 때 거치는 절차
  - Observable 정의 / 가공
  - Observer 정의
    - Observable 로 부터 이벤트를 전달받으면 어떻게 처리할 지를 정의
    - Ex. console.log / 다른 함수 호출 등
  - Observable Observer 연결
    - Observer와 Observable 연결 (observable.subscribe())
- Observable 이벤트를 동기 또는 비동기로 발생시킬 수 있음
- 구독 함수 호출하면 구독 취소 용도로 사용할 subscription 객체를 리턴받음
- Subject
  - 멀티캐스트를 위한 Observable
  - 하나의 Observable을 구독하는 여러 개의 Observer를 생성 / 등록 가능
  - Observable 이지만 Observer 로서 또 다른 Observable 을 구독 가능

#### 번들링 개념 설명

- **번들링 = 빌드**
- 여러 코드와 프로그램들을 묶는 행위
- 간략 과정
  - 개발자 => 번들링된 웹 앱 제작
  - 사용자 => 번들링한 파일을 받아와 브라우저가 번들 수행
- 번들링의 이유
  - 원본 프로그램 파일보다 크기가 작아지고 실행 속도, 로딩 속도 증가
  - 사용자가 임의로 조작 불가
  - 변수 중복 선언 / 의도치 않은 값 할당으로 인해 발생하는 에러 해결
    - 번들링 도구인 Webpack 에서는 모듈 번들링으로 해결

#### Webpack

- 번들링 도구, 번들러
- 자바스크립트 앱을 위한 모듈 번들러
  - HTML, CSS, Javascript 등을 각각의 모듈로 보고 이를 조합해 하나의 묶음으로 번들링, 즉 빌드하는 도구
    - 이미지 파일, 기타 파일 모두 포함
- 모듈 번들러 등장 배경
  - 모던 웹 발전으로 HTML, CSS 내용이 자바스크립트 안으로 들어옴
  - JS 양 증가
  - 세분화된 모듈 파일 증가
  - 의존성 트리의 복잡도 / 규모 증가
  - 자바스크립트 변수 스코프 문제 + 웹 앱을 실행할 때 네트워크 쪽의 비용 문제 발생
- 모듈 번들러의 솔루션
  - 시작점 (index.js)로부터 의존성을 가지는 모듈을 모두 추적해 의존성 그래프를 만들고, 하나의 결과물을 만들어 내는 방식 채택
    - 네트워크 비용 감소 (일일이 서버에 요청해 자원 얻어올 필요 X)
      - 같은 타입의 자원을 요청해 요청과 응답을 주고 받음
    - 자바스크립트 문법 버전 호환성 지원
      - loader 사용한 자바스크립트 ES6 문법을 ES5로 변환해주는 babel-loader 이용 가능
    - Development / Production 모드 선택 가능
      - Production 모드에서는 코드 난독화, 압축, 최적화 작업 지원
- 모듈 번들러 설정 커스터마이징
  - webpack.config.js 설정
    - entry
    - output
    - loader
      - Webpack은 기본적으로 자바스크립트와 JSON 파일만 이해 가능.
      - 다른 유형 파일 처리를 위해서는 loader 사용 필수
    - plugins
      - loader 보다 더 넓은 범위의 작업 수행
      - 번들 최적화 / 에셋 관리 / 환경변수 주입 등
    - mode
      - development / production / none 3가지 모드 존재
      - 기본값: production

#### GraphQL 설명

- 페이스북에서 만든 쿼리 언어.
- 애플리케이션 프로그래밍 인터페이스 (API) 를 위한 쿼리 언어.
- GraphQL 이라는 **서비스 브로커의 개념**
- 클라이언트 측에서는 서버를 알 필요 없이 GraphQL 레이어와만 통신하면서 데이터를 가져옴
- 장점
  - 유지 보수 / 확장 용이한 API 구현 가능
    - 이중 삼중 API Call 로직의 삭제
  - 필요한 일을 스키마 단위로 파악 가능 / 필요 정보를 유연하게 가져오는 것 가능
  - 요청 횟수가 줄어듬으로써 서버의 리소스 최적화가 가능, 클라이언트 요청에 대한 부담 줄어듬

#### 라이브러리, 모듈 생성의 이유

- 역할의 분리 목적
- 코드의 재사용 / 부품화 목적
- 대형 어플리케이션 개발 시간의 단축 목적

#### 표기법 종류와 설명

- dash-case (Kebab-case)
  - HTML / CSS
- Snake_case (스네이크케이스)
  - HTML / CSS
- camelCase (카멜케이스)
  - Javascript
  - 앞 글자 소문자
- PascalCase (파스칼케이스)
  - Javascript
  - 앞 글자 대문자

#### Zero-Based Numbering 설명

- 프로그래밍 기본 개념
- 0 기반 번호 매기기.
  - 배열 인덱스, 요일 정보 (0: 일요일)
- 특수한 경우를 제외하고 0부터 시작.

#### 자바스크립트 undefined, null 설명

- undefined: 값이 할당되지 않은 상태
- null: 어떤 값이 의도적으로 비어있음 의미

#### 특수 문자 명명법

- 백틱 (그레이브 (작은 역따옴표))
- 틸드 (물결 표시)
- 익스클러메이션 (느낌표)
- 앳 사인 (골뱅이),
- 샵, 넘버 사인
- 달러 사인
- 퍼센트 사인
- 캐럿 (^) 사인 (~ 이상 표현 시 사용)
- 앰퍼샌드
- 애스터리스크 (\*)
- 하이픈, 대시, 마이너스 (-)
- 언더스코어, 로대시 (Low dash) (\_)
- Equal sign
- Quatation (")
- Apostrphe (')
- Colon (:), SemiColon (;), Comma (,)
- Period, Dot (.)
- Question mark (?)
- Slash (/)
- Vertical bar (|)
- Backslash (\)
- Parenthesis (퍼렌서시스, 소괄호, 괄호 --> () )
- Brace {}
- Bracket []
- Angle Bracket, 꺽쇠괄호 ( <> )

#### 웹 이미지에 대한 설명

- **레스터 이미지 (JPEG / GIF / PNG)**
  - 픽셀이 모여 만들어진 정보들의 집합 (비트맵)
  - 정교하고 다양한 색상을 자연스럽게 표현 가능
  - 확대 / 축소 시 계단 현상 및 품질 저하 현상 발생
  - 종류
    - **JPG** (Joint Photographic coding Experts Group)
      - 손실 압축 방식 => 용량의 획기적 감소 효과
      - 24비트 (약 1600만 색상) 표현 가능
      - 반복적으로 새롭게 저장하는 행위 지양 => 품질 저하
      - 이미지의 품질과 용량을 쉽게 조절 가능
      - 가장 널리 사용되는 이미지 포맷
    - **PNG** (Portable Network Graphics)
      - GIF의 대체 포맷으로 개발
      - 비손실 압축 (JPG와 비교했을 때 상대적으로 용량 큼)
      - 8비트 (256색상) / 24비트 (약 1600만 색상) 표현 가능
      - 알파 채널 지원 (가장 큰 특징, 투명한 부분 사용 가능)
      - 원하는 이미지 영역만 처리 가능
      - W3C 권장 포맷
    - **GIF** (Graphics Interchange Format)
      - 이미지 파일 내 이미지 및 문자열 같은 정보 저장 가능
      - 비손실 압축
      - 애니매이션 지원
      - 8비트 (256색상) 지원
    - **WebP** (Web + Picture)
      - JPG, PNG, GIF 모두를 대체 가능한 구글이 개발한 포맷
      - 손실 및 비손실 둘 다 지원
      - 애니매이션 지원
      - 알파 채널 지원 (손실과 비손실 모두 해당)
      - IE 지원 불가
    - **SVG** (Scalable Vector Graphics)
      - 마크업 언어(HTML/XML) 기반의 벡터 그래픽을 표현하는 포맷
      - 해상도 영향에서 자유로움
        - 점, 선 그리고 면에 대한 수학적인 정보만을 가지고 있는 포맷이기 때문에 이 정보가 유효하기만 한다면 어느 해상도든 만들어 낼 수 있음
        - CSS, JS 로도 제어 가능
        - 파일 및 코드 삽입 가능
          - svg 라는 태그로 구성되어 있음
  - **벡터(SVG) 이미지**: 점, 선 그리고 면의 위치(좌표), 색상 등 수학적 정보의 형태로 이루어진 이미지
    - 정교한 이미지 표현 어려움 (Ex. 인물, 풍경 등)
    - 확대 / 축소 자유로움 (용량 변화 X)
    - 주로 로고와 아이콘 표현에 적합 (Flat한 이미지에 적합)
      - 참고. Material Design: 고품질 디지털 경험을 구축할 수 있도록 구글에서 만든 디자인 시스템 / 방식

#### 자바스크립트 기명 / 익명함수 설명

- 익명함수 **표현** / 호출 방법
  - 표현: let testFunc = function () {}
  - 호출: testFunc()
- 기명함수 **선언** / 호출 방법
  - 선언: function testFunc() {}
  - 호출: testFunc()
- 호이스팅 관점에서의 차이점
  - 기명함수: 호이스팅 영향 O
  - 익명함수: 호이스팅 영향 X

#### WebRTC (Web Real-Time Communication) 설명

- 별다른 소프트웨어 없이 카메라, 마이크 등을 사용하여 실시간 커뮤니케이션을 제공해주는 기술
  - 화상통화, 화상 공유 구현 가능한 오픈 소스
  - 비디오, 음성 / 일반 데이터가 P2P방식으로 Peer간 전송되도록 지원
  - 자바스크립트 API 로 제공
  - 용어 정리
    - **Data Streams**
      - 연속적으로 흘러나오는 데이터들의 흐름, 끊임없이 생성되고 변하는 데이터의 흐름
    - **NAT(Network Address Translation)**
      - 네트워크 주소 변환
      - IP 패킷의 TCP/UDP 포트 숫자와 소스 및 목적지의 IP 등을 재기록하면서 네트워크 트래픽을 주고 받는 기술
    - **Signaling**
      - P2P 통신 일어나기 전 여러가지 정보를 교환하는 데 사용
        - P2P 스트리밍을 시작하기 전에 성공적으로 완료되어져야 함.
        - 세션 제어 메세지: 통신 초기화 / 오류 보고
        - 네트워크 구성: 외부 세계에 컴퓨터의 아이피 주소와 포트는 무엇인지 파악.
        - 미디어 기능: 브라우저에서 처리할 수 있는 코덱과 해상도는 무엇인지 파악
    - **SDP** (Session Description Protocol)
    - **JSEP** (Javascript Session Establishment Protocol)
    - **ICE** (Interactive Connectivity Establishment)
      - 두 단말이 서로 통신할 수 있는 최적의 경로를 찾을 수 있도록 도와주는 프레임워크
        - TURN, STUN 서버 사용한 경로 찾기
      - **STUN** (Session Traversal Utilities for NAT)
      - 해당 Peer의 Public IP 주소를 보내는 역할
      - **TURN** (Traversal Using Relays around NAT)
    - **ICE Candidate Gathering**
      - Local, Server, Relayed Address 등 통신 가능한 주소들을 모두 가져옴
  - **장점**
    - Latency 짧음
      - 별도 플러그인 또는 미디어 송출 관련 소프트웨어 설치 불필요
      - 러닝커브 낮음
      - 무료 라이센스
  - **단점**
    - 크로스 브라우징 문제
    - Peer To Peer 통신 위해서는 사용자 IP를 알아야 하나 대부분의 사용자는 방화벽 등을 사용하므로 서로 다른 네트워크 상에서 연결을 맺기 위해서는 STUN / TURN 서버가 반드시 필요하다.
  - 참고. P2P (Peer To Peer) 통신
    - 하나의 컴퓨터와 하나의 컴퓨터가 데이터를 주고 받는 형식.
    - 동등 계층 간 클라이언트 / 서버의 개념이 없이 동등한 노드들로 구성되어 데이터를 주고 받는다.
  - 보통의 WebRTC 기반 라이브 스트리밍 서비스에서의 미디어 처리 흐름
    - 비디오, 오디오 입력
    - 미디어 편집
    - 보안
    - 송출
    - 시그널링 / 보안
    - Origin
    - 믹싱
    - 녹화
    - 트랜스코딩
    - Edge
    - 수신

#### RTMP 설명

- Real Time Message Protocol
- Adobe 독점 프로토콜
- 비디오 / 오디오를 인터넷 상에서 실시간으로 스트리밍 데이터를 전송해서 불특정 다수들이 받아 볼수 있도록 하는 기술 규격
- 기본 1935포트 사용
  - 통신 실패 시 RTMPS(434)나 RTMPT(80) 포트 사용하여 통신 시도
- Ex. 인스타라이브, 유튜브라이브, 트위치 등은 RTMP 방식의 실시간 스트리밍

#### DOM API 설명

- 자바스크립트로 HTML을 작업할 때 사용하는 여러가지 명령들
- DOM (Document Object Model) API (Application Programming Interface)
  - Ex. querySelector / getElementsByTagName / parentNode 등
  - 참고. DOM
    - 브라우저는 웹 문서 로드 후 파싱하여 DOM 생성
    - 모든 요소, 속성, 텍스트 등을 객체로 만들고 부모-자식 관계에 따라 트리 구조로 구성
    - 정적 페이지 변경을 하는 유일한 방법은 DOM을 변경하는 것
      - 변경을 위해서 DOM API 필요
  - 참고. DOM Tree 구성요소
    - 문서 노드 (Document)
    - 요소 노드 (Element)
    - 속성 노드 (Attribute)
    - 텍스트 노드 (Text)

#### 프로토타입에 대한 설명

- 자바스크립트는 클래스 대신 기존의 객체를 복사하여 새로운 객체를 생성하는데 이러한 방식을 프로토타입 방식이라 함
- 새로운 객체가 생성되기 위한 원형이 되는 객체
  - 같은 원형으로 생성된 객체가 공통으로 참조하는 공간
- 프로토타입 객체를 참조하는 prototype 속성(함수 멤버)과 객체 멤버인 proto 속성 존재
- 자바스크립트는 프로토타입 기반 언어
- 자바스크립트에서 OOP로 개발하기 위해 사용하는 패턴
- 클래스 문법은 프로토타입 기반으로 만들어졌고 상속을 통해 재사용성을 높임
- 자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있는데 이것은 OOP의 상속 개념과 같이 부모 객체의 프로퍼티와 메소드를 상속받아 사용할 수 있음.
  - 이러한 부모 객체를 프로토타입 객체 또는 프로토타입이라고 함
- 프로토타입은 OOP 상속 개념과 같이 부모 객체의 프로퍼티와 메소드를 상속받아 사용할 수 있는데 이때 부모 객체를 프로토 타입

#### 프로토타입 체인 설명

- JavaScript는 특정 객체의 프로퍼티나 메소드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티 또는 메소드가 없다면 [[Prototype]]이 가리키는 링크를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메소드를 차례대로 검색하는 것

#### 일반 클래스 언어와 프로토타입 언어의 차이점

- 클래스 기반 언어는 클래스라는 틀 자체를 상속시킴
  - 상속시킨 틀을 이용하여 객체 생성
- 프로토타입 기반 언어는 객체들을 프로토타입으로 연결시킴
  - 클래스의 개념 없음

#### Join 메소드 설명

- 배열을 인수 기준으로 문자로 병합해서 반환
  - Ex. "AidenKooG".split('').reserve().join('')
    - '' 기준으로 하나씩 문자들을 병합

#### 메소드 체이닝 (Method Chaining)

- 메소드를 연결해서 붙여서 사용하는 것
- 메소드를 계속 이어서 작성하는 방법
- 해당 함수 내부적으로 return this를 마지막에 반환
- 메소드가 객체를 반환하면 그 반환 값인 객체를 통해 또 다른 함수 호출이 가능한 프로그래밍 패턴
- 함수.함수... 의 형태