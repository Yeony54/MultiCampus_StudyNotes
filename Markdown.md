Markdown

## Markdown 문법 및 사용법

### 1. 제목(Header)

```
# This is h1
## This is h2
### This is h3
#### This is h4
##### This is h5
###### This is h6
```

### 2. 강조(Emphasis)

```
기울여 쓰기는 *별표* 또는 _언더바_를 사용
굵게 쓰기는 **별표 2개** 또는 __언더바 2개__를 사용
기울여 쓰기와 굵게 쓰기를 같이 쓰려면 **_언더바_와 별표 2개**를 같이 쓴다.
취소줄은 ~~물결 2개~~를 사용
밑줄 긋기는 <> 안에 'u'를 넣어 사용

!주의! 중간에 쓸 경우엔 띄어쓰기를 해야한다.
```

기울여 쓰기는 *별표* 또는 _언더바_를 사용
굵게 쓰기는 **별표 2개** 또는 __언더바 2개__를 사용
기울여 쓰기와 굵게 쓰기를 같이 쓰려면 **_언더바_와 별표 2개**를 같이 쓴다.
취소줄은 ~~물결 2개~~를 사용
밑줄 긋기는 <> 안에 'u'를 넣어 사용

### 3. 목록(List)

```
1. 순서만 쓰기
	1. 순서
	1. 순서
1. 순서 혼용
	- 순서 x
	* 순서 x
+ 순서 없이
	- 순서 x
		* 순서 x
```

1. 순서만 쓰기
	1. 순서
	1. 순서
1. 순서 혼용
	- 순서 x
	
	* 순서 x
+ 순서 없이
	- 순서 x
		* 순서 x

### 4. 링크(Links)

```
그냥 넣기 https://www.google.com/

[타이틀 예시](https://www.daum.net/)

[타이틀과 설명 있는 예시](https://www.naver.com/ "링크 설명 쓰세요")

[참조 링크 예시][1]

[내부 링크 예시][내부 링크]

참조와 내부 둘 다 본문을 쓴 뒤, 하단에 링크를 써둡니다. [링크 첨부]하는 방법 참 쉽죠?

[1]: https://www.google.com/
[내부 링크]: https://www.google.com/
[링크 첨부]: https://www.google.com/ "여기도 설명 가능"
```

### 5. 이미지

```
기본문법:![사진이름](사진경로)
```

### 6. 코드

````
```
블록(block) 코드 강조는 이 문장같이 `를 위, 아래로 3번 사용한다. 본문은 가운데에 위치.
```
또한 블록 코드는 특정 언어를 명시해주면, 문법에 대한 색이 바뀐다. (예시로 C언어 지정)

``` c
int val = 10;
printf(%s,"Hello, World!");
```

인라인(inline) 코드 강조는 `를 문장 앞뒤에 1번 사용해 속한 글의 색`을 바꾼다.
````



### 7. 표

##### 표 정렬

```
|왼쪽정렬|가운데정렬|오른쪽정렬|
|:------|:------:|-------:|
| 내용11 | 내용12 | 내용13 |
```

| 왼쪽정렬 | 가운데정렬 | 오른쪽정렬 |
| :------- | :--------: | ---------: |
| 내용11   |   내용12   |     내용13 |

```
| <center>Header1<center> | <center>Header2<center> | <center>Header3<center> |
|:------|:------:|-------:|
| **cell 1x1** | <center>cell 1X2 </center> | *cell 1x3* |
| **cell 2x1** | <center>cell 2X2 </center> | *cell 2x3* |
| **cell 3x1** | <center>cell 3X2 </center> | *cell 3x3* |
```

| <center>Header1<center> |  <center>Header2<center>   | <center>Header3<center> |
| :---------------------- | :------------------------: | ----------------------: |
| **cell 1x1**            | <center>cell 1X2 </center> |              *cell 1x3* |
| **cell 2x1**            | <center>cell 2X2 </center> |              *cell 2x3* |
| **cell 3x1**            | <center>cell 3X2 </center> |              *cell 3x3* |



### 8. 인용문(BlockQuote)

```
중첩 인용 사용.

>인용글 1단계
>>인용글 2단계
>>>인용글 3단계

인용문 내 줄 바꾸기는 '>' 사용,

중첩 인용 및 스타일 적용

>인용문
>>인용문
> #### 인용문 내부 헤더
```

>인용글 1단계
>>인용글 2단계
>>>인용글 3단계
>>>
>>>#### 인용문 내부 헤더 사용 가능



### 9. 수평선(Horizontal Rule)

```
---
하이퍼 이용

***
별표 이용

___
언더바 이용
```



### 10. 참고블록

```
[!NOTE]
[!TIP]
[!IMPORTANT]
[!CAUTION]
[!WARNING]
[!ADMINISTRATION]
[!AVAILABILITY]
[!PREREQUISITES]
```



#### 11. Typora 사진 git 연동

[TEAUK-WIKI : Typora 신기능 - 이미지 자동 업로드](https://taeuk-gang.github.io/wiki/Typora%20%EC%8B%A0%EA%B8%B0%EB%8A%A5%20-%20%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EC%9E%90%EB%8F%99%20%EC%97%85%EB%A1%9C%EB%93%9C/)

```json
{
    "picBed": {
      "current": "github",
      "github": {
        "repo": "Yeony54/MultiCampus_StudyNotes",
        "token": "{Token Key}",
        "path": "/img",
        "customUrl": "https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img",
        "branch": "main"
      }
    },
    "settings": {
      "showUpdateTip": true,
      "autoStart": true,
      "uploadNotification": true,
      "miniWindowOntop": true
    },
    "needReload": false,
    "picgoPlugins": {}
  }
```

Image Upload Error

```
[PicGo ERROR]: StatusCodeError: 401 - {"message":"Bad credentials","documentation_url":"https://docs.github.com/rest"}
```

Error Search

[FW개발자 - "Bad credentials" 메세지 발생시 조치방법](https://frankler.tistory.com/52)

- 새로운 Token Key를 만들었을 때 Git 과 GitHub의 설정이 다르다 - (나에겐 해당되지 않는 내용)

[Git 최초설정](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95) `~/.gitconfig`가 뭔지 몰라서 찾아봄

[sukkvon - personanl access key 설정](https://sukvvon.tistory.com/71)

- 결론 : Token Key가 expired되어 사용할 수 없는 상태였다.
  새로운 키를 만들어 하니까 Test Upload를 Error없이 수행



Image Test

![image-20220316155613451](https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img/img/image-20220316155613451.png)

이미지 복사, 붙여넣기 후 이미지업로드를 하게 되면 `https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img/img/image-20220316155248182.png` 처럼 생긴 링크가 생성되게 된다. 

git add, commit 후 push를 하려하면 pull을 하라는 메세지가 뜬다

이렇게 github으로 업로드를 하게 되면 img/ 폴더에 저장되게 된다.

**그런데도 자꾸 오류가 떴다.**

그런데 생각해보니 어차피 img/ 폴더에 저장이 될거면 upload가 필요할까라는 생각이 들었다....



자동저장 x + PicGo 설정







---



[ref-2](https://malgun-gothic.tistory.com/2)  [ref-2](https://steemit.com/kr/@antares007/-201787t14245290z)
