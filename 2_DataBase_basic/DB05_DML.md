SQL DataBase

## DataBase SQL : DML

앞서 DML중 하나인 SELECT에 대해서 알아보았다.

나머지 DML에 대해서 설명한다.

- INSERT
- UPDATE
- DELETE

---



#### SQL : DML - INSERT



##### INSERT : 기본

database 초기 설정

```sql
USE sqldb;

CREATE TABLE testTBL (
    id 			INT,
    userName 	VARCHAR(10),
    userAge 	INT
);
```

```sql
INSERT INTO testTBL VALUES(1,'아이유',20);
```

가장 기본적인 INSERT 형식

```SQL
-- 필요한 것만 선택해서 INSERT
INSERT INTO testTBL(id, userName) VALUES(2,'김연아');
-- 컬럼의 순서를 바꾸어도 상관 없어요
INSERT INTO testTBL(userAge, userName) VALUES(30,'신사임당');
```

INSERT는 이렇게 필요한것만 넣을 수 있고, 컬럼의 순서가 바뀌어도 가능하다.



##### INSERT : AUTO_INCREMENT

database 초기 설정

```sql
DROP TABLE testTBL;

CREATE TABLE testTBL (
    id 			INT AUTO_INCREMENT PRIMARY KEY,
    userName 	VARCHAR(10),
    userAge 	INT
);
```

위의 TABLE의 id 는 AUTO_INCREMENT를 가지고 있다.

```SQL
INSERT INTO testTBL VALUES(NULL,'아이유',20);
INSERT INTO testTBL VALUES(NULL,'김연아',30);
```

AUTO_INCREMENT를 사용할 경우에는 자동으로 그 값이 정해지기 때문에 해당 값을 NULL로 해서 추가해 주어야 한다.



##### INSERT : TABLE을 데이터로 추가

database 초기 설정

```sql
DROP TABLE testTBL;

CREATE TABLE testTBL (
    id		INT,
    fname	VARCHAR(50),
    lname	VARCHAR(50)
);
```

```SQL
INSERT INTO testTBL
	SELECT emp_no, first_name, last_name
    FROM   employees.employees;
```

테이블의 컬럼을 매치시켜 테이블 자체를 INSERT 할 수 있다. 



---



#### SQL : DML - UPDATE



```SQL
UPDATE testTBL 
SET lname = '홍길동'
WHERE fname = 'Parto';
```

UPDATE와 SET을 WHERE로 해당되는 곳의 lname을 바꾸어주었다.



---



#### SQL : DML - UPDATE



```SQL
DELETE
FROM testTBL
WHERE lname = '홍길동';
```

WHERE에 해당하는 row를  DELETE해 주었다.



---

