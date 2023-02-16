# SQL - Nested Queries

## 1. Subquery
> `A query inside a query` : 단일 쿼리문에 여러 테이블의 데이터를 결합하는 방법
- 조건에 따라 하나 이상의 테이블에서 데이터를 검색하는데 사용
- SELECT, FROM, WHERE, HAVING 절 등에서 다양한 맥락에서 사용

<br/>

```SQL
  SELECT customerNumber, amount
  FROM payments
  WHERE amount = (
    SELECT MAX(amount)
    FROM payments
  );
```
- 한번에 가장 많은 돈을 소비한 고객번호 조회 (payments 테이블 활용) <br/><br/>

```SQL
  SELECT lastName, firstName
  FROM employees
  WHERE officeCode IN (
    SELECT officeCode
    FROM offices
    WHERE country = 'USA'
  );
```
- 미국에 있는 사무실에서 근무하는 직원의 성과 이름 조회 (직원 정보는 employees, 사무실 정보는 offices 테이블에 존재) <br/><br/>

```SQL
  SELECT customerNumber, amount, contactFirstName
  FROM
    (
      SELECT contactFirstName, amount, payments.customerNumber
      FROM payments
      INNER JOIN customers USING (customerNumber)
    ) AS findName -> (*별칭*)
  WHERE
    amount = (SELECT MAX(amount) FROM payments);
  ;
```
- 소비를 한 고객들 중 한번에 지불한 금액이 가장 높은 고객의 customerNumber, amount, contactFirstName을 조회 (고객 테이블은 customers, 지불 테이블은 payments를 활용) 
- `FROM 절에서 사용하는 subquery는 별도의 파생된(derived) 테이블로 간주되기 때문에 MYSQL에서는 반드시 별칭 지정 필요` <br/><br/>

</br>

> `EXISTS` operator : 쿼리 문에서 반환된 레코드의 존재 여부를 확인

<br/>

```SQL
  SELECT
    select_list
  FROM
    table
  WHERE 
    [NOT] EXISTS (subquery);
```
- subquery가 하나 이상의 행을 반환하면 EXISTS 연산자는 true를 반환하고 그렇지 않으면 false를 반환
- 주로 WHERE 절에서 subquery의 반환 값 존재 여부를 확인하는데 사용 <br/><br/>

```SQL
  SELECT 
    employeenumber, lastName, firstName
  FROM
    employees
  WHERE
    EXISTS (
      SELECT *
      FROM offices
      WHERE city = 'Paris' AND offices.officeCode = employees.officeCode
  );
```
- Paris에 있는 사무실에서 근무하는 모든 직원의 번호, 이름, 성을 조회 (직원 테이블은 employees, 사무실 테이블은 offices이며 두 테이블의 officeCode 필드를 기준으로 비교) <br/><br/>

```SQL
  SELECT customerNumber, amount, contactFirstName
  FROM
    (
      SELECT contactFirstName, amount, payments.customerNumber
      FROM payments
      INNER JOIN customers USING (customerNumber)
    ) AS findName -> (*별칭*)
  WHERE
    amount = (SELECT MAX(amount) FROM payments);
  ;
```
- 소비를 한 고객들 중 한번에 지불한 금액이 가장 높은 고객의 customerNumber, amount, contactFirstName을 조회 (고객 테이블은 customers, 지불 테이블은 payments를 활용) 
- `FROM 절에서 사용하는 subquery는 별도의 파생된(derived) 테이블로 간주되기 때문에 MYSQL에서는 반드시 별칭 지정 필요` <br/><br/>

</br><br/>


## 2. Conditional Statements
> `CASE` statement : SQL 문에서 조건문을 구성

<br/>

```SQL
  CASE case_value
    WHEN when_value1 THEN statements,
    WHEN when_value2 THEN statements
    ...
    [ELSE else_statements]
  END CASE;
```
- case_value가 when_value와 동일한 것을 찾을 때까지 순차적으로 비교
- when_value와 동일한 case_value를 찾으면 해당 THEN 절의 코드를 실행
- 동일한 값을 찾지 못하면 ELSE 절의 코드를 실행 (ELSE절이 없을 때 동일한 값을 찾지 못하면 오류 발생) <br/><br/>

```SQL
  SELECT 
    orderNumber, status,
    CASE
      WHEN status = 'InProcess' THEN '주문중'
      WHEN status = 'Shipped' THEN '주완료'
      WHEN status = 'Cancellde' THEN '주문취소'
      ELSE '기타사유'
    END AS details
  FROM orders;
```
- order 테이블의 status에 따라 상세 정보를 매겨 조회 ('In Process'는 '주문중', 'Shipped'는 '발주완료', 'Cancellde'는 '주문취소' 그 외는 '기타사유'로 지정) <br/><br/>