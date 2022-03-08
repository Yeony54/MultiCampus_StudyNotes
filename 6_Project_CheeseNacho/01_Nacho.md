Mproject_Nacho_note

# Nacho Project



project file 생성

anaconda prompt > cd 로 file 변경 > startproject 명령어

```bash
$ django-admin startproject cndb
```



application file 생성

```bash
> python manage.py startapp entmt_info
> python manage.py startapp entmt_manage
> python manage.py startapp users
```



setting 설정

```python
ALLOWED_HOSTS = ['127.0.0.1', 'localhost']

INSTALLED_APPS = [
    ...,
    'entmt_info.apps.EntmtInfoConfig',
    'users.apps.UsersConfig',
    'entmt_manage.apps.EntmtManageConfig',
    'bootstrap4',]

TEMPLATES = [
    {
        ...
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        ...
    },
]

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'cheese_db',
        'USER': 'root',
        'PASSWORD': '...',
        'HOST': '127.0.0.1',
        'PORT': '3306'
    }
}

TIME_ZONE = 'Asia/Seoul'

STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

```



필요한 기본 폴더, 파일 추가



favicon.ico 404 Not Found Error 방지

```html
<link rel="icon" href="data:;base64,iVBORw0KGgo=">
```



DB 에 저장하기 위한 모델 class 생성

- 받을 데이터의 타입에 따라 만들어주어야 한다.
- _id 형태 안붙게 하는법 : https://www.hides.kr/843



---



1. API로 데이터 들어오는지 확인
   - 사용한 API : [tmdb](https://api.themoviedb.org)

2. DB에 저장해보기
   - id를 사용해서 제목, poster, 등 저장 해봄 : ei_import2
     - urllib : https://dololak.tistory.com/254
     - urllib는 앞에 https 가 다 있어야 가능한가?
     - querystring : 처음에만 ?이고 이어지는것은 &이다.
     
   - genre 가져와서 DB에 저장하기 : ei_import3
     - Python에서 request 보내는 방식 : https://my-repo.tistory.com/33
     - python에서 genre 받아서 DB에 있는지 확인하고 저장
       - 이전 포스터 이름 저장할때 중복저장되지 않은걸 보면, 그냥 알아서 되는것 같다.
     - Python 에서 DB 조회 방법 : [https://ssungkang.tistory.com](https://ssungkang.tistory.com/entry/Django-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%A1%B0%ED%9A%8C-queryset)
     - movies, tv genre 받는 url이 달라서 둘다 처리해줌
     - 완료
     
   - ei_import2 에서 했던 내용이랑 장르도 같이 해봄 : ei_import4

     - python dictionary : https://wikidocs.net/16043

     - 에러짜증난다

       ValueError: Cannot assign "634649": "Mgenres.mg_movie" must be a "Movies" instance.

     - 에러는 해결 : [https://velog.io/@jake93](https://velog.io/@jake93/Error-%EA%B8%B8%EC%9E%A1%EC%9D%B4-ValueError-Cannot-assign-must-be-a-instance)

       예습했을때랑 똑같은방법으로 했는데 왜 안되는지 모르겠다.

     - 문제1 : 한개의 model에 한개의 genre만 저장된다 ㅠㅠ

       - 빈 model 객체를 새로 생성해주어서 해결했다.

     - 문제2 : 중복생성이 된다.

       - 이건 primary key를 movie, genre로 묶어서 만들어줘야하나?
         - Django 에서 복합키 못한다 : [https://woungsub1234.gitbook.io/](https://woungsub1234.gitbook.io/today-i-learned/v/main/django-1/django-model)
       - Q를 import하여 복합 조건에 맞는 데이터를 찾아서 해결

   - csv 불러와서 저장

     - ascii encoding Error : [https://frhyme.github.io](https://frhyme.github.io/python-basic/py_eff_byte_order_mark/)
       - 파일 encoding 방식을 utf-8(BOM) 에서 utf-8로 바꿔서 하니 됐다.
     - with open 사용 : https://twpower.github.io/17-with-usage-in-python
     - 문제1 : poster path가 null 값인 것이 있다. 
       - **model 다시 바꿔주거나, null일 때 기본경로 설정해줘야할듯**

3. 회원가입

   - 실습에서 했던것과 다른 방식으로 회원가입을 만들었음
   - 이미지 입력은 아직 잘 안됌
   - 비밀번호 변경 참고 링크
     - https://ghqls0210.tistory.com/48

4. 검색기능

   - ~~참고사이트 : [https://velog.io/@mongle](https://velog.io/@mongle/Django-Web-Project-%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%804-%EA%B2%80%EC%83%89-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)~~
     - 참고하려고 했는데, DB를 사용한거라서 패쓰
   - 원래 했던 방식으로 만들어보았음
     - 검색을 누르면 text 창에 있는 data를 view 함수에 전달
     - 전달된 data를 keyword로 searchAPI를 한번 하고 rendering
   - 문제 1: 언어를 ko 기준으로 했는데, 한글 검색이 안됌
     - UnicodeEncodeError: 'ascii' codec can't encode characters in position 106-107: ordinal not in range(128)
     - qoute로 해결 : https://hengbokhan.tistory.com/25
   - 검색 결과를 누르면 detail 페이지로 가도록 설정
     - 

5. 이미지 업로드

   - 참고사이트 : 
     - 잘설명되어있음 :  ~~[https://codedec.com/](https://codedec.com/tutorials/upload-and-display-image-in-django/)~~ 저장하는방법 말고, 바로 가져오는 방법을 찾을것임
     - img 다운로드 종류별로 설명 : https://soyoung-new-challenge.tistory.com/92
   - API 방식이 아닌 html에서 직접 가져오는 방식으로 불러오는게 더 빨랐음

6. 디테일 페이지 만들기

   - 검색기능에서 항목 클릭 시 디테일 함수로 전송, id, media_type을 보냄
   - API에 검색해서 항목을 detail 화면에 표시
   - 에러
     - **all of us 검색 시 에러 : person은 genre_id가 없어서 에러**
     - 다른 media type 처리 필요

7. 좋아요 기능 구상

   - 디테일 페이지에 테스트 버튼을 만들어서 시도

     - 버튼을 누르면, view에서 Movie, Sereise객체와 user에 해당하는 Mlike, Slike를 찾는다.
     - Mlike, Slike에 포함되지 않았으면 포함시키고, like_count+=1
       Mlike, Slike에 포함되어 있으면 삭제하고, like_count-=1

   - 지금 model은 둘다 Forienkey로 만들어져있다.

     - 단점 : db에 저장된 movie만 좋아요 등록 가능
     - 그래서 그냥 일반키(movie_id)로 등록하게 되면, 단점이 뭐가 있을까...
       - 단점 : movie가 자기 like개수 모름 -> 그건 뭐 like_count로 가능
     - 생각해보니까 like_count도 db에 저장된 객체만 할 수 있음
       - db에 저장되지 않은 객체는 like_count를 하지 못함
       - **detail로 들어갈 때, DB에 없으면 추가하는 기능을 해야할듯함**

   - ForienKey로 저장하고 개수셀 때, count로 세면 될것같다. 

     - F() 객체로 더하기를 할 수 있는 기능도 있다고 한다. 

       <-이방식이 처리는빠를듯한데

     - .filter().exists() / .filter().count() : https://velog.io/@fcfargo/Django-Repository

   - code 수정

     1. view의 detail 함수에서 detail.html로 넘어올때, like 변수 전송
     
     2. detail.html에 like관련 항목을 작성, 버튼 생성, 변수상태에 따라 style 변경
     
     3. jQuery 기본문법 와 좋아 : https://soft91.tistory.com/9
     
        jQuery로 태그 가져와서 확인할까하다가 고민중

8. 좋아요 기능 구현

  - is_authenticated 로 인증되었는지 확인
  - results_id와 media_type을 통해 Like 기능 수행
    - Like 리스트에 있으면 삭제, 없으면 추가
  - 기능 수행 후, redirect로 다시 detail 페이지 표출
    - redirect 참고 : https://velog.io/@ready2start/Django-redirect
      - **form에 대한 내용도 있다.** form을 저장해서 redirect하면 저장한 form을 다시 redirect한 페이지에 표시한다는 내용같음
    - redirect 참고 : [https://velog.io/@rosewwross](https://velog.io/@rosewwross/Django-render-%EC%99%80-redirect%EC%9D%98-%EC%B0%A8%EC%9D%B4)
      - 이 블로그를 보다가 문득 생각이 들어서 redirect를 성공했다.
  - 클릭하면 좋아요 되게 완료~
  - 단점 : 다시 페이지로 redirect 해주는거라서 뒤로가기해보면 페이지가 두번 나오는것을 확인할 수 있음.... 이런건 어떻게 해? ㅠㅠ 새로고침은 못하나
    - **결국 Ajax활용해야할듯 ㅠㅠ** : https://wayhome25.github.io/django/2017/06/25/django-ajax-like-button/

9. 별점 기능 만들기

   - 별점 등록
   - 별점 통계

10. 장르 선택 옵션 구현

   - users에 장르선택 옵션 구현

11. DB 업로드 수정

    - series에서 path=Null일때 오류

      - https://wayhome25.github.io/django/2017/09/23/django-blank-null/

        CharField와 TextField에서 null=True라고 하면, 빈문자열과 null의 두가지의 경우가 존재하기 때문에 null=True라고 해선 안된다고 되어있다.

        하지만 API의 경우 빈 문자열이 아닌 null로 다루고 있기 때문에 null=True로 해서 해본다. 

      - 155082 : 얘가 말썽임
        poster path도 없고, 첫방영일도 없음 다 null=True로 해서 진행하겠음

      - 해결완료

    - detail 불러올 때, DB에 있는지 확인하고 없으면 넣어주는거 추가

12. 마이페이지

    - bbs의 comment에서는 

      <QuerySet [<Comment: 너무비싸요>, <Comment: 너무비싸요>, <Comment: 너무비싸요>]>

      의 형식으로 context에 담겨졌다.
      
    - 다시하니까 성공했다

13. url 정리

    - 장르 import
      - https://api.themoviedb.org/3/genre/movie/list?api_key=(api_key)
      - https://api.themoviedb.org/3/genre/tv/list?api_key=(api_key)
    - movie import
      - https://api.themoviedb.org/3/movie/(movie_id)?api_key=(api_key)
    - series import
      - https://api.themoviedb.org/3/tv/(series_id)?api_key=(api_key)
    - detail
      - https://api.themoviedb.org/3/movie/(movie_id)?api_key=(api_key)
      - https://api.themoviedb.org/3/tv/(series_id)?api_key=(api_key)
    - search
      - https://api.themoviedb.org/3/search/multi?language=ko&page=1&include_adult=false?api_key=(api_key)&query=quote(search_word)
    - 비슷한 코드를 묶으려고함
      - 위의 4개를 같은코드로 묶고, search 까지 2개의 코드로 만들까,,,
      - 코드 묶음 완료

14. 수정할것 

    1. entmt_info/models.py : m_likeCount 필요없음
    2. default 이미지 나오게 수정 : 수정함
       - upload_to 때문에 앞에 media/가 붙어서 그랬던것같음,,, : 내일확인
       - 완료

15. 템플릿 필요한 소스

    - 메인페이지, 검색결과페이지, 디테일페이지
    - 로그인, 회원가입, 마이페이지, 장르선택페이지, 비밀번호변경, 업데이트

16. 로딩페이지

    -  [로딩페이지 영상](https://www.google.com/search?q=How+to+add+loading+page&sa=X&ved=2ahUKEwiOyN3J3rP2AhXFrlYBHTJSBeMQ1QJ6BAgxEAE&biw=1080&bih=828&dpr=1#kpvalbx=_mNclYrqnEJvf2roP-KOjoA421)
    - 로딩페이지 하려면 뭐 웹사이트에 넣어놓고 그거 쓴다는것같은데
    - loading.io

17. 댓글 나머지 구현

    - 한사람당 댓글한개 구현
    - 밑에는 다른사람들의 댓글들 나오도록 구현
    - 별점이 점수가 아닌 별로 보이도록 구현
    - 수정, 삭제 구현



---



Template 적용

1. base.html 만들기
2. 회원가입, 로그인 팝업으로 가능하게 만들기
3. 검색 -> result.html
4. detail.html
5. mypage













