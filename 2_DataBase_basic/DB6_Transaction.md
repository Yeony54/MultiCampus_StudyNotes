SQL DataBase

## DataBase SQL : Transaction

Transaction에 대해서 알아보자



- Transaction의 정의
- Transaction을 쓰는 이유
- Transaction 사용 방법

- SQL : Transaction 가능여부

---



#### Tansaction이란?

**Transaction**는 **<i>"데이터베이스의 상태를 변화시키기 위해서 하나의 논리적 기능을수행하기 위한 일, 작업의 단위"</i> **를 뜻한다.

데이터베이스의 상태를 변화시킨다는 말은 SQL 질의어를 통해서 데이터베이스에 접근하는 것을 의미한다.

정의만 보면 뭐가뭔지 모르겠지만 들어보면 생각보다 별것 아니다.

대표적인 예로 은행 송금 예제가 있다.

> **A가 B에게 1000원을 보내는 코드**
>
> 1. A 계좌에서 1000원이 있는지 확인한다.
> 2. B 계좌가 존재하는지 확인한다.
> 3. A 계좌에서 1000원을 뺀 나머지 금액으로 재설정한다.
> 4. B 계좌에서 1000원을 더한 금액으로 재설정한다.

이렇게 A가 B에게 1000원을 보내는 하나의 작업을 Transaction이라고 할 수 있다.



---



#### Transaction은 왜 하는걸까요?

기본적으로 Transaction을 설정하게 되면 DBMS자체에서 4가지 특성(기능)을 제공하고, 이를 ACID라고 부른다.

**ACID**

- Atomicity (원자성) : All or Nothing 전체 아니면 아예 원상태 유지
- Consistency (일관성) : 데이터의 일관성을 유지
- Isolation (독립성) : 동시성 때문에 발생하는 문제를 해결
- Durability (영속성) : 데이터가 안전하게 저장되는것을 보장

위의 은행 송금 예제에서 내가 하나의 Transaction을 수행하게 될 때, 다른 사람들이 은행 송금을 위해 Transaction이 함께 수행될 수 있다.

특히 돈거래를 할 때 나와 거래를 하면서, 다른사람들의 거래까지 모두 같이 수행하려고 하면 어디서 돈이 어떻게 나왔고, 들어가는지 뒤죽박죽 섞여버릴 수 있다.

그래서 Transaction은 내가 작업을 수행하는 데에 있어 다른 방해를 받지 않고 완수할 수 있도록 해주는 것이다.



또한, 앞으로의 사용에서는 임시저장 기능으로 많이 사용이 될 것이다.

Transaction 기능을 통해 작업에 실수가 있었더라도 이전으로 돌아갈 수 있도록 한다.

 

---



#### Transaction 사용 방법

```sql
START TRANSACTION;
```

`START TRANSACTION`을 통해 TRANSACTION을 시작할 수 있다.



**COMMIT, ROLLBACK**

원하는 작업을 다 수행한 후 `COMMIT`,`ROLLBACK`을 수행할 수 있는데,

```SQL
COMMIT;
ROLLBACK;
```

COMMIT은 TRANSACTION에서 한 지금까지의 작업들을 저장한다는 것

ROLLBACK은 TRANSACTION에서 한 지금까지의 작업들을 지우고 이전으로 돌아가게 하는 명령어이다.



**SavePoint**

보통 ROLLBACK 사용 시 작업 전체가 취소되는데 SavePoint는 전체가 아닌 특정부분에서 트랜잭션을 취소시킬 수 있다.

SavePoint를 통해 트랜잭션을 작게 분할할 수 있다.

```sql
SAVEPOINT 세이브포인트이름;
ROLLBACK TO 세이브포인트이름;
```



---



#### SQL : Transaction 가능 여부



SQL에는 3가지 분류가 있다.

- DML
- DDL
- DCL

이 세가지 분류 중에서 오직 DML만 Transaction사용이 가능하다.

다른 DDL이나 DCL에서는 Transaction 사용이 불가하기 때문에 데이터 조작에 신중을 가해야할 것이다.



---


