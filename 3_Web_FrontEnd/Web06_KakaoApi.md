Web

## Web Storm KAKAO API 예제

- KAKAO API

---

#### KAKAO API

영화 포스터를 불러오는 예제를 동작시켜보기 위해 KAKAO 의 Daum 이미지 검색 API를 사용하였다.

[KAKAO 이미지검색 OpenAPI 사용방법](https://csora2.tistory.com/37) 



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="https://code.jquery.com/jquery-2.2.4.min.js" integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44=" crossorigin="anonymous"></script>
    <script src="js/jQuery13.js"> </script>
</head>
<body>
    <div id="myDiv">여기에 이미지 추가할거에요</div>
    <input type="text" id="searchTitle">
    <input type="button" value="KAKAO 이미지 검색"
           onclick="my_func()">
</body>
</html>
```

``` javascript
function my_func() {
    let title = $('#searchTitle').val()
    let key = [KAKAO Authorization Key]

    $.ajax({
        async: true,
        url: [KOFIC Authorization Key], // 키 입력
        method: 'GET',
        headers: {
            Authorization: "KakaoAK " + key
        },
        data: {
            query: title
        },
        timeout: 4000,
        dataType: 'json',
        success: function(result) {
            $('#myDiv').empty()
            //console.log(result)
            let imgUrl = result['documents'][0]['thumbnail_url']
            let img = $('<img />').attr('src', imgUrl)
            $('#myDiv').append(img)
        },
        error: function() {
            alert('먼가 이상해요')
        }
    })
}
```

코드는 어려운게 없다.

`let imgUrl = result['documents'][0]['thumbnail_url']`로 img를 받아오고

`let img = $('<img />').attr('src', imgUrl)`로 받아온 img로 태그작성,

`$('#myDiv').append(img)`로 myDiv에 추가해준다.



다만, 기술문서만 보고 API를 적용시키는 방법이 어렵고 HTML, JavaScript에서 나는 오류를 빠르게 찾을 수 없어서 힘들었다...

