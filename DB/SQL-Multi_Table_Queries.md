# SQL - Multi Table Queries

## Joining tables
> `JOIN` clause : 둘 이상의 테이블에서 데이터를 검색하는 방법  

</br><br/>

### 1. `INNER JOIN` clause : 두 테이블에서 값이 일치하는 레코드에 대해서만 결과를 반환

<br/>

```SQL
  SELECT
    select_list
  FROM
    table1
  INNER JOIN table2
    ON table1.fk = table2.pk;
```
- FROM 절 이후 메인 테이블 지정 (table1)
- INNER JOIN 절 이후 메인 테이블과 조인할 테이블을 지정 (table2)
- ON 키워드 이후 조인 조건을 작성 (조인 조건은 table1과 table2 간의 레코드를 일치시키는 규칙을 지정) <br/><br/>

```SQL
  SELECT
    t1.orderNumber,
    t1.status,
    t2.priceEach
  FROM
    orders AS t1
  INNER JOIN orderdetails AS t2
    ON t1.orderNumber = t2.orderNumber;
```
- orders와 orderdetails 테이블에서 orderNumber 값이 같은 레코드의 ordeNumber, status, priceEach 필드를 조회 <br/><br/>

```SQL
  SELECT
    t1.orderNumber,
    SUM(quantityOrdered * priceEach) AS totalSales
  FROM
    orders AS t1
  INNER JOIN orderdetails AS t2
    ON t1.orderNumber = t2.orderNumber
  GROUP BY orderNumber;
```
- 직전 조회 결과를 바탕으로 각 주문번호 별 주문상태와 총 판매액을 요약(주문번호는 orderNumber필드, 총 판매액은 quantityOrdered와 priceEach필드의 곱셈 결과) <br/><br/>

</br><br/>

### 2. `LEFT JOIN` clause : 오른쪽 테이블의 일치하는 레코드와 함께 왼쪽 테이블의 모든 레코드 반환
- 왼쪽은 무조건 표시하고, 매치되는 레코드가 없으면 NULL을 표시  
- 왼쪽 테이블 한 개의 레코드에 여러 개의 오른쪽 테이블 레코드가 일치할 경우, 해당 왼쪽 레코드를 여러번 표시

<br/>

```SQL
  SELECT
    select_list
  FROM
    table1
  LEFT JOIN table2
    ON table1.fk = table2.pk;
```
- FROM 절 이후 왼쪽 테이블 지정 (table1)
- LEFT JOIN 절 이후 오른쪽 테이블과 조인할 테이블을 지정 (table2)
- ON 키워드 이후 조인 조건을 작성 (왼쪽 테이블의 각 레코드를 오른쪽 테이블의 모든 레코드와 일치시킴) <br/><br/>

```SQL
  SELECT
    contactFirstName,
    orderNumber,
    status
  FROM
    customers
  INNER JOIN orders
    ON orders.customerNumber = cutomers.customerNumber;
```
- customers와 orders 테이블의 customerNumber 필드가 일치하는 레코드와 함께 customers 테이블 contactFirstName와 orders 테이블의 orderNumber, status 필드 조회 (왼쪽 테이블은 customers, 오른쪽 테이블은 orders, 일치하지 않는 경우 NULL) <br/><br/>

```SQL
  SELECT
    contactFirstName,
    orderNumber,
    status
  FROM
    customers
  INNER JOIN orders
    ON orders.customerNumber = cutomers.customerNumber
  WHERE orders.orderNumber IS NULL;
```
- 직전 조회 결과를 바탕으로 주문내역이 없는 고객의 이름과 주문번호 및 배송상태 조회 (고객의 이름은 contactFirstName 필드, 주문번호는 orderNumber 필드, 배송상태는 status 필드) <br/><br/>

</br><br/>

### 3. `RIGHT JOIN` clause : 왼쪽 테이블의 일치하는 레코드와 함께 오른쪽 테이블의 모든 레코드 반환
- 오른쪽은 무조건 표시하고, 매치되는 레코드가 없으면 NULL을 표시  
- 오른쪽 테이블 한 개의 레코드에 여러 개의 왼쪽 테이블 레코드가 일치할 경우, 해당 오른쪽 레코드를 여러번 표시

<br/>

```SQL
  SELECT
    select_list
  FROM
    table1
  RIGHT JOIN table2
    ON table1.fk = table2.pk;
```
- FROM 절 이후 왼쪽 테이블 지정 (table1)
- RIGHT JOIN 절 이후 오른쪽 테이블 지정 (table2)
- ON 키워드 이후 조인 조건을 작성 (오른쪽 테이블의 각 레코드를 왼쪽 테이블의 모든 레코드와 일치시킴) <br/><br/>

```SQL
  SELECT
    employeeNumber,
    firstName,
    customerNumber,
    contactFirstName
  FROM
    customers
  INNER JOIN employees
    ON salesRepEmployeeNumber = employeeNumber;
```
- employeeNumber 필드와 salesRepEmployeeNumber 필드가 일치하는 레코드와 함께 employeeNumber, firstName, customerNumber, contactFristName 필드 조회 (왼쪽 테이블은 customers, 오른쪽 테이블은 employees, 일치하지 않는 경우 NULL) <br/><br/>

```SQL
  SELECT
    employeeNumber,
    firstName,
    customerNumber,
    contactFirstName
  FROM
    customers
  INNER JOIN employees
    ON salesRepEmployeeNumber = employeeNumber
  WHERE salesRepEmployeeNumber IS NULL;
```
- 직전 조회 결과를 바탕으로 고객에게 판매한 내역이 없는 지원 몰골 조회 (직원 번호와 이름은 employeeNumber, firstName 필드이며, 고객 번호와 이름은 customerNumber, contactFirstName 필드) <br/><br/>

</br><br/>

### 4. JOIN 정리
```SQL
  SELECT
    *
  FROM
    tableA
  INNER JOIN tableB
    ON tableA.fk = tableB.id;
```

<br/>

```SQL
  SELECT
    *
  FROM
    tableA
  LEFT JOIN tableB
    ON tableA.fk = tableB.id;
```

<br/>

```SQL
  SELECT
    *
  FROM
    tableA
  RIGHT JOIN tableB
    ON tableA.fk = tableB.id;
```

<br/>

```SQL
  SELECT
    *
  FROM
    tableA
  LEFT JOIN tableB
    ON tableA.fk = tableB.id
  WHERE tableB.id IS NULL;
```

<br/>

```SQL
  SELECT
    *
  FROM
    tableA
  RIGHT JOIN tableB
    ON tableA.fk = tableB.id
  WHERE tableB.id IS NULL;
```

<br/>

```SQL
  SELECT * FROM tableA
  LEFT JOIN tableB ON tableA.fk = tableB.id
  UNION
  SELECT * FROM tableA
  RIGHT JOIN tableB ON tableA.fk = tableB.id
```