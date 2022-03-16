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



### 11. Typora 사진 git 연동

~~[TEAUK-WIKI : Typora 신기능 - 이미지 자동 업로드](https://taeuk-gang.github.io/wiki/Typora%20%EC%8B%A0%EA%B8%B0%EB%8A%A5%20-%20%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EC%9E%90%EB%8F%99%20%EC%97%85%EB%A1%9C%EB%93%9C/)~~ : 잘못된 경로설정 정보... 😂 고생했다 나자신

PicGo json 파일 설정

```json
{
    "picBed": {
      "current": "github",
      "github": {
        "repo": "{GitID}/{Repository명}",
        "token": "{Token Key}",
        "path": "/{저장하고 싶은 경로}",
        "customUrl": "https://raw.githubusercontent.com/{GitID}/{Repository명}/{branch명}",
        "branch": "{branch}"
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

Git Token 👉 https://github.com/settings/tokens

Generate new token > repo, workflow, gist 선택하고 만들기 선택

생성된 token은 다시 열람할 수 없으니 복사해서 가지고 있던지, 아님 새로생성하면 된다.

---

**-고생했던 Error-**

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
  새로운 키를 만들어 하니까 Test Upload를 Error없이 수행할 수 있었다.

**-Image Test-**

1. 자동저장o + PicGo 설정o

   ![image-20220316155613451](https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img/img/image-20220316155613451.png)

   이미지 복사, 붙여넣기 후 이미지업로드를 하게 되면 `https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img/img/image-20220316155248182.png` 처럼 생긴 링크가 생성되게 된다. 

   git add, commit 후 push를 하려하면 pull을 하라는 메세지가 뜬다.

   그래서 pull해주고 push를 완료하고 git 페이지를 보면 upload는 되었지만, img는 뜨지 않는다.

   - 그런데 생각해보니 어차피 git에서 img/ 폴더에 저장이 될거면 upload가 필요할까라는 생각이 들었다....
   - 그리고 git에서 업로드한것과 내가 local에저장된것이 push되면서 엇갈리는것이 아닐까라는 생각이 들었다.
   - githubuser 링크를 보면 내가 설정한 링크와 다르게 /img가 두번 들어가 있는데 이거 때문에 오류가 생겼던 것일까 생각도 잠~ 깐 들었지만, path에 맞게 잘 저장 되는것을 보아 그건 또 아닌것같기도하고,,,,
     - 다른 블로그에서는 마지막이 경로가아니고 branch명이라고 되어있는곳도 있었다.

2. 자동저장 x + PicGo 설정

   ![image-20220316155956299](https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/img/img/image-20220316155956299.png)

   역시 pull 메세지가 떠서 pull을 하고 push를 완료해 주었다.

   **이미지는 여전히 뜨지 않는다.**

3. 자동저장o + PicGo설정 x

   ![image-20220316160626489](img/image-20220316160626489.png)

   이렇게 하니까 그냥 된다. 왜 PicGo를 쓰는지 모르겠다.

   PicGo 없이 자동저장되도록 경로를 설정하고, 경로가 설정된 곳의 링크에서 사진을 가져온다.

   **해결**

4. 위에서 생각했던 안되는 이유중에 경로 설정을 다시 해주는것 test

   Test img는 잘 올라간다.

   ![image-20220316162538155](https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/main/img/image-20220316162538155.png)

   `https://raw.githubusercontent.com/Yeony54/MultiCampus_StudyNotes/main/img/image-20220316162538155.png`으로 경로가 설정되니 잘 업로드 되어서 저장 되었다. 화난다. 👿

   어쨋든 5번의 이유가 아니면 쓸 이유가 없어서 일단은 그냥 3번방식으로 쓸 것 같다.

   매번 업로드 하는것도 귀찮으니까 말이다. 😉

5. 내가 생각하는 PicGo를 사용하는 이유

   PicGo를 사용하면 Git을 통해 자동으로 업로드가 될 수 있도록한다. 

   어차피 Git에 올라가고, pull을 해서 받아야 하면 왜 Git에 올리는 건가 생각을 했는데, 

   **만약 업로드하는 Git repository가 현재 내 문서가 있는 repository가 아닌 다른 repository이고, 여기서 사진을 가져올 수 있다면 아주 편리한 기능일 것 같다.**

   **게다가, 위에서 설정했던 json 코드를 보면 branch설정 칸이 있는데, 여기에 main이 아닌 다른 branch으로 설정하게 되면 내 main에 보이지 않게 관리할 수도 있을것 같다.**

   하지만 나는 감자기 때문에 그냥 main에 저장해서 쉽게쉽게 할것이다 😀



---



[ref-2](https://malgun-gothic.tistory.com/2)  [ref-2](https://steemit.com/kr/@antares007/-201787t14245290z)
