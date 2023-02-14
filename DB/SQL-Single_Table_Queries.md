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
        select_list2
      FROM
        table_name
      ORDER BY
        column1 [ASC|DESC],
        column2 [ASC|DESC];
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

3. Filtering data
    - `DISTINCT` clause : 조회 결과에서 중복된 레코드를 제거<br/><br/>

      ```SQL
      SELECT DISTINCT
        select_list1
      FROM
        table_name;
      ```
        - `SELECT 키워드 바로 뒤`에 위치
        - SELECT DISTINCT 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드 지정<br/><br/>

    - `WHERE` clause : 조회 시 특정 검색 조건을 지정
      - Comparison Operators(비교 연산자)  
      =, >=, <=, !=, IS, LIKE, IN, BETWEEN...AND
      - Logical Operators(논리 연산자)  
      AND(&&), OR(||), NOT(!)
      - `IN` Operators  
      값이 특정 목록 안에 있는지 확인
      - `LIKE` Operators  
      값이 특정 패턴에 일치하는지 확인 with Wildcards
      - Wildcard Characters  
      '%' : `0개 이상의 문자열`과 일치 하는지 확인  
      '_' : `단일 문자`와 일치 하는지 확인<br/><br/>

      ```SQL
      SELECT
        select_list
      FROM
        table_name
      WHERE
        search_condition;
      ```
        - `FROM clause 뒤`에 위치
        - search_condition은 비교연산자 및 논리연산자(AND, OR, NOT 등)를 사용하는 구문이 사용됨<br/><br/>
      
      ```SQL
      SELECT
        lastName,
        firstName,
        officeCode,
        jobTitle
      FROM
        employees
      WHERE
        officeCode < 5
        OR jobTitle != 'Sales Rep';
      ```
        - 테이블 employees에서 officeCode 필드 값이 5미만이거나 jobTitle 필드 값이 'Sales Rep'이 아닌 데이터의 lastName, firstName, officeCode, jobTitle 조회<br/><br/>

      ```SQL
      SELECT
        lastName,
        firstName,
        officeCode
      FROM
        employees
      WHERE
        officeCode BETWEEN 1 AND 4;
      ```
        - 테이블 employees에서 officeCode 필드 값이 1에서 4 사이 값(1과 4를 포함)인 데이터의 lastName, firstName, officeCode 조회<br/><br/>
      
      ```SQL
      SELECT
        lastName,
        firstName,
        officeCode
      FROM
        employees
      WHERE
        officeCode IN (1, 3, 4);
      ```
        - 테이블 employees에서 officeCode 필드 값이 1 또는 3 또는 4 값인 데이터의 lastName, firstName, officeCode 조회<br/><br/>
      
      ```SQL
      SELECT
        lastName,
        firstName
      FROM
        employees
      WHERE
        lastName LIKE '%son';
      ```
        - 테이블 employees에서 lastName 필드 값이 son으로 끝나는 데이터의 lastName, firstName 조회<br/><br/>

      ```SQL
      SELECT
        lastName,
        firstName
      FROM
        employees
      WHERE
        firstName LIKE '___y';
      ```
        - 테이블 employees에서 firstName 필드 값이 4자리면서 y로 끝나는 데이터의 lastName, firstName 조회<br/><br/>

    - `LIMIT` clause : 조회하는 레코드 수를 제한<br/><br/>

      ```SQL
      SELECT
        select_list
      FROM
        table_name
      LIMIT [offset,] row_count;
      ```
        - LIMIT clause는 하나 또는 두개의 인자를 사용(0 또는 양의 정수)
        - row_count는 조회할 최대 레코드 수를 지정 지정<br/><br/>

      ```SQL
      SELECT
        contactFirstName, 
        creditLimit
      FROM
        customers
      ORDER BY
        creditLimit DESC
      LIMIT 3, 4;
      ```
        - 테이블 customers에서 contactFirstName, creditLimit필드 데이터를 creditLimt 기준 내림차순으로 4번째부터 7번째 데이터만 조회<br/><br/>

4. Groupint data
    - `GROUP BY` clause : 레코드를 그룹화하여 요약본 생성 with 집계 함수
      - Aggregation Functions : 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수  
      SUM, AVG, MAX, MIN, COUNT<br/><br/>

      ```SQL
      SELECT
        c1, c2,..., aggregate_function(ci)
      FROM
        table_name
      GROUP BY
        c1, c2,...;
      ```
        - `FROM 및 WHERE clause 뒤`에 위치
        - GROUP BY 절 뒤에 그룹화할 필드 목록을 작성<br/><br/>

      ```SQL
      SELECT
        country,
        AVG(creditLimit)
      FROM
        customers
      GROUP BY
        country
      ORDER BY
        AVG(creditLimit) DESC;
      ```
        - 테이블 customers에서 country 필드를 그룹화하여 각 그룹에 대한 creditLimit의 평균값을 내림차순 조회<br/><br/>

      ```SQL
      SELECT
        country,
        AVG(creditLimit)
      FROM
        customers
      GROUP BY
        country
      HAVING
        AVG(creditLimit) > 80000;
      ```
        - 테이블 customers에서 country 필드를 그룹화하여 각 그룹에 대한 creditLimit의 평균값이 80000을 초과하는 데이터만 조회<br/><br/>
