# SQL - Managing Tables

## 1. Creat a table
> `CREATE TABLE` statement : 테이블 생성

<br/>

```SQL
CREATE TABLE table_name (
  column_1 data_type,
  column_2 data_type,
  ...,
  constraints
);
```
- 각 필드에 적용할 데이터 타입(data type)작성
- 테이블 및 필드에 대한 제약조건(constraints) 작성 <br/><br/>

```SQL
CREATE TABLE examples (
  examId INT AUTO_INCREMENT,
  lastName VARCHAR(50) NOT NULL,
  firstName VARCHAR(50) NOT NULL,  
  PRIMARY KEY (examId)
);
```
```SQL
-- Table 구조 확인
SHOW COLUMNS FROM examples;
```
- PRIMARY KEY : 해당 필드를 기본 키로 지정
- NOT NULL : 해당 필드에 NULL 값을 저장하지 못하도록 지정
- AUTO_INCREMENT attribute : 테이블의 기본 키에 대한 번호 자동 생성
  - 시작 값은 1이며 데이터 입력시 값을 생략하면 자동으로 1씩 증가
  - 이미 사용한 값을 재사용하지 않음
  - 기본적으로 NOT NULL 제약조건을 포함 <br/><br/>


## 2. Delete a table
> `DROP TABLE` statement : 테이블 삭제

<br/>

```SQL
DROP TABLE table_name;
```
- DROP TABLE statement 이후 삭제할 테이블 이름 작성 <br/><br/>


## 3. Modifying table fields
> `ALTER TABLE` statement : 테이블 필드 조작(생성, 수정, 삭제)  
ALTER TABLE ADD : 필드 추가  
ALTER TABLE MODIFY : 필드 속성 변경  
ALTER TABLE CHANGE COLUMN : 필드 이름 변경  
ALTER TABLE DROP COLUMN : 필드 삭제 

<br/>

```SQL
ALTER TABLE
  table_name
ADD
  new_column_name column_definition;
```
- ADD 키워드 이후 추가하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성 <br/><br/>

```SQL
ALTER TABLE examples
ADD age INT NOT NULL,
ADD address VARCHAR(100) NOT NULL;
```
- examples 테이블에 age와 address 필드 추가
- 단, age 필드는 정수 타입이 저장되며 NULL 값을 허용하지 않음, address 필드는 가변길이 문자열 최대 100자이며 NULL 값을 허용하지 않음 

<br/><br/>

```SQL
ALTER TABLE
  table_name
MODIFY
  column_name column_definition;
```
- MODIFY 키워드 이후 변경하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성 <br/><br/>

```SQL
ALTER TABLE examples
MODIFY lastName VARCHAR(10) NOT NULL,
MODIFY firstName VARCHAR(10) NOT NULL;
```
- examples 테이블의 lastName, firstName 필드를 가변길이 문자열 최대 10자이며 NULL 값을 허용하지 않도록 변경

<br/><br/>

```SQL
ALTER TABLE
  table_name
CHANGE COLUMN
  original_name new_name column_definition;
```
- CHANGE COLUMN 키워드 이후 기존 필드 이름, 변경하고자 하는 필드 이름과 데이터 타입 및 제약 조건 작성 <br/><br/>

```SQL
ALTER TABLE 
  examples
CHANGE COLUMN
  country state VARCHAR(100) NOT NULL;
```
- examples 테이블의 country 필드 이름을 state로 변경(단, 데이터 타입 및 제약조건은 기존과 동일)

<br/><br/>

```SQL
ALTER TABLE
  table_name
DROP COLUMN
  column_name;
```
- DROP COLUMN 키워드 이후 삭제하고자 하는 필드 이름 작성 <br/><br/>

```SQL
ALTER TABLE 
  examples
DROP COLUMN
  state,
DROP COLUMN
  age;
```
- examples 테이블의 state, age 필드 삭제

<br/><br/>

# SQL - Modifying Data

## 1. Insert data into table
> `INSERT` statement : 테이블 레코드 삽입

<br/>

```SQL
INSERT INTO table_name (c1, c2,...)
VALUES (v1, v2,...);
```
- INSERT INTO 절 다음에 테이블 이름과 괄호 안에 필드 목록을 작성
- VALUES 키워드 다음 괄호 안에 해당 필드에 삽입할 값 목록을 작성 <br/><br/>

```SQL
INSERT INTO
  articles (title, content, createdAt)
VALUES
  ('title1', 'content1', '1900-01-01'),
  ('title2', 'content2', '1800-01-01'),
  ('title3', 'content3', '1700-01-01');
```
- articles 테이블에 각 필드에 적합한 데이터를 3개 입력<br/><br/>


## 2. Update data in table
> `UPDATE` statement : 테이블 레코드 수정

<br/>

```SQL
UPDATE table_name
SET column_name = expression,
[WHERE
  condition];
```
- SET 절 다음에 수정할 필드와 새 값을 지정
- WHERE 절에서 수정할 레코드를 지정하는 조건 작성(WHERE 절을 작성하지 않으면 모든 레코드를 수정) <br/><br/>

```SQL
UPDATE 
  articles
SET 
  title = 'newTitle',
  content = 'newContent'
WHERE
  id = 2;
```
- articles 테이블 2번 레코드의 title, content 필드 값을 자유롭게 변경<br/><br/>

```SQL
UPDATE 
  articles
SET 
  content = REPLACE(content, 'content', 'TEST')
```
- articles 테이블 모든 레코드의 content 필드 값 중 문자열 'content'를 'TEST'로 변경
- REPLACE : '지정된 문자열 변경'<br/><br/>


## 3. Delete data from table
> `DELETE` statement : 테이블 레코드 삭제

<br/>

```SQL
DELETE FROM table_name
[WHERE
  condition];
```
- DELETE FROM 절 다음에 테이블 이름 작성
- WHERE 절에서 삭제할 레코드를 지정하는 조건 작성(WHERE 절을 작성하지 않으면 모든 레코드를 삭제) <br/><br/>

```SQL
DELETE FROM
  articles
ORDER BY
  createdAt DESC
LIMIT 2;
```
- articles 테이블에서 가장 최근에 작성된 레코드 2개를 삭제 