SQL DataBase

## DataBase SQL : SELECT

SELECT 마지막파트

**SELECT**

- Sub Query 서브쿼리
- ORDER BY
- GROUP BY, 집계함수
- GROUP BY, HAVING
- SQL 명령어 순서



---



####  SQL : Sub Query (서브쿼리)

문제 : 김경호보다 키가 크거나 같은 사람의 이름과 키를 조회하세요

이 문제는 어떻게 풀어야 할까?

먼저 김경호의 키를 조회해 보자.

```SQL
-- 1. 김경호의 키를 먼저 알아내야 한다.
SELECT userHeight
FROM userTBL
WHERE userName = '김경호';   -- 177
```

그리고 알아낸 키를 이용해 이보다 크거나 같은 사람의 이름과 키를 조회하자.

```SQL
-- 2. 알아낸 키를 이용해서 다른 사람의 이름과 키를 조회한다.
SELECT userName, userHeight
FROM userTBL
WHERE userHeight >= 177;
```

지금 문제를 풀기 위해 두개의 SELECT문을 사용하였다.

이를 서브쿼리를 활용하여 하나로 합칠 수 있다.

```SQL
SELECT userName, userHeight
FROM userTBL
WHERE userHeight >= (
    SELECT userHeight
    FROM userTBL
    WHERE userName = '김경호')
    AND userName NOT IN ('김경호');
```

처음에는 어렵지만, 서브쿼리를 활용해서 만드는 연습을 해야한다.



---



#### SQL : ORDER BY 정렬

정렬은 기본적으로 오름차순으로 정렬이된다.

SELECT절에서 ORDER BY는 제일 마지막에 위치되어 실행된다.

오름차순은 생략이 가능하지만, 명시적으로 ASC라고 하며, 내림차순은 DESC로 표기한다.

```SQL
-- 가입일이  빠른 순으로 모든 회원의 이름, 아이디, 가입일을 출력하세요
SELECT userName, userID, userDate
FROM userTBL
ORDER BY userDate ASC;
```

```SQL
-- 회원의 이름과 키를 출력하세요. 단, 키에 대한 내림차순으로 출력하세요
SELECT userName, userHeight
FROM userTBL
ORDER BY userHeight DESC;
```



**2차 정렬**

2차 정렬은 정렬을 한 상태에서 똑같은 값들을 상대로 한번더 정렬을 하는것이다.

```SQL
-- 동률이 존재할 경우 이름 오름차순으로 정렬
SELECT userName, userHeight
FROM userTBL
ORDER BY userHeight DESC, userName ASC;
```



---



#### SQL : GROUP BY, 집계함수

**GROUP BY**절은 유형별로 데이터를 그룹화하여 데이터를 조회할 수 있는 기능이다.

GROUP BY절을 사용할 때는 보통 집계함수와 함께 쓰인다.

**집계함수**에는 SUM, COUNT, MIN, MAX, AVG, STDEV 등 다양한 종류가 있다.

집계함수는 GROUP BY절과 함께 사용하며, GROUP BY 절이 있을 때, 그룹별로 집계함수를 실행할 수 있다.

```SQL
-- 사용자별 구매한 물품의 총 개수를 출력
SELECT userID, SUM(buyAmount)
FROM buyTBL
GROUP BY userID;
```

```SQL
-- 사용자별 구매한 횟수를 출력
SELECT userID, COUNT(buyAmount)
FROM buyTBL
GROUP BY userID;
```

```SQL
-- 사용자별로 한번 구매 시 평균 몇 개의 물건을 구매했는지 조회
SELECT userID, AVG(buyAmount)
FROM buyTBL
GROUP BY userID;
```

간단하게 GROUP BY만 추가하여 사용자별 집계함수를 사용하는 구문을 동작해 보았다.



---



#### SQL : GROUP BY, HAVING 절

문제 : 사용자 별 총 구매 금액이 1000원 이상인 사용자의 아이디와 구매 금액을 출력

이전에 배운걸로 활용한다면 `WHERE(GROUP BY 총구매금액 집계 >= 1000)`의 형태로 해야할 것 같지만, 그렇지 않다. WHERE절에는 집계함수를 쓸 수 없다.

GROUP BY에서는 HAVING절을 사용하여 조건을 만든다.

```SQL
SELECT userID, SUM(productPrice*buyAmount) -- 총사용금액 = 가격*개수
FROM buyTBL
GROUP BY userID
HAVING SUM(productPrice*buyAmount) >= 1000;
```

먼저 `GROUP BY`를 사용하여 사용자별 그룹핑을 진행하였고, `HAVING` 을 통해 총 사용금액이 1000 이상인 조건을 만드는 방식으로 사용할 수 있다.



---



#### SQL : 명령어 순서

여러가지 명령어들을 배워보며 짐작했듯이 명령어에는 순서가 있다.

아까 말한 ORDER BY는 맨 마지막에 작성해 준다고 했고, HAVING 절은 GROUP BY 절 뒤에 나올 수 있다.

이 순서를 정리해 보면

- SELECT
- FROM
- WHERE
- GROUP BY
- HAVING
- ORDER BY

이렇게 정리할 수 있다.

명령어 순서에 맞게 SELECT문을 잘 작성해 보자



---





**SQL : Sub Query 연습문제**

문제 : 주소가 '경남'인 사람들의 키보다 크거나 같은 사람을 조회하세요

우선 주소가 '경남'인 사람들의 키를 알아보자

```sql
SELECT userName, userHeight
FROM userTBL
WHERE userAddr = '경남';
```

이전에 봤던 ANY를 활용하여 이렇게 완성할 수 있다.

```sql
SELECT userName, userHeight
FROM userTBL
WHERE userHeight >= ANY(
    SELECT userHeight
    FROM userTBL
    WHERE userAddr = '경남');
```





**SQL : 응용문제**

```SQL
-- 가장 큰 키와 가장 작은 키의 회원의 이름과 키를 출력하세요
SELECT * FROM userTBL;
SELECT userName, userHeight
FROM userTBL
WHERE userHeight = (SELECT MIN(userHeight) FROM userTBL)
	OR userHeight = (SELECT Max(userHeight) FROM userTBL)
ORDER BY userHeight;
```













