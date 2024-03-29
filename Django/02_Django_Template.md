# Django Template
<br><br>

>## Django Template Language(DTL)
- Template에서 조건, 반복, 변수, 필터 등의 프로그래밍적 기능을 제공하는 시스템
<br><br>

>## DTL Syntax
### 1. Variable
- view 함수에서 render 함수의 세번째 인자로 딕셔너리 타입으로 넘겨 받을 수 있음
- 딕셔너리 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨
- dot(.)를 사용하여 변수 속성에 접근할 수 있음
```django
  {{ variable }}
```
<br>

### 2. Filters
- 표시할 변수를 수정할 때 사용
- chained가 가능하며 일부 필터는 인자를 받기도 함
```django
  {{ name|truncatewords:30 }}
```
- 약 60개의 built-in template filters를 제공
```django
  {{ variable|filter }}
```
<br>

### 3. Tags
- 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
- 일부 태그는 시작과 종료 태그가 필요
```django
  {% if %} {% endif %}
```
- 약 24개의 buil-in template tags를 제공
```django
  {% tag %}
```
<br>

### 4. Comments
- 주석 표현
```django
  {% comment %} {% endcomment %}
```
<br><br>

>## Template inheritance(템플릿 상속)
### 1. 'extends' tag
- 자식(하위)템플릿이 부모 템플릿을 확장한다는 것을 알림
- `반드시 템플릿 최상단에 작성되어야 함(2개 이상 사용 불가)`
```django
  {% extends 'path' %}
```
<br>

### 2. 'block' tag
- 하위 템플릿에서 재정의(overridden)할 수 있는 블록을 정의
- `하위 템플릿이 작성할 수 있는 공간을 지정`
```django
  {% block name %} {% endblock name %}
```
<br><br>

>## HTML form
### 1. 'form' element
- 사용자로부터 할당된 데이터를 서버로 전송
- 웹에서 사용자 정보를 입력하는 여러 방식(text, password)을 제공
- '**action' & 'method**'
  - `form의 핵심 속성 2가지`
  - 데이터를 어디(`action`)로 어떤 방식(`method`)으로 보낼지 지정
  - action
    - 입력 데이터가 전송될 URL을 지정(목적지)
    - 만약 이 속성을 지정하지 않으면 데이터는 현재 form이 있는 페이지의 URL로 보내짐
  - method
    - 데이터를 어떤 방식으로 보낼 것인지 정의
    - 데이터의 HTTP request methods (GET, POST)를 지정
<br><br>

### 2. 'input' element
- 사용자의 데이터를 입력 받을 수 있는 요소
- type 속성 값에 따라 다양한 유형의 입력 데이터를 받음
- '**name**'
  - input의 핵심 속성
  - 데이터를 제출했을 떄 서버는 name 속성에 설정된 값을 통해 사용자가 입력한 데이터에 접근할 수 있음



