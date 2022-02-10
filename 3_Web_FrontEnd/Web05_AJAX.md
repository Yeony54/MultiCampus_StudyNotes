Web

## Web Storm AJAX

- Ajax

---

#### AJAX란?

Ajax (Asyncronous JavaScript And XML) : 동적 Web을 실행시킬 때 Web Server에 부하가 가지 않도록 WAS로 따로 분리하여 프로그램을 처리

- WAS (Web Application Server) : Web application 동작 수행
- *Open API 를 동작시킬 때 사용한다*

Round-Trip 방식의 Web : response를 받을 때 마다 새로 페이지를 재구성 - page refresh 발생

SPA (Single Page Application) : Ajax의 통신방법으로, 처음 페이지를 구성한 이후로는 데이터만 받아 화면에 데이터를 적용하는 방식을 사용하여 page refresh를 방지



Ajax는 Open API를 사용할 때 호출한다.

`$.ajax()`의 형태로 호출되며, request에 대한 정보를 JavaScript를 통해 넘겨주게 된다.



#### KOFIC Open API

영화진흥위원회가 제공하는 API를 사용하여 실습을 진행한다.

[KOFIC Open API Link](https://www.kobis.or.kr/kobisopenapi/homepg/main/main.do) 

일별박스오피스, 주말/주간 박스오피스, 공통 코드조회 등의 오픈소스가 있다.

그 중에서 일별박스오피스로 간단하게 실습해보았다.



**일별 박스오피스를 조회하여 1위를 myDiv 내용에 띄워주기**

HTML 설명은 스킵한다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
	<!--파비콘 경로 오류 수정-->
    <link rel="icon" href="data:;base64,iVBORw0KGgo=">
    <script src="https://code.jquery.com/jquery-2.2.4.min.js"
            integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44="
            crossorigin="anonymous"></script>
    <script src="js/jQuery11.js"> </script>
</head>
<body>
    <div id="myDiv">여기에 내용이 바뀌어요</div>
    <input type="button" value="AJAX호출" onclick="my_func()">
</body>
</html>
```

JavaScript

```javascript
function my_func(){
    $.ajax({
        async: true,
        url: 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json',
        data: {
            key:[KOFIC Authorization Key], // 키 입력
            targetDt : '20220209'
        },
        method: 'GET',
        timeout: 3000,
        dataType: 'json',
        success: function(result) {
            let m_title = result["boxOfficeResult"]["dailyBoxOfficeList"][0]["movieNm"]
            $('#myDiv').text(m_title)
        },
        error: function () {
            alert('먼가이상해')
        }
    })
```

ajax에 들어있는 function을 제외한 모든 코드가 ajax() 함수의 인자이다.

- async : 동기 비동기 설정

  - 동기방식 : 프로그램이 끝날때까지 기다리는 방식으로, 프로그램하기가 편하지만 효율적이지 않다.

  - 비동기방식 : 프로그램 호출 후 기다리지 않는 이벤트 처리 방식으로,  효율적이긴 하지만 프로그램 처리가 어렵고 언제수행될지 모르는 단점이 있다.

- url : 사용하고자 하는 API의 기본 url

- data : 입력 Parameter, 필수인자는 적어주어야 한다.

- method : 호출방식 'GET', 'POST', API에 따라 다르니 주의

- timeout : 응답하지 않을 시 종료, 1/1000초의 단위로 3000은 3초다

- dataType : 결과로 반환되는 타입, json은 보기 힘드니까 JavaScript로 변환해주는 툴을 사용하면 좋다.

- success : 성공하면 수행할 function()을 작성하였다. result가 결과로 반환된 데이터이다.

- error : 실패할 경우 수행할 function()을 작성하였다.



성공할 경우 success function을 수행한다.

result는 객체의 연속으로 싸여져 있다. 이를 하나씩 풀어내는 코드이다.

`let m_title = result["boxOfficeResult"]["dailyBoxOfficeList"][0]["movieNm"]`

result 의 "boxOfficeResult" 속의 "dailyBoxOfficeList" 속의 0번째 요소의 "movieNm"을 가져온다는 코드이다.

이 결과를 `$('#myDiv').text(m_title)`를 통해 myDiv에 올릴 수 있다.



