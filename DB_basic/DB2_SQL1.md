SQL DataBase

## DataBase SQL

DataBase 실습을 위해 MySQL을 설치하고 동작해 보았던 것들을 기록한다.

- SQL 분류 
  - DML, DDL, DCL
- SQL 간단 설명
- 색인 설명



---



#### SQL이란?

**SQL(Structured Query Language)** 는 구조적 질의 언어이다.

(관계형)데이터베이스에서 사용하는 프로그래밍 언어 **표준**으로 한번 익혀놓으면 다른 관계형 데이터베이스에서도 사용이 가능하다.

하지만 SQL언어를 사용하는 프로그램에 따라 기능이 다른것들도 있기 때문에 유의해야 한다.



##### SQL의 3가지 분류

SQL은 3가지로 분류할 수 있다.

- DML (Data Manipulation Language) - 데이터 조작언어
- DDL (Data Definition Language) - 데이터 정의언어
- DCL (Data Control Language) - 데이터 제어 언어



그 중에서 DML을 가장 많이 사용한다.

DML의 명령어에는 INSERT, DELETE, UPDATE, SELECT가 존재한다.



<i>이는 CRUD 작업에 해당하는 것들이다.</i>

<i>CRUD는 데이터에서 처리하는 4가지 작업으로 (Create, Read, Update, Delete)로 구분된다.</i>



----



**과정 설명**

1. DataBase에는 실습용 employees 파일이 download되어져 있다.

2. shopdb라는 schema를 새로 생성하여 그 안에 memberTBL, productTBL table을 생성한다.
3. SQL 실습



---





#### 실습 Table 요소 설명

<member TBL 테이블 설명>

| 열 이름(한글) | 영문 이름  | 데이터 형식 | 길이         | NULL허용 |
| ------------- | ---------- | ----------- | ------------ | -------- |
| 아이디        | memberID   | 문자(CHAR)  | 8글자(영문)  | X        |
| 회원 이름     | memberName | 문자(CHAR)  | 5글자(한글)  | X        |
| 주소          | memberAddr | 문자(CHAR)  | 20글자(한글) | O        |

<product TBL 테이블 설명>

| 열 이름(한글) | 영문 이름   | 데이터 형식 | 길이        | NULL허용 |
| ------------- | ----------- | ----------- | ----------- | -------- |
| 제품이름      | productName | 문자(CHAR)  | 4글자(한글) | X        |
| 가격          | cost        | 숫자(INT)   | 정수        | X        |
| 제조일자      | makeDate    | 날짜(DATE)  | 날짜형      | O        |
| 제조회사      | company     | 문자(CHAR)  | 5글자(한글) | O        |
| 남은 수량     | amount      | 숫자(INT)   | 정수        | X        |



#### SQL 실습 코드



```sql
SELECT * FROM shopdb.membertbl;
SELECT memberName FROM shopdb.membertbl;
```

Select는 `SELECT 컬럼명 FROM 테이블명;`으로 작성할 수 있다.

`*`는 모든 컬럼(ALL) 을 지칭한다. 테이블의 모든 컬럼을 조회한다는 뜻이 된다.

아래의 구문은 shopdb의 membertbl 테이블의 memberName컬럼을 조회한다는 뜻이다.



**memberTBL에 데이터 삽입**

```SQL
INSERT INTO shopdb.membertbl VALUES('hong', '홍길동', '서울');
INSERT INTO shopdb.membertbl VALUES('iu', '아이유', '서울');
INSERT INTO shopdb.membertbl VALUES('shin', '신사임당', '인천');
INSERT INTO shopdb.membertbl VALUES('kim', '김연아', '광주');
```

데이터 삽입은 `INSERT INTO 테이블명 VALUES(데이터)`으로 작성할 수 있다.



**productTBL에 데이터 삽입**

```sql
INSERT INTO shopdb.producttbl VALUES('컴퓨터', 1000, '2022-01-01', '삼성', 5);
INSERT INTO shopdb.producttbl VALUES('세탁기', 2000, '2022-01-02', 'LG', 2);
INSERT INTO shopdb.producttbl VALUES('냉장고', 1500, '2022-01-03', '대우', 3);
```



**삽입된 데이터 확인**

```sql
SELECT * FROM shopdb.membertbl;
SELECT memberName, memberAddr FROM shopdb.membertbl;
SELECT memberName, memberAddr FROM shopdb.membertbl WHERE memberName = '아이유';
```

다시 SELECT를 통해 삽입된 데이터들을 확인할 수 있다.

WHERE 절을 통해 원하는 조건의 데이터를 조회 가능하다.



---



**test data를 삽입해보자**

```sql
SELECT first_name, last_name, hire_date
FROM employees.employees LIMIT 500;
```

기존에 만든 TBL의 형식에 따라서 first_name, last_name, hire_date만을 추출하려한다.

```sql
INSERT INTO shopdb.indexTBL
SELECT first_name, last_name, hire_date
FROM employees.employees LIMIT 500;
```

MySQL은 설정에 `"Limit to 1000 rows"`라고 되어있는 경우가 있다. 이것을 `"Dont Limit"`으로 바꿔줄 수도 있고, 위의 코드처럼 LIMIT을 정해줄 수도 있다.



**삽입된 코드 확인**

```SQL
SELECT * FROM shopdb.indexTBL;
```

SELECT구문으로 잘 삽입이 되었는지 확인해 본다.





---



#### Database의 Index(색인)



이전에서 만들어진 indexTBL에서 'Mary' 라는 이름을 조회해 보자.

```sql
SELECT * FROM shopdb.indexTBL WHERE first_name = 'Mary';
```

SELECT를 통해 Mary를 조회할 수 있다, 하지만 Full table scan을 사용해 처음부터 Mary를 검색하기 때문에 효율이 떨어진다.



그래서  색인을 사용하는 것이다.

indexTBL의 first_name에 index를 설정해보자.

```sql
CREATE INDEX idx_indextbl_firstname on shopdb.indexTBL(first_name);
SELECT * FROM shopdb.indexTBL WHERE first_name = 'Mary';
```

CREATE 구문을 통해 INDEX를 만들어준다.

그리고 Mary를 조회하게 되면, 이전에서와 달리 속도가 5배 정도 빠른것을 알 수 있다.





**색인**이란 검색을 빠르게 하기 위해서 사용한다.

Index의 종류에는 **clustered Index**와 **secondary Index** 가 있는데 색인을 생성할 때에는 secondary Index 방법이 사용된다.

**Secondary Index**방식은 column 안에 있는 값을 사용해 Index를 설정하고 B-Tree구조의 형태로 데이터를 분배시켜서 저장하는 Index를 따로 생성한다.

B-Tree는 빠르게 찾는데 최적화 되어있지만, Index의 내용이 변경(추가, 삭제, 변경)될 경우 B-Tree를 다시 생성해야하면서 Overhead가 발생하게 된다.

그래서 Index가 빠르게 찾을 수 있다고 무조건적으로 좋은것이 아니고, 전체적인 performance를 따져 index를 꼭 사용해야하는 곳에만 만드는 것이 중요하다.



