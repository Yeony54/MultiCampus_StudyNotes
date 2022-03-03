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
       - **model 다시 바꿔줘야함.**

3.  회원가입

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

   - 검색기능에서
   - 에러
     - all of us 검색 시 에러 : person은 genre_id가 없어서 에러













