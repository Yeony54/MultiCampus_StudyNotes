SQL DataBase

## DataBase SQL : SELECT

SELECT는 DML 명령어 중 하나이다.

제일 많이 사용되는 명령어이며, 그래서 많은 기능들이 존재한다.

SELECT로 사용할 수 있는 조건문과 함수들을 사용해보고 기록



SELECT

- WHERE절
- 논리연산자, 비교연산자
- BETWEEN 연산자
- LIKE 연산자, 패턴매칭
- IN, NOT IN, ANY, ALL
- DISTINCT
- LIMIT 사용법
- SQL 응용 테이블복사



---



#### SQL : WHERE 절

WHERE절을 사용하여 SELECT를 사용할 때 조건을 줄 수 있다.

```SQL
USE sqldb;
```

우선 이전에 만들어둔 db를 사용설정 해 준다.

```SQL
-- 사용자 이름이 '김경호'인 데이터 조회
SELECT * 
FROM userTBL
WHERE userName = '김경호';
```

이렇게 userName에 '김경호'와 같을 경우를 조건으로 걸어 검색할 수 있다.



---



#### SQL : 논리연산자, 비교연산자

논리연산자와 비교연산자는 다른언어에서도 많이 사용하는 연산자이다.

위에서 사용했던 WHERE 절을 활용해서 아래 예제를 풀었다.

```SQL
-- 1970년 이후에 출생하고 키가 182 이상인 사람의 아이디와 아름을 조회하세요
SELECT userID, userName
FROM userTBL
WHERE birthYear >= 1970 AND userHeight >= 182;
```

WHERE절에 비교연산자를 사용할 수 있으며, 여러가지 조건을 사용할 때 AND나 OR 등의 비교 연산자를 사용하여 조건을 추가할 수 있다.

```SQL
-- 1970년 이후에 출성하거나 키가 182 이상인 사람의 아이디와 이름을 조회헤세요
SELECT userID, userName
FROM userTBL
WHERE birthYear >= 1970 OR userHeight >= 182;
```



---



#### SQL : BETWEEN 연산자

BETWEEN은 영어에서 사용하는 `between A and B`와 같이 사용한다.

```SQL
-- 키가 180~183인 사람을 조회하세요
SELECT userID, userName, userHeight
FROM userTBL
-- WHERE userHeight >= 180 AND userHeight <= 183; 
WHERE userHeight BETWEEN 180 AND 183;
```

AND를 사용하여 이상, 이하로 표현할 수도 있고, BETWEEN을 사용하여 표현할 수 있다는것을 알아두자.



---



#### SQL : LIKE 연산자, 패턴매칭

많이 사용되는 기능 중 하나인 패턴매칭이다.

성이 '김'씨인 사람들의 이름과 키를 조회하세요 라는 문제를 어떻게 풀어야 할까?

이 때, 와일드카드 문자를 사용한다.

**와일드카드 문자**

- % : 0개 이상의 글자를 의미
- _ : 1개의 글지를 의미

와일드카드로 패턴매칭을 할 때에는 LIKE 연산자를 사용한다.

```SQL
SELECT userName, userHeight
FROM userTBL
WHERE userName LIKE '김%';
```

'김%' 패턴을 사용하여 '김'씨 성을 가진 사람들의 이름과 키를 출력할 수 있다.



---



#### SQL : IN, NOT IN, ANY, ALL 연산자

**IN** 연산자는 조건절에서 사용한다.

다수의 비교값과 비교하여 하나라도 같은 값이 있다면 true이다.

```SQL
-- 키가 176, 174, 172 인 사람의 아이디와 이름을 출력하세요
SELECT userID, userName
FROM userTBL
-- WHERE userHeight = 176 OR userHeight = 174 OR userHeight = 172;
WHERE userHeight IN (176, 174, 172);
```

OR 을 써서 만들 수 있는 구문을 IN을 이용해 더 간단하게 만들 수 있다.



**NOT IN** 연산자는 IN과 반대되는 개념으로 하나라도 같은 값이 있다면 false이다.

```SQL
-- 키가 176, 174, 172가 아닌 사람의 아이디와 이름을 출력하세요
SELECT userID, userName
FROM userTBL
WHERE userHeight NOT IN (176, 174, 172);
```

NOT을 통해 IN과 반대되는 기능을 수행할 수 있다.



**ANY **연산자는 다수의 비교값 중 하나라도 만족하면 ture이다.

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight = ANY(176, 174, 172);
```

위의 문장으로 IN과 같은 결과를 출력할 수 있다. 

IN과 다른점은 비교 연산자 `(=, <, >)`를 사용한다는 점이다.

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight > ANY(176, 174, 172);
-- userHeight가 172 이상인 사람들을 출력
```

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight < ANY(176, 174, 172);
-- userHeight가 176 이하인 사람들을 출력
```

ANY는 나올 수 있는 모든 조건에서 OR연산을 수행한 것과 동일한 결과를 얻는다.



**ALL** 연산자는 전체값을 비교하여 모두 만족해야만 true이다.

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight = ALL(176, 174, 172);
```

위의 예시를 ALL로 동작시키면 결과가 나오지 않는다.

하나의 값이 모든 값과 일치할 수 없기 때문이다.

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight > ALL(176, 174, 172);
-- userHeight가 176 이상인 사람들을 출력
```

```sql
SELECT userID, userName
FROM userTBL
WHERE userHeight < ALL(176, 174, 172);
-- userHeight가 172 이하인 사람들을 출력
```

ALL은 나올 수 있는 모든 조건에서 AND연산을 수행한 것과 동일한 결과를 얻는다.



---



#### SQL : DISTINCT

DISTINCT는 중복을 제외할 때 쓸 수 있다.

```SQL
-- 회원의 주소를 중복을 제외하여 출력해주세요
SELECT DISTINCT userAddr
FROM userTBL;
```



---



#### SQL :  LIMIT

이전에도 한번 봤던 LIMIT이다.

LIMIT은 출력할 값을 제한해 주는 역할을 한다.

```SQL
SELECT * FROM userTBL LIMIT 3;
```

```SQL
SELECT * FROM userTBL LIMIT 0,3;
```

이 두코드는 같은 동작을 수행한다.

LIMIT를 사용할 때에 `LIMIT (OFFSET), (가져올 개수)`로 사용하게 되는데, `OFFSET`을 입력하지 않으면 Default로 0으로 동작하게 된다.

```SQL
SELECT * FROM userTBL LIMIT 2,5;
```



---



#### SQL : (응용) 테이블 복사

테이블 복사하는 방법 

```SQL
CREATE TABLE userTBL (
    userName VARCHAR(6),
    userAddr VARCHAR(12),
    userMobile VARCHAR(11)
);
```

CREATE 를 할 때 위의 예시처럼 기본적으로 명세를 지정해서 생성해 주었다.

하지만 TABLE을 입력해서 CREATE할 수 있는 방법도 있다.

```SQL
CREATE TABLE tmpTBL(
    SELECT * FROM userTBL
);
```

이렇게 CREATE TABLE 안에 바로 TABLE을 SELECT구문으로 넣어 생성할 수 있다.

한가지 다른점이 있는데, 

```SQL
DESC userTBL;
DESC tmpTBL;
```

DESCRIBE 명령어로 원래 테이블과 복사한 테이블의 명세를 확인해 보면,

원래 테이블에 있는 KEY(PK, FK)는 복사가 되지 않는것을 확인할 수 있었다.





---





다음장에서 SELECT의 ORDER BY, GROUP BY절을 설명한다.
