SQL DataBase

## DataBase SQL : JOIN 예시 테이블 생성

DataBase SQL 예시 Table

- Database, JOIN 예시 Table 생성

---

#### Database, Table 생성

```SQL
USE sqldb;
```



**학생 테이블**

```SQL
CREATE TABLE stdTBL (
	stdName	VARCHAR(10) PRIMARY KEY,
    stdAddr	VARCHAR(10) NOT NULL
);
```



**동아리방 테이블**

```SQL
CREATE TABLE clubTBL (
	clubName VARCHAR(10) PRIMARY KEY,
    clubRoom VARCHAR(4) NOT NULL
);
```



**학생 동아리 테이블**

``` SQL
CREATE TABLE stdclubTBL (
	num		INT AUTO_INCREMENT PRIMARY KEY,
    stdName VARCHAR(10) NOT NULL,
    clubName VARCHAR(10) NOT NULL,
    FOREIGN KEY(stdName) REFERENCES stdTBL(stdName),
    FOREIGN KEY(clubName) REFERENCES clubTBL(clubName)
);
```



**데이터 입력**

```SQL
INSERT INTO stdTBL VALUES('김범수','경남'); 
INSERT INTO stdTBL VALUES('성시경','서울'); 
INSERT INTO stdTBL VALUES('조용필','경기'); 
INSERT INTO stdTBL VALUES('은지원','경북'); 
INSERT INTO stdTBL VALUES('바비킴','서울'); 
```

```SQL
INSERT INTO clubTBL VALUES('수영','101호');
INSERT INTO clubTBL VALUES('바둑','102호');
INSERT INTO clubTBL VALUES('축구','103호');
INSERT INTO clubTBL VALUES('봉사','104호');
```

```SQL
INSERT INTO stdclubTBL VALUES(NULL, '김범수','바둑');
INSERT INTO stdclubTBL VALUES(NULL, '김범수','축구');
INSERT INTO stdclubTBL VALUES(NULL, '조용필','축구');
INSERT INTO stdclubTBL VALUES(NULL, '은지원','축구');
INSERT INTO stdclubTBL VALUES(NULL, '은지원','봉사');
INSERT INTO stdclubTBL VALUES(NULL, '바비킴','봉사');
```

**데이터 확인**

```SQL
SELECT * FROM stdTBL;
SELECT * FROM clubTBL;
SELECT * FROM stdclubTBL;
```







