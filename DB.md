# DataBase

## Data
> 저장이나 처리에 효율적인 형태로 변환된 정보

<br>

## Database
> organized collection of data

> 데이터를 저장하고 조작
- Create (저장)
- Read (조회)
- Update (갱신)
- Delete (삭제)

<br>

## 관계형 데이터베이스 
> 데이터 간에 `관계(여러 테이블 간의 연결)`가 있는 데이터 항목들의 모음
- 서로 관련된 데이터 포인트를 저장하고 이에 대한 액세스 제공

1. Table (aka Relation)​
    - 데이터를 기록하는 곳
2. Field (aka Column, Attribute)​
    - 각 필드에는 고유한 데이터 형식(타입)이 지정됨
3. Record (aka Row, Tuple)​
    - 각 레코드에 구체적인 데이터 값이 저장됨
4. Database (aka Schema)
    - 테이블의 집합(set of tables)
5. Primary Key(PK)
    - 각 레코드의 고유한 값
    - 관계형 데이터베이스에서 레코드의 식별자로 활용
6. Foreign Key(FK)
    - 테이블의 필드 중 다른 테이블의 레코드를 식별할 수 있는 키
    - 각 레코드에서 서로 다른 테이블 간의 관계를 만드는데 사용

<br>

## RDBMS (Relational Database Management System)
> 관계형 데이터베이스를 관리하는 소프트웨어 프로그램
- 데이터 저장 및 관리를 용이하게 하는 시스템
- 데이터베이스와 사용자 간의 인터페이스 역할
  - 사용자가 데이터 구성, 업데이트, 모니터링, 백업, 복구 등을 할 수 있도록 도움
- MySQL 구조
```
table ⊂ Database ⊂ Database Server(MySQL)
 ```