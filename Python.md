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
      ``` 
      True : 1, ''문자열'', [1, 2, 3], {"a" : 1}
      False : 0, " ", [], (), {}, None
- 시퀀스
  - 문자열(string)
  - 리스트(list)
  - 튜플(tuple)
  - 레인지(range)
- 컬렉션
  - 딕셔너리(dictionary)
  - 집함(set)

## 연산자(Operator)
- 산술 연산자
  - +, -, *, %(나머지), /, //(몫), **
- 복합 연산자
  - ex) a `+=` b  ->  a = a + b
- 비교 연산자
  - <, >, <=, >=, ==, !=
- 논리 연산자 
  - and, or, Not

## 컨테이너
> 여러개의 값을 담을 수 있는 것(객체)
- 시퀀스
  - 문자열 : 문자들의 나열
    - str
    - 작은 따옴표(')나 큰 따옴표(")를 활용하여 표기
      ``` python
      print("hello")
      ```
    - 인덱스는 0부터 시작함
    - 문자열 내에서 특정 문자나 조작을 위해서 역슬래시(\)를 활용하여 구분
    - 변경 불가능, 반복 가능
  - 리스트 : 변경 가능한 값들의 나열
    - 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
    - 변경 가능, 반복 가능
    - 항상 대괄호 형태로 정의, 요소는 콤마로 구분
      ``` python
      [0, 1, 2, 3, 4, 5]
      ```
    - 리스트는 대괄호([]) 혹은 list()를 통해 생성
    - 순서가 있는 시퀀스로 인덱스를 통해 접근 가능
  - 튜플: 불변한 값들의 나열
    - 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
    - 변경 불가능, 반복 가능
    - 소괄호 형태로 정의, 요소는 콤마로 구분
      ```
      (0, 1, 3)
      ```

## 컬렉션(collections)
- 딕셔너리(Dictionary)
  - 키-값(key-value) 쌍으로 이뤄진 모음
  - 키와 값은 :로 구분, 개별 요소는 ,로 구분 {키:값, 키:값}
  - 키는 불변 자료형만 가능(리스트, 딕셔너리 불가능)
  - 값은 어떠한 형태든 관계 없음
  - 변경 가능, 반복 가능
  - 메서드 활용 `keys(), values(), items() `
- 세트(Set)
  - 유일한 값들의 모음
  - 순서가 없고 중복된 값이 없음
  - 순서가 없어 별도의 값에 접근할 수 없음
  - 변경 가능, 반복 가능
  - 중괄호{}, 혹은 set()을 통해 생성(빈 Set를 만들기 위해서는 set()을 반드시 활용해야 함)

<br>

## 에러/예외처리
- 문법에러(Syntax Error)
- 예외(Exception) `try / except` 사용
  ```
  1. try : 코드실행
  2. except : try문에서 예외 발생 시 실행
  3. else : try문에서 예외가 발생하지 않으면 실행
  4. finally : 예외 발생 여부와 관계없이 항상 실행

<br>

## 파일 입출력
```
1. f = open('파일명.txt', 'w', encoding = 'UTF-8')
   f.write()
   f.close()

2. with ('파일명.txt', 'w', encoding = 'UTF-8') as f:
   f.write()
```
  
  - f.read() -> str type 통째로 읽기
  - f.readline() -> str type 한줄씩 읽기
  - f.readlines() -> list type
