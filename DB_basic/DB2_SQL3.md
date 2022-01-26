SQL DataBase

## DataBase SQL

DataBase MySQL을 사용해 동작해 보았던 것들을 기록한다.

- Primary Key 실습
- Forien Key 실습



Key는 column에 설정할 수 있고, Primary Key와 Forien Key가 존재한다.

이전에 앞서 Primary Key와 Forien Key에 대해서 설명했다.

이번에는 PK, FK 코드를 작성하고 작동시켜 보자.



---



#### SQL : Primary Key 실습

**<PK를 설정하지 않은 코드>**

```sql
CREATE TABLE userTBL (
    userName VARCHAR(6),
    userAddr VARCHAR(12),
    userMobile VARCHAR(11)
);

INSERT INTO userTBL VALUES('아이유','서울','1234');
INSERT INTO userTBL VALUES('김연아','인천','5678');
INSERT INTO userTBL VALUES('신사임당','부산','1357');

SELECT * FROM userTBL;
```

| userName | userAdrr | userMobile |
| -------- | -------- | ---------- |
| 아이유   | 서울     | 1234       |
| 김연아   | 인천     | 5678       |
| 신사임당 | 부산     | 1357       |

위의 코드를 실행시키고 SELECT를 통해 확인 해 본 결과이다.



**<PK를 설정한 코드>**

```sql
DROP TABLE IF EXISTS userTBL;
```

```sql
CREATE TABLE userTBL (
    userName VARCHAR(6) PRIMARY KEY,
    userAddr VARCHAR(12),
    userMobile VARCHAR(11)
);

INSERT INTO userTBL VALUES('아이유','서울','1234');
INSERT INTO userTBL VALUES('김연아','인천','5678');
INSERT INTO userTBL VALUES('신사임당','부산','1357');

SELECT * FROM userTBL;
```

`IF EXISTS`는 userTBL이 존재하면 Drop을 실행하게 하는 구문이다.

userName 뒤에 `PRIMARY KEY`를 입력하여 고유키로 설정해 주었다.

| userName | userAddr | userMobile |
| -------- | -------- | ---------- |
| 김연아   | 인천     | 5678       |
| 신사임당 | 부산     | 1357       |
| 아이유   | 서울     | 1234       |

이전에 나온 결과와 비교해 본다면 순서가 다른 것을 확인 해 볼 수 있다.

이 이유는 **Primary Key**를 지정해 주었기 때문이다.

Primary Key를 지정해 주어서, Clustered Index가 자동으로 설정되고, 데이터가 사전식으로 정렬된 결과가 나왔다. 



---



#### SQL : Forien Key 실습

```sql
CREATE TABLE buyTBL (
    userName		VARCHAR(6) NOT NULL, -- forien key
    productName 	VARCHAR(10) NOT NULL,
    productPrice 	INT NOT NULL,
    buyAmount 		INT NOT NULL,
    FOREIGN KEY(userName) REFERENCES userTBL(userName)
);
```

마지막 줄의 코드를 통해 `Forien Key`를 적용했다.

userName각각 현재 table의 FK를 적용할 userName과 연결 시킬 table의 PK인 userName이다.

이를 통해 buyTBL의 userNamed은  userTBL의 PK인 userName을 참조하는 FK가 되었다.

```sql
-- test code (error)
INSERT INTO buyTBL VALUES('홍길동', '냉장고', 1000, 2);
```

test code를 입력하면 ERROR가 발생한다.

userName이 FK가 되었기 때문에 PK에 존재하지 않는 '홍길동'을 입력할 수 없기 때문이다.

```sql
-- test data Insert
INSERT INTO buyTBL VALUES('아이유', '냉장고', 1000, 2);
INSERT INTO buyTBL VALUES('김연아', 'TV', 2000, 3);
INSERT INTO buyTBL VALUES('신사임당', '컴퓨터', 3000, 4);

SELECT * FROM buyTBL;
```

다시 코드를 입력하고 SELECT구문을 통해 확인했다.

```SQL
-- test code (error)
DELETE FROM userTBL WHERE userName = '아이유';
```

test code를 입력하면 ERROR가 발생한다.

userTBL을 참조하는 buyTBL의 FK가 존재하기 때문에 삭제할 수 없기 때문이다.





