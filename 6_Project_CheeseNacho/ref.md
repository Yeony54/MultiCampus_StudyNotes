# Reference



[CheeseNacho git](https://github.com/supaflanka/CheeseNacho)

왜 나쵸치즈가 아닌 치즈나쵸가 되었는지는 모르겠지만 우리의 프로젝트 git 링크



[TMDB](https://www.themoviedb.org/?language=ko)

API 사이트



---



[loading화면](https://kkamikoon.tistory.com/entry/Javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-%EB%A1%9C%EB%94%A9%EC%A4%91-%ED%99%94%EB%A9%B4-%EB%A7%8C%EB%93%A4%EA%B8%B0%EB%A1%9C%EB%94%A9-%ED%91%9C%EC%8B%9C)

페이지 로딩화면



MySQL 문법

```sql
# 다른 db의 table조회하기
select *
from database1.table1 a
join database2.table2 b m on a.id = b.id
```

[임대리 - 테이블복사](https://server-engineer.tistory.com/500)

```sql
# Sample SQL 
INSERT INTO TB_BOARD_TEMP (NUM, TITLE, CONTENTS) SELECT NUM, TITLE, CONTENTS FROM TB_BOARD;
```



[nuung.log - Django Model 필드 모음](https://velog.io/@qlgks1/4.-Django-Model-%ED%95%84%EB%93%9Cfiled-%EB%AA%A8%EC%9D%8C%EC%A7%91)

model을 구성하는 field 방법 모음

★ 깨닳 : sql 모델로는 리스트를 구현하면 안좋음

하는방법이 있긴함 

- [how to create list field in django](https://stackoverflow.com/questions/5216162/how-to-create-list-field-in-django)
- [Django document - List Fields](https://django-mysql.readthedocs.io/en/latest/model_fields/list_fields.html)



---



api 반복 호출 방법

```js
// 일정시간마다 api 호출하는 방법
var health_timer = null;
var interval_val = 5000;

$(function() {
  // 5초마다 호출
	health_timer = setInterval(function() {

		//호출할 메소드

	}, "5000");

}

출처: https://leelsm.tistory.com/17 [Devlog]
```

```js
timeRequest(){
  const arr = ['첫번째','두번째','세번째','네번째']
  arr.forEach((titem, index) => {
    setTimeout(function() {
      this.getRes(titem)
    }, 1000 * (index + 1))
  })
}

getRes(){
  // api 호출 함수
  this.axios.post("api주소",{ num }) 
  .
  .
}

출처: https://im-designloper.tistory.com/68
```







---



참고

데이터 파싱 python에서 하는 방법 https://my-repo.tistory.com/33

towards 웹 공부 추천페이지 : [https://towardsdatascience.com](https://towardsdatascience.com/using-python-flask-and-ajax-to-pass-information-between-the-client-and-server-90670c64d688)



