# Python 기초

## 컴퓨터 프로그래밍 언어
> 컴퓨터에게 명령하기 위한 약속

## Python
- Easy to learn
- Expressive Language
- 크로스 플랫폼 언어
- 인터프리더(Interpreter) 언어
- 객체 지향 프로그래밍(Object Oriented Programming)

### 객체(object)
> 객체(Object) : 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것

### 변수(Variable)
> 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름
- 동일 이름에 다른 객체를 언제든 할당할 수 있음
- 변수는 할당 연산자(=)를 통해 값을 할당(assignment)
- type()
  - 변수에 할당된 값의 타입
- id()
  - 변수에 할당된 값(객체)의 고유한 값, 메모리주소
- 변수할당
  - 같은 값을 동시에 할당 할 수 있음
  ``` python
  x = y = 1
  ```
  - 다른 값을 동시에 할당 할 수 있음(multiple assignment)
  ``` python
  x, y = 1, 2
  ```

### 식별자(Identifiers)
> 파이썬 객체를 식별하는데 사용하는 이름
- Snake_case 형식 사용

<br>

## Type
- 숫자
  - 수치형(Numeric Type)
    - int (정수)
    - float (실수)
    - complex (복소수)
  - 불린형(Boolean Type) : True / False
- 시퀀스
  - 문자열
  - 리스트

## 연산자(Operator)
- 산술 연산자
- 복합 연산자
- 비교 연산자
- 논리 연산자 