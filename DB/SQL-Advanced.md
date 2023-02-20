# SQL - Advanced

## 1. Transactions
> (다 성공하던지 혹은 다 실패하던지 해야하는) `여러 쿼리문을 묶어서 하나의 작업처럼` 처리하는 방법
- 쪼개질 수 없는 업무처리의 단위
- 전체가 수행되거나 또는 전혀 수행되지 않아야 함(All or Nothing)

<br/>

```SQL
  START TRANSACTION;
  state_ments;
  ...
  [ROLLBACK|COMMIT];
```
- START TRANSACTION : 트랜잭션 구문의 시작을 알림
- COMMIT : 모든 작업이 정상적으로 완료되면 한꺼번에 DB에 반영
- ROLLBACK : 부분적으로 작업이 실패하면 트랜잭션에서 진행한 모든 연산을 취소하고 트랜잭션 실행 전으로 되돌림 <br/><br/>

<br/><br/>

## 2. Triggers
> 특정 이벤트에 대한 응담으로 자동으로 실행되는 것 `(INSERT, UPDATE, DELETE)`  
> 트리거는 DML의 영향을 받는 필드 값에만 적용할 수 있음
- 트리거 목록 확인 : SHOW TRIGGERS; 
- 트리거 삭제 : DROP TRIGGER trigger_name;
- 트리거에서 특정 시점 전/후의 값에 접근 할 수 있도록 제공하는 키워드 -> OLD, NEW
- INSERT -> NEW
- UPDATE -> OLD, NEW
- DELETE -> OLD

<br/>

```SQL
  CREAT TRIGGER trigger_name
  {BEFORE | AFTER} {INSERT | UPDATE | DELETE}
  ON table_name FOR EACH ROW
  trigger_body;
```
- CREAT TRIGGER 키워드 다음에 생성하려는 트리거의 이름을 지정
- 각 레코드의 어느 시점에 트리거가 실행될지 지정 (삽입, 수정, 삭제 전/후)
- ON 키워드 뒤에 트리거가 속한 테이블의 이름을 지정
- 트리거가 활성화될 때 실행할 코드를 trigger_body에 지정
  - 여러 명령문을 실행하려면 BEGIN END 키워드로 묶어서 사용 <br/><br/>

```SQL
  DELIMITER //
  CREAT TRIGGER beforeArticleUpdate
    BEFORE UPDATE
    ON articles FOR EACH ROW
  BEGIN
    SET NEW.updatedAt = CURRENT_TIME();
  END//
  DELIMITER ;
```
- 트리거를 사용해 기존 게시글이 수정되면, 게시글의 수정일자 필드 값을 최신 일자로 업데이트 하기 
- `DELIMITER //`
  -  SQL의 구문 문자(;)를 변경
  - BIGIN - END 구문 사이에 여러 SQL문이 작성되기 때문에 하나의 트리거로써 작동될 수 있도록 사용
- `BIGIN - END`
  - 하나 이상의 구문 목록을 표현
  - BIGIN과 END 키워드로 둘러싸는 다중 구문을 구성하게 됨
- SET `NEW.`updatedAT
  - 트리거에서 특정 시점 전/후의 값에 접근 할 수 있도록 제공하는 키워드 -> OLD, NEW <br/><br/>

```SQL
  DELIMITER //
  CREAT TRIGGER recordLogs
    AFTER INSERT
    ON articles FOR EACH ROW
  BEGIN
    INSERT INTO articleLogs (description, createdAt)
    VALUES (CONCAT(NEW.id, '번 글이 작성되었습니다.'), CURRENT_TIME());
  END//
  DELIMITER ;
```
- 트리거를 사용해 기존 게시글이 작성되면, 별도의 테이블에 몇 번 게시글이 작성되었다는 것을 기록하기 <br/><br/>

```SQL
  DELIMITER //
  CREAT TRIGGER backupLogs
    AFTER DELETE
    ON articles FOR EACH ROW
  BEGIN
    INSERT INTO backupArticles (title, createdAt, updatedAt)
    VALUES (OLD.title, OLD.createdAt, OLD.updatedAt);
  END//
  DELIMITER ;
```
- 트리거를 사용해 기존 게시글이 삭제되면, 삭제된 게시글의 구조 그대로 별도의 테이블에 기록하기 <br/><br/>
