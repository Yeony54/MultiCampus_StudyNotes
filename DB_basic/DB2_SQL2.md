SQL DataBase

## DataBase SQL

DataBase MySQL을 사용해 동작해 보았던 것들을 기록한다.

- View
- DROP : database Backup, Restore 방법
- SHOW, USE
- Data Modeling
- PK, FK
- Data Type
- AS : alias



SQL의 대소문자 : 

SQL은 대문자, 소문자를 구분하지 않는다.

일반적으로 keyword(이미 정해져 있는글자)는 대문자로 표기하는게 관용적이다.

식별자(변수명, 함수명, 테이블명, 인덱스명, view명)은 관용적으로 소문자를 이용한다.



---



#### SQL : View

**View**는 Database안에 존재하는 객체로, 가상의 Table을 만들어준다.

View는 실제 데이터를 가지고 있지 않지만, 사용자 측면에서 table과 동일하게 사용할 수 있다.

View를 사용하는 이유는 **보안**과 **편리**가 있다.



**보안**

일반적으로 테이블 안에는 개인정보와 같은 중요한 정보가 들어있다. 

데이터 베이스 관리자 (DBA)는 View를 만들어 다른사람(개발자, 일반사용자)에게 제공한다.

**편리**

복잡한 SQL 구문을 View로 단순화 시켜 제공할 수 있다.



```SQL
CREATE VIEW shopdb.v_memberTBL
AS SELECT memberName, memberAddr FROM shopdb.membertbl;
```

이전에 만들었던 shopdb의 membertbl에서 컬럼을 선택하여 view를 만들었다.



```SQL
SELECT * FROM shopdb.v_memberTBL;
```

select구문을 사용하여 view를 확인해 본다.





---



#### SQL : DROP - database Backup, Restore



데이터를 백업하는것은 중요한일이다.

MySQL에서 데이터 백업, DROP 후 Restore 하는 방법이다.



MySQL 의 왼쪽 Navigator 창에서 Administration > Data Export에서 백업을 할 수 있다.

이후 shopdb를 DROP을 통해 삭제를 해 보고 다시 백업한 데이터를 불러와 보자

```sql
DROP DATABASE shopdb;
```

MySQL 의 왼쪽 Navigator 창에서 Administration > Data Import 를 통해 아까 백업한 데이터를 다시 불러들일 수 있다.



**<DROP 오류 방지>**

존재하지 않는 database를 없애려하는 경우에는 오류가 발생한다.

그래서 보통 database를 삭제할때 `IF EXIST`구문을 사용하여 오류를 방지한다.

```SQL
DROP DATABASE IF EXISTS sqldb;
```





---



#### SQL : SHOW, USE

##### **SHOW** 에 대한 설명

SHOW 는 현재 목록을 보여줄 때 사용한다.

```SQL
SHOW DATABASE;
```

SHOW 구문을 통해 현재 사용가능한 모든 DataBase(Schema)를 출력할 수 있다.

```sql
USE employees;
```

USE 구문을 통해 DataBase(Schema)를 선택한다.

```sql
SHOW TABLES;
```

SHOW 구문을 통해 현재 선택된 DataBase내의 Table을 조회한다.

```sql
DESC employees;
```

DESC는 DESCRIBE의 약자로 둘다 사용할 수 있다.

선택된 DataBase안의 employees라는 table의 명세를 조회한다.



##### USE 에 대한 추가 설명

테이블을 사용할 때에는 데이터베이스(schama) 명을 표시해 주어야 한다.

```sql
SELECT * FROM shopdb.v_memberTBL;
```

이런식으로 테이블 명 앞에 shopdb 라는 스키마를 표시 해 주었다.

USE를 통해 내가 사용할 데이터베이스(schema)를 지정해 준다면, 데이터베이스(schema)명을 생략하고 작성할 수 있게 된다.

```sql
USE shopdb;
SELECT * FROM v_memberTBL;
```

이렇게 USE 구문을 사용하거나, Navigator창의 Schemas > 데이터베이스를 더블클릭해서 사용할 수 있다.

데이터베이스(schema)가 선택되면 데이터베이스(schema)명이 bold체가 되니 알아두자.



---



#### SQL : Data Modeling

**데이터 모델링**이란  현실의 데이터를 DBMS의 Database내로 옮기기 위한 과정이다.



1. Null과 데이터가 뒤죽박죽 섞여있는 원본 데이터
2. 데이터를 기준으로 Null 이 있는값과 없는 값을 분리
   - Null값이 한곳에 모여있어 L자 처럼 보이는 데이터를 `L자형 테이블`이라고 부른다.
   - L자형 테이블은 보는것과 같이 공간낭비라는 문제점을 가지고 있다.
3. L자형 테이블을 기준으로 Table을 분리한다.
   - 공간낭비를 해결할 수 있다.
   - 중복이 되는 컬럼과, 분리되어 정보가 떨어져버리는 문제가 생긴다.
4. 두개의 테이블 각각 데이터의 중복을 제거, 정보 추가
   - 이를 통해 두개의 Table이 업무적으로 연관성을 맺게 된다.
   - 연관성을 갖는것을 Relation(관계)를 가진다 라고 말한다.



---



#### SQL : PK, FK

Relation을 말할 때에는 Key 가 필요하다.

Key의 종류에는 PK(Primary Key)와 FK(Forien Key)가 있다.



**Primary Key (고유키)** : 각각의 record를 유일하게 식별하는 컬럼의 집합

전화번호, 이메일 등 각자 고유의 정보를 Primary Key로 지정할 수 있다.

이름 같은 경우는 중복되는 이름이 있을 수 있어 Primary Key로 지정할 수 없다.

이름+전화번호 등 `복합키`로 고유의 정보를 만들어 Primary Key로 지정할 수 있다.

- NOT NULL 제약조건
- UNIQUE 제약조건

Primary Key는 비어있지 않아야 하고(NOT NULL) 각자 고유(Unique)한 값이어야 한다.

<i>- 테이블마다 반드시 PK가 존재해야 하는것은 아니다</i>

<i>- PK를 설정한 column에서 Index가 설정되어 정렬된다.</i>



**Forien Key (외래키)** : 하나의 table의 column이 다른 table의 PK를 가르킬 때 이 컬럼을 Forien Key 라고 한다.

- NOT NULL 제약조건
- FK 안의 값은 반드시 PK안에 존재해야 한다
- UNIQUE 제약조건은 없다.

다른 table의 PK를 가리키기 때문에 NOT NULL 이어야하며, FK의 값이 PK에 반드시 존재하여야 한다.

PK와 달리 FK는 FK의 테이블 안에서 UNIQUE 제약조건을 갖지 않고 중복된 값을 가질 수 있다.

이렇게 PK와 FK의 관계가 성립되었을 때 Relation을 갖는다 라고한다.

PK와 FK의 관계는 1:N 의 관계이다.

<i>- PK를 가리키기 때문에 PK와 Data Type도 같게 설정해 주어야 한다.</i>

<i>- FK에 PK의 값이 있을 때, PK를 삭제하지 못한다.</i>



---



#### SQL : Data Type

SQL의 기본적인 Data Type에 대해 설명한다.



- INT 
  - 정수형 타입의 데이터
  - -21억 ~ +21억 범위의 데이터를 저장할 수 있다.
  - SHORTINT(128) BIGINT(더큰거)도 존재한다.
- VARCHAR(variable character)
  - 가변 문자열
  - VARCHAR(10)을 설정 하면 최대 10글자 까지 저장할 수 있다.
  - 만약 5글자만 저장하면 사용되는 공간이 5글자로 줄어든다
  - 저장되는 공간을 효율적으로 사용이 가능하다
- CHAR
  - CHAR(10) 을 설정하면 최대 10글자 까지 저장할 수 있다.
  - 만약 5글자를 저장하더라도 10글자의 공간을 할당한다.
  - VARCHAR 보다 연산이 빠르다는 장점이 있다.
- DATE
  - 날짜타입(연월일)
- DATETIME
  - 날짜타입(연월일시분초)



---



#### SQL : AS - alias

SELECT를 할 때 컬럼명을 바꾸어 사용할 수 있다.

```SQL
SELECT emp_no AS '사번', 
	   first_name AS '이름', 
       hire_date AS '입사일'
FROM employees LIMIT 5;
```

alias (AS) 를 사용하여 컬럼명을 바꾸거나 줄여서 사용할 수 있다.



---



이어서 실습을 하며 SQL에 대해 알아본다.