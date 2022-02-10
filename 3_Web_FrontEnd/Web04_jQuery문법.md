Web

## Web Storm jQuery 문법

- Selector
- Method
- Element 생성
- jQuery Event
- Document Ready

---

#### Selector

- 전체 선택자(universal selector) : 현재 HTML 안에 있는 모든 Element를 다 선택

  ```javascript
  $('*').css('color','red');
  ```

  전체 Element의 글자색을 빨간색으로 적용한다.

- 태그 선택자(tag selector) : 태그명을 이용하여 선택

  ```javascript
  alert($('div').text())
  ```

  `$`로 태그를 선택할 수 있다.

  뒤의 text()는 method라고 부르며, 인자가 없을 시 태그사이의 문자열을 알아오고, 인자가 있으면 태그사이의 문자열을 변경한다.

- ID 선택자(ID selector) : id attribute를 이용해서 선택

  ```javascript
  $('#seoul').remove()
  ```

  `#`을 사용하여 ID를 선택

- class 선택자(class selector) : class attribute를 이용해서 선택

  ```javascript
  $('.myClass').css('color','yellow')
  ```

  `.`을 사용하여 class선택

- 자식 선택자, 후손 선택자

  ```javascript
  $('ul > li').css('color','violet')
  $('ul li').css('color','violet')
  ```

  자식선택자는 `>` 를 사용하고, 후손 선택자는 공백(space)를 사용한다.

- 동위선택자 (형제관계)

  ```javascript
  $('#seoul + li').css('color','red')
  $('#seoul ~ li').css('color','red')
  ```

  `+`로 바로 다음에 나오는 형제를 지칭

  `~`로 바로 다음에 형제부터 그 밑 형제 모두 다를 지칭

- 속성 선택자 : attribute를 이용해서 선택

  ```javascript
  $('[value=클릭클릭]').remove()
  ```

  `[]` 를 사용해서 속성이 일치하는것을 찾는다.

- list 자식 선택방법

  - first, last 처음과 끝을 의미

    ```javascript
    console.log($('ol > li:first').text())
    console.log($('ol > li:last').text())
    ```

  - +로 형제 찾기

    ```javascript
    console.log($('ol > li:first + li').text())
    ```

  - eq

    ```javascript
    console.log($('ol > li:eq(1)').text())
    ```

    0부터 시작하는 순서로 선택할 수 있다. 음수가능



---



#### Method

- text

  - 인자가 없으면 태그사이의 문자열을 알아온다.

    ```javascript
    alert($('div').text())
    ```

  - 인자가 있으면 태그사이의 문자열을 변경한다.

    ```javascript
    $('div').text('변경할내용')
    ```

- css

  스타일을 변경한다.

  ```javascript
  $('li').css('color','blue')
  ```

  css는 한번에 1개의 style만 적용해서 그린다. 효율도 좋지않고, 보기에도 힘들기 때문에 css를 file로 만들어 적용시키는 방법을 사용한다.

  css는 잘 사용되지 않고 주로 addClass( )를 사용한다.

- addClass, removeClass

  - addClass : 클래스 속성 추가

    ```javascript
    $('ul > li:eq(1)').addClass('myStyle')
    ```

  - removeClass : 클래스 속성 삭제

    ```javascript
    $('ul > li:eq(1)').removeClass()
    ```

- val

  - 인자가 없으면 사용자가 입력한 값을 알아온다.

    ```javascript
    $('[type=text]').val()
    ```

  - 인자가 있으면 값을 변경한다.

    ```javascript
    $('[type=text]').val('변경해요')
    ```

- attr, removeAttr

  - attr : 속성의 값을 변경

    ```javascript
    $('[type=text]').attr('value','변경값')
    ```

  - removeAttr : 속성의 값을 remove

    ```javascript
    $('[type=text]').removeAttr('disabled')
    ```

- remove, empty

  - remove : 자기 자신과 자신의 후손을 모두 삭제

    ```javascript
    $('ul').remove()
    ```

  - empty : 자기 자신은 삭제하지 않고, 후손만 삭제

    ```javascript
    $('ul').empty()
    ```

- each

  object와 배열 등 length속성을 갖는 배열과 유사 배열 객체들을 index기준으로 반복할 수 있는 메소드

  - $.each( )  - jQuery 유틸리티 메서드

    일반적인 반복함수 처럼 사용

    첫번째 매개변수로 배열이나 객체를 받고, 두번째 매개변수로 콜백함수를 받으며, 콜백함수의 인자로는 인덱스와 값을 인자로 갖는다.

    ```javascript
    $.each(arr, function(index, item){
        var result = '';
        result += index + ' : ' + item.title + ', ' + item.url;
        console.log(result);
    })
    ```

  - $( ).each( )  -jQuery 일반 메서드

    jQuery에 선택자를 넘기면 해당 선택자를 자바스크립트 반복문과 같이 사용한다.

    ```javascript
    $('.list li').each(function (index, item){ 
    	$(item).addClass('li_0' + index);
        });
    ```

  

---



#### Element 생성

1. element 생성

   ```javascript
   $('<li></li>').text('신사임당')
   ```

   ```javascript
   //<img src='img/penquin.jpg'>
   $('<img />').attr('src','img/penguin.jpg')
   ```

2. 생성된 element 화면에 추가

   - append : 맨 마지막 자식으로 추가

   - prepend : 맨 처음 자식으로 추가

   - after : 바로뒤에 형제로 추가

     ```javascript
     $('ul>li:eq(1)').after(li)
     ```

   - before : 바로앞에 형제로 추가

   

---



#### jQuery Event

event는 사용자가 마우스나 키보드 등으로 하는 행위를 말한다

- source : 현재 event가 발생한 객체
- handler : event가 발생했을 때, 특정 처리를 하는 java script 함수
- event attribute(속성) : onclick, ondblclick등 html 속성으로 event 처리 지정을 위한 속성

*HTML Element가 Event Source가 되어 Element의 속성을 이용해서 Event가 발생되었을 때 수행되는 Handler를 지정한다.*

*Event가 발생하였을 때에는 Event Source가 직접 처리하지 않고, Event 속성을 통해 Handler를 이용해서 처리한다. 이를 deligation Model (위임 모델)이라고 한다.*

- this 

  - event handler 안에서 의미를 가지는 객체
  - event source에 대한 문서객체(document object를 지칭)

- on('click')

  ```html
  <ul>
      <li>아이유</li>
      <li>김연아</li>
      <li>홍길동</li>
  </ul>
  <input type="button" value="클릭" onclick="my_func()">
  ```

  ```javascript
  function my_func() {
      $('ul>li:eq(1)').on('click',function() {
          alert($(this).text())
      })
  }
  ```

  버튼을 클릭한 이후 my_func()가 실행된다.

  `ul>li:eq(1)`김연아를 찾는다. `on()` method로 event처리를 등록한다.

  김연아를 클릭할 때마다 this 의 text즉 김연아를 alert 한다.

- on('mouseenter'), on('mouseleave')

  마우스가 들어올때, 마우스가 나갈때 event가 발생한다.

  ```javascript
  function my_func() {
      $('ul>li').each(function(idx,item){
          $(item).on('mouseenter',function(){
              $(this).css('color','red')
          })
          $(item).on('mouseleave',function(){
              $(this).css('color','black')
          })
      })
  }
  ```

  마우스가 들어오면 글자색이 빨간색으로 변경되고, 마우스가 나가면 글자색이 검정색으로 변경된다.

  each() 메소드를 사용해 각 li 마다 event를 적용하였다.



#### Document Ready

이전 예제는 전부 함수 호출이 있을 때, 사용할 수 있는 예제였다.

함수 호출 없이 실행되자마자 실행되게 하는 방법이다.

- $(document).on('ready' function()){} - 원래 방법

  ```javascript
  $(document).on('ready',function(){
      $('ul>li').each(function(idx,item){
          $(item).on('mouseenter',function(){
              $(this).css('color','red')
          })
          $(item).on('mouseleave',function(){
              $(this).css('color','black')
          })
      })
  })
  ```

- $() - 축약 형태

  ```javascript
  $(function(){
      $('ul>li').each(function(idx,item){
          $(item).on('mouseenter',function(){
              $(this).css('color','red')
          })
          $(item).on('mouseleave',function(){
              $(this).css('color','black')
          })
      })
  })
  ```

  위의 코드가 길어서 축약 형태로 사용한다.



#### 참고

each [WEBCLUB](https://webclub.tistory.com/455)
