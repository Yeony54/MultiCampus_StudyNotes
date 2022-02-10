SQL DataBase

## DataBase 개요

데이터베이스란 무엇인가?



---



#### 1. DataBase란?

**DataBase**는 데이터의 집합을 의미한다. 종이, 데이터 형태의 상관없이 대용량의 데이터를 체계적으로 구성해 놓은것을 DataBase라고 칭할 수 있다.

DataBase는 여러개가 존재할 수 있고, 이를 프로그램을 통해 여러사람이 사용할 수 있다.

이렇게 DataBase를 사용하기 위해 지원하는 여러 프로그램을 **DBMS**라고 한다.



#### 2. DBMS (Database Management System)

**DBMS**는 DataBase를 관리하는 시스템으로 여러 프로그램이 개발되어져 있다.

예시로 몇가지를 적어보았다.

| program    | company     | type       |
| ---------- | ----------- | ---------- |
| MySQL      | Oracle      | 중,소형       |
| MariaDB    | Open Source | 개인         |
| Oracle     | Oracle      | 대형         |
| DB2        | IBM         | main frame |
| SQL Server | MS          |            |



#### 3. DBMS의 종류

- 계층형 DBMS (hierachical DBMS)
  
  - 폴더를 만들어 관련있는 데이터 끼리 모아놓은 구조
  
  - 장점 : 목적에 맞게 방문하는 형태로 사람의 생각구조와 비슷하다
  
  - 문제점 : 완전 따로 나누어져 있어 연계가 힘들다.

- 네트워크 DBMS (Network DBMS)
  
  - 따로 떨어져 있는 폴더를 프로그램적으로 서로 연결한 구조
  
  - 아이디어는 좋은데, 구현이 너무 어렵다.

- 관계형 DBMS (Relational DBMS)
  
  - 1970년 : IBM에 재직중이던 E.F.Codd가 논문을 발표
  
  - 지금의 우리가 알고 있는 colums(열)과 record,row(행) 으로 이루어진 데이터
  
  - 정형화된 데이터에 특화되어있음
  
  - 커다란 발전을 이룸



#### 4. MySQL 사용 방법

MySQL은 CS(Client-Server)구조를 가진다. 

DB를 활용하기 위해서는 MySQL Server에 접속을 해야하는데 3가지 방법이 있다.

- 기본으로 제공되는 console을 이용 (불편함)

- 타 사에서 만든 프로그램을 사용 (DBeaver, DataGrip)

- MySQL의 GUI 프로그램을 사용 (workbench)



---



앞으로 MySQL이 제공하는 workbench를 사용하여 DB실습을 할것이다.

**Schema** : MySQL에서 schema라는 용어는 DataBase와 동일하게 사용한다.
