SQL DataBase

## DataBase SQL 실습

DataBase SQL 실습

- Database, Table 생성



---

#### Database, Table 생성



**데이터베이스 생성**

```sql
-- 데이터베이스(Schema)가 존재하면 DROP
DROP DATABASE IF EXISTS sqldb;

-- 데이터베이스(Schema)를 생성
CREATE DATABASE sqldb;

-- sqldb를 사용할 database로 지정
USE sqldb;
```

데이터베이스를 생성하고, 사용할 데이터베이스로 지정해 준다.



**회원 테이블 생성**

```sql
-- 회원테이블
CREATE TABLE userTBL (
    userID      CHAR(8) PRIMARY KEY,    -- 사용자 ID (PK)
    userName    VARCHAR(10) NOT NULL,   -- 사용자 이름
    birthYear   INT NOT NULL,           -- 출생년도
    userAddr    CHAR(2) NOT NULL,       -- 지역(2글자 짜리 지역명)
    mobile1     CHAR(3),                -- 휴대폰 앞자리(3글자)
    movile2     CHAR(8),                -- 휴대폰 뒷자리(8글자)
    userHeight  SMALLINT,               -- 키/SMALLINT 128까지의 작은범위 정수
    userDate    DATE                    -- 회원가입일
);
```

회원 테이블을 생성한다.



**구매 테이블 생성**

```sql
CREATE TABLE buyTBL (
    num            INT AUTO_INCREMENT PRIMARY KEY,    -- 순번(PK)
    userID         CHAR(8) NOT NULL,                  -- 사용자ID(FK)
    productName    CHAR(6) NOT NULL,                  -- 제품명
    productGroup   CHAR(4),                           -- 제품 분류
    productPrice   INT NOT NULL,                      -- 제품 가격
    buyAmount      INT NOT NULL,                      -- 구매 수량
    FOREIGN KEY(userID) REFERENCES userTBL(userID)
);
```

구매 테이블을 생성해 준다.

num을 생성한 AUTO_INCREMENT 라는 명령어는 자동으로 1씩 증가시켜주는 것으로, 데이터를 입력할 때마다 자동적으로 번호가 생성되게 한다.

FK가 될 userID는 userTBL의 PK와 동일한 DataType 조건으로 생성해 준다.



**데이터 입력**

```sql
-- usertbl 데이터 입력
INSERT INTO usertbl VALUES('LSG', '이승기', 1987, '서울', '011', '1111111', 182, '2008-8-8');
INSERT INTO usertbl VALUES('KBS', '김범수', 1979, '경남', '011', '2222222', 173, '2012-4-4');
INSERT INTO usertbl VALUES('KKH', '김경호', 1971, '전남', '019', '3333333', 177, '2007-7-7');
INSERT INTO usertbl VALUES('JYP', '조용필', 1950, '경기', '011', '4444444', 166, '2009-4-4');
INSERT INTO usertbl VALUES('SSK', '성시경', 1979, '서울', NULL, NULL, 186, '2013-12-12');
INSERT INTO usertbl VALUES('LJB', '임재범', 1963, '서울', '016', '6666666', 182, '2009-9-9');
INSERT INTO usertbl VALUES('YJS', '윤종신', 1969, '경남', NULL, NULL, 170, '2005-5-5');
INSERT INTO usertbl VALUES('EJW', '은지원', 1972, '경북', '011', '8888888', 174, '2014-3-3');
INSERT INTO usertbl VALUES('JKW', '조관우', 1965, '경기', '018', '9999999', 172, '2010-10-10');
INSERT INTO usertbl VALUES('BBK', '바비킴', 1973, '서울', '010', '0000000', 176, '2013-5-5');

-- buytbl 데이터 입력
INSERT INTO buytbl VALUES(NULL, 'KBS', '운동화', NULL , 30, 2);
INSERT INTO buytbl VALUES(NULL, 'KBS', '노트북', '전자', 1000, 1);
INSERT INTO buytbl VALUES(NULL, 'JYP', '모니터', '전자', 200, 1);
INSERT INTO buytbl VALUES(NULL, 'BBK', '모니터', '전자', 200, 5);
INSERT INTO buytbl VALUES(NULL, 'KBS', '청바지', '의류', 50, 3);
INSERT INTO buytbl VALUES(NULL, 'BBK', '메모리', '전자', 80, 10);
INSERT INTO buytbl VALUES(NULL, 'SSK', '책', '서적', 15, 5);
INSERT INTO buytbl VALUES(NULL, 'EJW', '책', '서적', 15, 2);
INSERT INTO buytbl VALUES(NULL, 'EJW', '청바지', '의류', 50, 1);
INSERT INTO buytbl VALUES(NULL, 'BBK', '운동화', NULL , 30, 2);
INSERT INTO buytbl VALUES(NULL, 'EJW', '책', '서적', 15, 1);
INSERT INTO buytbl VALUES(NULL, 'BBK', '운동화', NULL, 30, 2);
```

데이터를 입력해 준다.

이때 buyTBL의 num 컬럼은 AUTO_INCREMENT 로 자동 생성되도록 했으니 NULL을 입력해 주면 된다.



**데이터 입력 확인**

```sql
SELECT * FROM userTBL;
SELECT * FROM buyTBL;
```

데이터가 잘 입력되었는지 확인 해 준다.





---





