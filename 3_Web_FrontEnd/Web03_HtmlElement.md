Web

## Web Storm HTML Element

- Element
- Attribute
- Event

---



### HTML

#### 01. Element

##### br

한줄을 띄우는 Element

```html
<br>
```



##### a

앵커라고 부르며, 하이퍼링크(클릭 가능한 형태)를 만들어준다.

```HTML
<a href="http://www.naver.com">네이버로 가기</a>
```

- `href` : 연결할 주소 지정
- target : 링크를 클릭할 때 창을 어떻게 열지 설정
- title : 해당 링크에 마우스 커서를 올릴 때 도움말 설명을 설정



##### div, span

영역을 잡아주는 element

- `<div></div>` : block level element - 영역을 끝까지 잡아준다.
- `<span></span>` : inline element - 내용부분만 영역을 잡아준다.



##### img

그림을 표현할 때 사용하는 Element

```html
<img src="Img/penquin.jpg">
```



##### 사용자 정의 attribute

attribute는 Tag에 추가적인 정보를 포함시킬 때 사용한다.

`data-`를 붙여 사용자가 정의하는 attribute를 추가할 수 있다.

```html
<img src="Img/penquin.jpg" data-auther = "IU">
```



##### table

2차원 테이블형태로 데이터를 표현하기 위해 사용

```html
<table>
    <thead>
    <!-- 컬럼에 대한 정의 -->
        <th>이름</th>
        <th>학과</th>
        <th>주소</th>
    </thead>
    <tbody>
    <!-- 각 컬럼에 대한 데이터 -->
        <tr>
            <td>홍길동</td>
            <td>건축학과</td>
            <td>서울</td>
        </tr>
        <tr>
            <td>아이유</td>
            <td>영문과</td>
            <td>인천</td>
        </tr>
    </tbody>
</table>
```

`<thead>`와 `<tbody>`로 나누어지고, `<th>`와`<td>`로 이루어진다.



##### ul, li

순서없는 리스트를 표현하는 Element

```html
<ul>  <!-- Unordered List -->
    <li>서울</li>
    <li>인천</li>
    <li>대구</li>
</ul>
```

`<ul>`로 감싸고 `<li>`로 구성한다.



##### ol, li

순서가 있는 리스트를 표현하는 Element

```html
<ol>
    <li>아이유</li>
    <li>김연아</li>
    <li>홍길동</li>
</ol>
```

`<ol>`로 감싸고 `<li>`로 구성한다.



##### input

`type` 속성에 들어가는 값에 따라 생성 

- **text** : 일반 텍스트를 입력받을 수 있다.

  ```html
  <input type="text" value="입력하세요" disabled='disabled'>
  ```

  - disabled : 사용자의 선택을 막음, 비활성화

- **password** : 패스워드를 입력받을 수 있도록, 입력값이 화면에 보여지지 않는다.

- **submit** : `<from>` 태그 내에 입력된 데이터를 서버로 전달해 준다. 

- **button** : 버튼을 생성해준다.

  ```html
  <input type = "button" value = "버튼을 클릭하세요" onclick = "my_func()">
  ```

  - value : value에 지정된 값을 버튼에 표시해준다.
  - onclick : 버튼을 클릭하면 실행할 이벤트를 지정하기 위한 이벤트명

- **checkbox** : 체크박스 형태의 입력을 받을 수 있다.

  ```html
  <input type="checkbox"><span>아이유</span><br>
  <input type="checkbox"><span>김연아</span><br>
  <input type="checkbox"><span>홍길동</span><br>
  <input type="checkbox"><span>신사임당</span><br>
  ```

- **radio** : 라디오 버튼 형태의 입력을 받을 수 있다.

- **reset** : `<from>`태그 안의 사용자 입력을 초기화 한다.



##### select

셀렉트박스, 콤보박스, Pull-Down Menus라고 한다.

`<select>`태그와 `<option>`태그로 구성된다.

```html
<select name="person" onchange="my_func()">
    <option>선택하세요</option>
    <option value="아이유">아이유</option>
    <option value="김연아">김연아</option>
    <option value="홍길동">홍길동</option>
    <option value="신사임당">신사임당</option>
</select>
```

select의 속성

- name, value 

  위의 예제에서 name과 value는 사용자가 선택했을 때 변수와 값의 역할을 한다.

- selected : 기본값으로 선택되게하려면 사용

  ```html
  <option value="홍길동" selected="selected">홍길동</option>
  ```

- optgroup : 옵션에 카테고리를 생성

  ```html
  <select name="hobby">
       <option value="독서">독서</option>
       <optgroup label="스포츠">
          <option value="야구">야구</option>
          <option value="축구">축구</option>
       </optgroup>
       <option value="음악감상">음악감상</option>
  </select>
  ```

- multiple : 복수선택 가능 (단독사용)

  ```html
  <select name = "hobby" multiple>
  ```

- size : 보여지는 아이템의 개수를 조절 가능

  ```html
  <select name = "hobby" multiple size=8>
  ```

- required : 선택지에서 반드시 선택을 해야한다. (단독사용)

- disabled : 사용자의 선택을 막음, 비활성화 (단독사용)

  required와 disabled속성을 같이 사용하면 required 속성이 무시된다.







##### from, submit





#### 02. Attribute

##### id

```html
<li id="seoul">서울</li>
```

##### class

```html
<li id="seoul" class="myClass">서울</li>
```





#### 03. Event 예제

`on + event명` 을 이름으로 가지고 있고, event속성으로 사용되어 event처리할 때 쓴다.

event속성으로 처리할 때에는 순수 javascript event방식으로, this를 사용하지 못한다.

this를 사용하고 싶으면 jQuery Event 방식으로 처리해야한다.

##### onclick

클릭 이벤트가 있을 때, my_func()를 호출한다.

```html
<input type="checkbox"><span>아이유</span><br>
<input type="checkbox"><span>김연아</span><br>
<input type="checkbox"><span>홍길동</span><br>
<input type="checkbox"><span>신사임당</span><br>

<input type="button" value="클릭클릭" onclick="my_func()">
```

```javascript
function my_func() {
	console.log($('[type=checkbox]:checked + span').text())
}
```

속성선택자, checked된 span 형제의 text를 가져와 console에 출력

위의예제는 선택된 element를 따로 처리할 수 없어서 한번에 출력된다.

```javascript
function my_func() {
    $('[type=checkbox]:checked + span').each(
        function(idx, item){
        	console.log($(item).text())
    	})
}
```

each() 를 사용하여 선택된 element가 여러개이면, 그 각각에 대해서 each안에 있는 함수를 호출하게 된다.



##### ondblclick

더블클릭하면 작동한다.

```html
<li ondblclick="my_func2()">김연아</li>
```



##### onchange

값에 변경이 있을 때, my_func()를 호출한다.

```html
<select onchange="my_func()">
    <option>아이유</option>
    <option>김연아</option>
    <option>홍길동</option>
    <option>신사임당</option>
</select>

<div>선택한 사람 출력</div>
```

```javascript
function my_func() {
    let txt = $('select > option:selected').text()
    $('div').text(txt)
}
```

select의 자손 option의 속성이 selected인 값의 text를 불러온다.

div 태그를 선택하여 불러온값을 입력한다.

`$('div').text($('select > option:selected').text())`로 쓸 수 있다.

















### 참고

input : [hianna](https://hianna.tistory.com/307)

select : [homejjang](http://www.homejjang.com/05/select.php) - html 잘 정리되어있음