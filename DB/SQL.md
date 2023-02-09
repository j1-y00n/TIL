# SQL(Structure Query Language)
> DB에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- SQL 키워드는 `대소문자를 구분하지 않음` (하지만 대문자로 작성하는 것을 권장 -명시적 구분)
- 각 SQL Statements의 `끝에는 세미콜론(;)이 필요` (세미콜론은 SQL Statements을 구분하는 방법)

<br>

## SQL Statements
> SQL 언어를 구성하는 가장 기본적인 코드 블록

<br>

### SQL Statements 유형
1. DDL(Data Definition Language)
    - 데이터의 기본 구조 및 형식 변경
    - 키워드 : `CREATE, DROP, ALTER`
2. DQL(Data Query Language)
    - 데이터 검색
    - 키워드 : `SELECT`
3. DML(Data Manipulation Language)
    - 데이터 조작(추가, 수정, 삭제)
    - 키워드 : `INSERT, UPDATE, DELETE`

4. DCL(Data Control Language)
    - 데이터 및 작업에 대한 사용자 권한제어
    - 키워드 : `COMMIT, ROLLBACK, GRANT, REVOKE`

<br>

## SQL - Single Table Queries
1. Querying data
    - `SELECT` statement : 테이블에서 데이터를 조회<br/><br/>

      ```SQL
      SELECT
        select_list1,
        select_list2
        ...
      FROM
        table_name;
      ```
        - `SELECT` 키워드 다음에 데이터를 선택하려는 `필드`를 하나 이상 지정
        - `FROM` 키워드 다음에 데이터를 선택하려는 `테이블`의 이름을 지정<br/><br/>

      ```SQL
      SELECT
        *
      FROM
        employees;
      ```
        - *(asterisk) : 테이블 employees에서 `모든 필드`의 데이터 조회<br/><br/>

      ```SQL
      SELECT
        firstName AS '이름'
      FROM
        employees;
      ```
        - 조회 시 firstName이 아닌 '이름'으로 출력명 변경
        - `AS keyword` : 필드에 새로운 별칭을 지정<br/><br/>

      ```SQL
      SELECT
        quantityOrdered + priceEach
      FROM
        orderdetails;
      ```
        - quantityOrdered와 priceEach 필드를 더한 결과 값 조회
        - 기본적인 `사칙연산` 사용 가능<br/><br/>

2. Sorting data
    - `ORDER BY` clause : 조회 결과의 레코드를 정렬<br/><br/>

      ```SQL
      SELECT
        select_list1,
      FROM
        table_name
      ORDER BY
        column1 [ASC|DESC],
        column1 [ASC|DESC];
      ```
        - `FROM clause 뒤`에 위치
        - 하나 이상의 컬럼을 기준으로 결과를 오름차순, 내림차순으로 정렬할 수 있음
            - ASC : 오름차순(기본 값)
            - DESC: 내림차순<br/><br/>

      ```SQL
      SELECT
        lastName, firstName
      FROM
        employees
      ORDER BY
        lastName DESC,
        firstName;
      ```
        - 테이블 employees에서 lastName 필드를 기준으로 내림차순으로 정렬한 다음 firstName 필드 기준으로 오름차순 정렬하여 조회<br/><br/>