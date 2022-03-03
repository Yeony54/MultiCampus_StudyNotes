Mproject_Project_BBS

# BBS Project



```
인터페이스 개발 수행평가 내용

다음의 항목으로 수행평가 작성한 코드를 zip으로 압축해서  
comment파일(MS word파일)과 함께 e-ncs 사이트에 
수행평가 부분에 upload합니다.

제출기한 : 프로젝트 마감일까지(3월 14일)

수행평가 내용은 수업에서 진행했던 Django 게시판 입니다.
각자가 수행할 수 있는 부분까지 작성하셔서 제출하시면 됩니다.
------------------------------------
1단계 : 게시판 글 리스트 출력
2단계 : 1단계 + 글 상세보기, 좋아요, 삭제기능
3단계 : 2단계 + AJAX 댓글 리스트보기, 댓글 등록, 댓글 삭제기능
4단계 : 3단계 + 게시글 수정기능 구현
5단계 : 4단계 + 
          회원가입기능 및 로그인 기능
          로그인한 회원만 게시판 이용가능하게 구현
6단계 : 5단계 + 
          로그인한 회원이 게시판에 글을 쓸때 자신의 이름이 작성자명에
          자동으로 출력되게 구현
          자신이 작성한 글만 수정, 삭제가 가능하게 하고
          자신의 작성한 글은 좋아요를 할 수 없도록 구현
7단계 : 6단계 + 댓글 역시 자신의 아이디 자동입력
          자신의 댓글만 삭제가능하고 다른 사람의 댓글은 삭제할 수 없도록
          구현
----------------------------------------
이상의 내용입니다. 

우리가 수업 중 진행한 내용이 다수이기 때문에 복습을 겸한다 
생각하고 구현해서 제출하시면 됩니다. 

comment파일(MS word파일)은 실행한 화면에 대한 
화면캡쳐(제가 확인할 수 있도록)를 꼭!! 넣어주세요!!
또한 어느단계까지 구현했는지에 대한 내용과 기타 저에게 알려야할 
사항이 있으면 포함시켜 주세요!
```



Project File 생성

anaconda prompt > cd 로 file 변경 > startproject 명령어

```bash
$ django-admin startproject lecture
```



application file 생성

```bash
> python manage.py startapp bbs
> python manage.py startapp users
```



settings.py 수정

```bash
INSTALLED_APPS = [
    ...
    'bbs.apps.BbsConfig',
    'users.apps.UsersConfig',
    'bootstrap4',
]

ALLOWED_HOSTS = ['127.0.0.1', 'localhost']

AUTH_USER_MODEL = 'users.Member'

TEMPLATES = [
		...
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
		...
]

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'lecture0220_db',
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



기본적인 셋팅 

urls.py 수정, 디렉토리 추가, html 생성



---



1. index.html 홈페이지 수정

   - 홈페이지 구성, bootstrap을 사용해서 간단하게 만들기
   - 게시판 입장 버튼을 누르면 list.html로 가도록 구성

2. list.html 게시판 리스트 생성

   - 리스트 나열
     - view.py의 b_list() 함수를 실행
       - 만약 인증된 회원이면, Board model로 생성된 객체들을 id의 역순으로 나열하여 context에 포함하여 rendering 한다.
   - 리스트 항목 클릭 시 detail.html로 가도록 구성

3. create.html 새글작성

   - 게시판 리스트 list.html에서 새글작성 버튼을 누르면, b_create() 함수 실행

     - 새글 작성 폼 생성 : 빈 form 객체를 rendering 해준다.

       - 나중에 GET 방식으로 바꾸어 POST 일때와 다른 동작을 하게 수정

     - create.html을 작성, 등록버튼을 submit으로 구성
       submit 버튼을 생성할때에는 csrf_token을 사용해야한다.

       ```html
       {% csrf_token %} 
       ```

     - POST 방식으로 호출하게 되면, BoardForm에 있는 양식을 바탕으로 객체를 생성하게 된다.

4. detail.html 생성

   - 상세보기 구성

5. 댓글 입력 구현

   - detial.html에 label 태그를 작성하여 이름, 내용을 입력한 후 , onclick 명령
   - ajax를 사용해 html의 label에 작성된 데이터를 view에 전송
   - view에서 Comment() 객체를 생성하여 전송된 데이터를 삽입, 성공 return
   - ajax가 success 일 시 다시 detail 화면을 갱신

6. 댓글 삭제 구현

   - 댓글 구성 시, 생성한 댓글 id를 사용한다.
   - 삭제버튼을 누르면, ajax를 호출
   - 댓글 id를 data에 담아 view에 보낸다.
   - view에서 해당 댓글 id를 포함한 Comment를 찾아 delete() 후 성공 return
   - ajax가 success 일 시 다시 detail 갱신

7. 좋아요 버튼 구현

8. 게시글 수정 구현

9. 로그인 기능 구현

   - 로그인 model.py 생성
   - 로그인 화면 구성
   - 로그인 form.py 생성, url 구성
   - users/templates/users 안에 login.html 생성, bootstrap으로 구성

10. 회원가입 기능 구현

    - 참고 : https://eveningdev.tistory.com/20

    - 에러 : Manager isn't available; 'auth.User' has been swapped for 'users.Member'

      - ```ini
        AUTH_USER_MODEL = "pet.Person"
        ```

        아까 settings.py에 선언했던걸로 객체를 만들어주어야 한다.

    - 회원가입 구현 성공

11. 새글 작성 시, 자기의 이름이 자동등록되도록

    - 참고 : https://iamthejiheee.tistory.com/59

    - Error : 'BoardForm' object has no attribute 'cleaned_data'

      - [https://stackoverflow.com/](https://stackoverflow.com/questions/4308527/django-model-form-object-has-no-attribute-cleaned-data) is_valid() 후에 나와야 사용가능

    - **Forien Key 작성할 시 주의할 것**

      ```
      b_author_id=user.id
      b_author=user
      ```

      어디는 되고, 어디는 안되는줄 알았는데,,, 

      - model을 구성한 column을 Forien Key로 생성하게 되면 자동으로 _id 가 붙어서 생성된다.

      - 만약 TestModel class의 column명을 test로 하였을 때를 가정하면

        test=(TestModel 형식)

        test_id=(TestModel.id 형식)

12. 자신의 글만 삭제

    -  참고 : [https://wayhome25.github.io/](https://wayhome25.github.io/django/2017/03/01/django-99-my-first-project-3/) 
      - 자신의 글에만 삭제버튼이 보이도록