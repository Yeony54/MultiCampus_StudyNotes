SQL DataBase

## DataBase SQL : JOIN

MySQL DBMS는 관계형 데이터 베이스이다.

Database는 중복과 공간의 낭비를 피하고 데이터의 무결성을 위해서 여러개의 테이블에 데이터를 나누어서 저장한다.

분리된 테이블은 서로 Relation을 가지고 있다.

두개의 테이블을 묶어서 하나의 결과 집합(Result Set)을 만들어 내는 방법을 알아보자



- JOIN 예시 테이블 생성

- INNER JOIN
- OUTER JOIN
- UNION



---



#### SQL : INNER JOIN

JOIN은 크게 INNER JOIN, OUTER JOIN으로 나뉜다.

보통 INNER JOIN을 많이 사용한다.



**INNER JOIN 형식**

- SELECT <열 목록>
  FROM <첫번째 테이블>
  	INNER JOIN <두번째 테이블>
      ON <조인 조건>
  WHERE <검색 조건>
  GROUP BY
  HAVING
  ORDER BY



이전에 만들어진 Database를 사용해 JOIN 예시를 보자

sqldb에 만들어진 userTBL과 buyTBL을 결합시켜보자.

```SQL
USE sqldb; -- 사용할 db 설정
```

```sql
SELECT *
FROM buyTBL
	INNER JOIN userTBL
    ON buyTBL.userID = userTBL.userID
```

userTBL과 buyTBL 에는 똑같은 이름의 userID가 존재한다.

그래서 모호한 표현(ambiguous)이 되지않도록 앞에 컬럼명의 테이블명을 명시해준다.



코드를 작성하면서 느낀점으로, 테이블 명을 일일히 적기가 힘들다는것을 알 수 있다.

그래서 이전에 배운 AS(alias)를 사용하여 축약한 이름으로 사용할 수 있다.

```sql
SELECT B.userID, B.productName, U.userName, U.userHeight
FROM buyTBL B
	INNER JOIN userTBL U
    ON B.userID = U.userID;
```



INNER JOIN은 조인되는 속성이 A, B모두 존재해야 결과에 출력된다.

JOIN 실습테이블에서 만든 테이블에서 생각한다면

userTBL 과 buyTBL을 JOIN시킬 경우, 구매내역이 없는 회원은 결과에 포함되지 않는다는것을 알 수 있다.

구매내역이 없는 회원도 출력하기 위해서는 OUTER JOIN을 해야한다.



---



#### SQL : INNER JOIN 예제

```SQL
-- 학생을 기준으로 학생이름, 지역, 가입한 동아리, 동아리방을 출력하세요
SELECT SC.stdName, S.stdAddr, SC.clubName, C.clubRoom
FROM stdTBL S
	INNER JOIN stdclubTBL SC
    ON S.stdName = SC.stdName
    INNER JOIN clubTBL C
    ON SC.clubName = C.clubName;
```

```SQL
-- 동아리를 기준으로 가입한 학생의 목록을 출력하세요!
SELECT C.clubName, C.clubRoom, SC.stdName, S.stdAddr
FROM clubTBL C
	INNER JOIN stdclubTBL SC
    ON C.clubName = SC.clubName
    INNER JOIN stdTBL S
    ON S.stdName = SC.stdName;
```



---



#### SQL : OUTER JOIN

INNER JOIN을 했으니 OUTER JOIN에 대해 알아보자.

OUTER JOIN의 종류에는 3가지가 있습니다.

- LEFT OUTER JOIN : 왼쪽테이블에 빠진것을 추가
- RIGHT OUTER JOIN : 오른쪽 테이블에 빠진것을 추가
- FULL OUTER JOIN : 양쪽 테이블에 빠진것을 추가

OUTER JOIN은 INNER JOIN에 포함되지 못한 데이터를 포함해주는 기능을 수행한다.



**OUTER JOIN의 형태**

- OUTER JOIN의 형태
  SELECT <컬럼>
  FROM <왼쪽(left)테이블>
  	(LEFT | RIGHT | FULL) OUTER JOIN <두번째(오른쪽)테이블>
      ON <조인 조건>
  WHERE <검색 조건>
  GROUP BY
  HAVING
  ORDER BY



예제를 통해 살펴봅시다.

```SQL
-- 전체 회원의 구매내역을 조회하세요. 단, 구매 기록이 없는 회원도 출력
SELECT *
FROM userTBL U
	LEFT OUTER JOIN buyTBL B
    ON U.userID = B.userID
ORDER BY U.userID;
```

```SQL
-- 한번도 구매한 적이 없는 회원의 목록을 출력하세요!
SELECT *
FROM userTBL U
	LEFT OUTER JOIN buyTBL B
    ON U.userID = B.userID
WHERE B.productName IS NULL           -- ( = NULL ) 하면안됌
ORDER BY U.userID;
```



---



#### SQL : UNION

UNION은 두 쿼리의 결과물을 행으로 합치는 기능을 수행한다.

UNION 예시를 통해 알아보자

```SQL
(SELECT stdName, stdAddr FROM stdTBL)
UNION
(SELECT clubName, clubRoom FROM clubTBL);
```



UNION은 별도의 쿼리를 합치는 기능을한다.

컬럼명은 처음 나온 쿼리의 컬럼명을 따라 간다.

UNION을 하기 위한 기본조건이 있다.

- 컬럼의 개수가 같아야 한다.
- 데이터 타입이 같아야 한다.



UNION에는 두가지가 있다.

- UNION - 중복을 배제하고 합친다.
- UNION ALL - 중복에 상관없이 무조건 합친다.

일반 UNION을 하게 되면 중복이 배제된 결과가 나오고, UNION ALL을 통한 결합을 하게 되면, 중복이 제거되지 않은 결과가 나온다.



---



SQL 에 대한 기초 학습이 끝났습니다.

JOIN실습을 통해 SQL을 학습하세용

SQL에 추가적으로 공부해야 할 것으로 Database 안에 들어있는 객체가 있다.

- Table, View, Index, Stored Procedure, Function, Trigger

더 세부적인 내용이 있지만, 기초까지만 학습





