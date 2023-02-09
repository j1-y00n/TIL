# MySQL Workbench 활용 가이드

## 용어 설명
### DBMS(Database Management System)
> DB관리 소프트웨어 프로그램

<br>

### SQL(Structured Query Language)
> DB와 소통하기위한 언어

<br>

### MySQL
> RDBMS의 한 종류, SQL사용

<br>

### MySQL Workbench
> DB관리 툴, MySQL 서버 및 데이터베이스 작업을 위한 그래픽 도구

<br>

## MySQL Workbench 실행하기
1. MySQL 설치(macOS)
      ```
      brew install mysql
      ```

2. MySQL 실행

    터미널 입력
    ```
    mysql.server start
    ```
    터미널 출력
    ```
    Starting MySQL SUCCESS!
    ```

3. MySQL Workbench 다운로드 및 설치

4. 실행

    `! MySQL 서버를 실행한 상태로 Workbench 실행`

- Rescan servers 클릭
- MySQL Connections 클릭
- password 입력

<br>

## 실습 데이터베이스에 대한 쿼리(Query)문 작성 및 쿼리문 실행 방법
- 실습용 데이터베이스 추가
  1. MySQL 접속
  2. Administration -> Data Import/Restore 클릭
  3. Import from Self-Contained File 체크 -> 다운받은 sample.sql  파일 선택 -> start Import
  4. Import Completed

- 실습용 데이터베이스 확인
  1. Schemas 클릭
  2. 새로고침 버튼 클릭
  3. 데이터베이스 Classicmodels 확인

- 쿼리(Query) 실행 테스트
  1. Classicmodels 데이터베이스 선택(더블클릭)
  2. Query 에디터 클릭
  3. 쿼리문 입력
      ```SQL
      SELECT * FROM customers;
      ```
  4. 쿼리 실행
  5. 출력 확인