# CS basic
### 1. IP와 도메인
- IP
  - 네트워크에 연결된 모든 컴퓨터에는 IP 주소(IP는 인터넷 프로토콜을 나타냄)라는 고유한 주소가 있음
  - 주소는 숫자를 4개의 점으로 구분하여 구성, ex) `173.194.121.32.`
  - 컴퓨터는 IP 주소로 다른 컴퓨터를 찾을 수 있음
- 도메인
  - 사람이 읽을 수 있는 IP 주소, ex) `google.com`
<br><br>

### 2. 클라이언트와 서버
- 클라이언트
  - 서비스를 요청하는 시스템 ex) 컴퓨터, 스마트폰 등
  - 웹에 접근하는 소프트웨어 ex) 크롬, 파이어폭스 등과 같은 웹브라우저
- 서버
  - 서비스를 제공하는 시스템
  - 웹페이지, 사이트, 앱을 저장하는 컴퓨터
<br><br>

### 3. 정적 웹 사이트와 동적 웹 사이트의 차이점 및 Django
- 정적 웹 사이트
- 동적 웹 사이트
- Django
  - web frameworks
  - 일반적인 문제 해결, 개발 속도 향상, 다양한 유형의 작업을 단순화하도록 설계된 함수, 객체, 규칙 및 기타 코드 구성요소의 모음
  - 직접 구현해야하는 많은 공통 웹 서버 기능을 제공(세션 지원, 사용자와 인증 지원, 데이터베이스와 쉬운 연결, 템플리트 라이브러리 등)


<br><br>

### 4. HTTP, 요청과 응답 메시지의 구성
- HTTP
  - HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜(데이터의 교환 방식을 정의하는 규칙 체계)
  - 웹에서 이루어지는 모든 데이터 교환의 기초
  - 클라이언트 - 서버 프로토콜
- 요청과 응답 메시지
  - 클라이언트와 서버들은 개별적인 메시지 교환에 의해 통신
  - **요청(requests)** : 클라이언트에 의해 전송되는 메시지
    - Method : 클라이언트가 수행하고자 하는 동작을 정의, ex) GET, POST, OPTIONS, HEAD...
    - Path : 가져오려는 리소스의 경로
    - Version of the protocol : HTTP 프로토콜의 버전
    - Headers : 서버에 대한 추가 정보를 전달
  - **응답(responses)** : 서버에서 전송되는 메시지
    - Version of the protocol : HTTP 프로토콜의 버전
    - Status code : 요청의 성공 여부와, 그 이유를 나타내는 상태코드
    - Status message : 상태코드의 짧은 설명
    - Headers : 요청 Headers와 비슷한 HTTP headers


### 5. 프레임워크
- 웹 어플리케이션을 작성하기 쉽고, 유지 및  보수기 쉽게 만드는 소프트웨어
- 웹 개발 작업을 단순화하는 도구와 라이브러리 제공