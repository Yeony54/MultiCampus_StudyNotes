Web

## Web Storm
- HTML
  - HTML?
  - HTML 구성
  - WebStorm 동작방법
- CSS
  - CSS적용 방법
- JavaScript
  - JavaScript 기본
  - JavaScript 함수
  - JavaScript 객체 선언
- jQuery
- 연결하기



----

### HTML (HyperText Markup Language)

#### HTML?

- Markup 언어

  - 태그언어
  - 정해져 있는 Tag를 사용하여 화면을 구성한다.
  - 배우기 쉽다.

- 1999년 12월 HTML 4.01을 마지막 버전으로 버전업을 하지 않겠다고 선언하였다. (W3C)

  2014년에 버전업이 한번 더 있었고 그것이 지금 사용되는 **HTML5** 버전이다.

- HTML의 구성은 3가지가 있는데, HTML5가 되면서 다 합쳐졌다.

  - ECMAScript (HTML Element), CSS 3, JavaScript

#### HTML 구성

HTML 문서를 만들면 만들어지는 기본 구조를 보며 HTML의 구성을 설명한다.

```html
<!-- HTML 기본 생성 구조 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

</body>
</html>
```

- **Element**(요소, 엘리먼트) : HTML의 Tag+내용을 Element라고 한다.

  - `<>` 괄호로 닫혀있는 것을 Element라고 부른다.

- **Tag**(태그)

- **Attribute**(어트리뷰트, 속성) 

- 기본 구조, Element 설명

  `<!DOCTYPE html>` 은 문서의 형태를 알려주는 역할을 한다.

  HTML은 크게 `<head>~</head>`와 `<body>~</body>` 2부분으로 나누어진다.

  전체 html은 `<html>~</html>`로 묶여진다.

  html은 이렇게 묶이고 나누어지는 포함관계를 가진다. (안가지는것들도 있다.)

  - `<html>` : HTML 문서는 반드시 이 Element 로 감싸져야 한다.
  - `<head>` : 문서의 설정을 담당한다. 대표적으로 charset 설정(유니코드)
  - `<body>` : 문서의 내용을 표현한다.

  - `<a>` : 앵커라고 부르며, 하이퍼링크(클릭 가능한 형태)를 만들어준다.

    클릭했을 때, request전송 방식을 설정해주는 attribute가 존재한다.

  - `<img>` : 그림을 표현할 때 사용하는 Element

    src의 attribute를 이용해 이미지 url을 담는다.

  - `<br>` : 한줄을 띄우는 Element

  - `<table>` : 2차원 테이블형태로 데이터를 표현하기 위해 사용

  - `<ul><li>` : 목록을 만드는 Element

#### WebStorm 동작방법

1. (내장) Web Server에 프로젝트의 존재를 알린다 : configure
2. Web Server가 프로젝트를 인식한 상태에서 기동
3. Web Client(Browser)를 실행시킨다
4. URL(protocol://IP:Port/Resource(파일명))을 이용해서 Web Client가 Web Server에 Request를 보낸다
5. Web Server가 Request에 대한 처리를 한 후 Web Client에게 Response를 보낸다
6. Web Client가 Response를 해석해서 Browser에 Rendering한다.



---



### CSS (Cascading Style Sheet)

- 화면을 꾸며준다.
- 영역을 잡아주는 Element
  - `<div></div>` : block level element - 영역을 끝까지 잡아준다.
  - `<span></span>` : inline element - 내용부분만 영역을 잡아준다.



##### CSS 적용방법

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
        <h1>여기는 h1입니다</h1>
        <div>이것은 소리없는 아우성</div>
        <img src = "img/naver_com_20140417_130653.jpg">
        <span style="color:red">여기는 span 영역</span>
    </body>
</html>
```

- 코드설명

  - `<h1>~<h6>` markdown의 제목과 같이 중요도를 숫자로 표시한 제목 Element

  - `<div>` 로 만들어진 구역과 `<span>`으로 만들어진 구역을 비교하기 위해 작성, 관리자창으로 보면 표시되는 구역이 다른것을 확인할 수 있다.

  - `<span style = "color:red">`는 속성에 직접 style을 명시해 주는것이다.

    색상을 빨갛게 만든다.

- 속성에 직접 style을 명시해 주는것은 좋은 방법이 아니기 때문에, javascript를 사용



---



### JavaScript

java script를 사용하여 동적으로 화면을 조작하는 방법을 본다.

우선, HTML에서 Browser에 표시할 버튼을 만드는 코드이다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/aaa.js">
        // javascript 코드를 작성
        // html과 javascript가 혼용되기 때문에 별도의 파일로 관리
    </script>
</head>
<body>
    <!-- 버튼이 클릭되면 JavaScript 함수를 실행 -->
    <input type = "button" value = "버튼을 클릭하세요"
           onclick = "my_func()">
</body>
</html>
```

- `<script>~</script>` 이곳에 javascript 코드를 작성할 수 있다. 

  하지만, html과 javascript의 언어가 혼용되기 때문에 별도의 파일로 관리한다.

  script에 src속성을 사용하여 javascript 파일을 연결시켜준다.

- body에 버튼이 눌리면 javascript를 동작하는 Element를 추가하였다

  - value에 지정된 값을 버튼에 표시해준다.
  - onclick속성으로, 클릭될 때 실행할 이벤트를 지정한다.



#### JavaScript 예제

JavaScript는 Browser에서 실행되며, console에서 출력을 확인할 수 있다.

##### JavaScript 기본

- 콘솔 출력

  ```javascript
  console.log('콘솔출력')
  ```

- 변수 선언

  ```javascript
  let tmp1 = 100;		    //number
  let tmp2 = '야호';	   //string
  let tmp3 = true;	    //boolean (소문자)
  let tmp4 = [1,2,3,4]	//array
  ```

- 알림창

  ```javascript
  alert('알림창 띵동')
  ```

  



##### JavaScript 함수

- 선언적 함수

  ```javascript
  function my_func(a,b){
      return a+b;
  }
  
  console.log(my_func(10,20))
  ```

- 익명함수(람다함수)

  ```javascript
  let tmp6 = function(a,b) {return a+b;}
  console.log(tmp6(10,30))
  ```



##### JavaScript 객체 선언

```javascript
let obj = {
    name : '김연아',
    age : 20,
    print_info :function(){
        return this.name + ' : ' + this.age;
    }
}

console.log(obj.name)
console.log(obj.age)
console.log(obj.print_info())

console.log(obj['name'])
console.log(obj['age'])
```



### jQuery

jQuery는 모든 browser에서 동작하는 Client javascript library 이다.

jQuery를 사용하기 위해 CDN 방식을 사용한다.

CDN (Content Delivery Network) : jQuery를 HTML Tag를 이용해서 library를 동적으로 download해서 사용하는 방식





### 연결하기

HTML, CSS, JavaScript, jQuery를 모두 연결해서 사용하기 위해 link를 해주어야한다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--jQuery library-->
    <script src="https://code.jquery.com/jquery-2.2.4.min.js"
            integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44="
            crossorigin="anonymous"></script>
    <script src="js/jQuery01.js"> </script>
    <link rel="stylesheet" href="css/myStyle.css">
</head>
<body>
    
</body>
</html>
```

jQuery 실습을 했던 HTML 코드이다.

우선 jQuery를 사용하기 위해 CDN방식으로 jQuery Library를 가져온다. (6번째줄)

웹동작을 하기위해 JavaScript파일인 `jQuery01.js`를 연결한다. 

css를 적용하기 위해 `css/myStyle.css`를 연결한다.

리스트를 만들고, event 적용을 위한 button을 만들었다.





