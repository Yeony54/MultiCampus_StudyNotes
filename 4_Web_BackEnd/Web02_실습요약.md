Web BackEnd

## Web BackEnd Django 개요

- django project 만들기
- django project setting
- application - table 만들기
- application - url 변경
- application - view 생성



---



##### **django project 만들기**

anaconda prompt

python-django 파일로 이동

```django-admin startproject mysite```



##### **django project setting**

가상환경 새로 만들기

django 설치 : ```conda install django```

application 생성 : ```python manage.py startapp polls```

setting 설정 : 

- host : ```ALLOWED_HOSTS = ['127.0.0.1', 'localhost']```

- app 추가 : ```'polls.apps.PollsConfig'```

- db : 

  ```python
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': 'mysite0215_db',
          'USER': 'root',
          'PASSWORD': 'test1234',
          'HOST': '127.0.0.1',
          'PORT': '3306'
      }
  }
  ```

- 언어 : `TIME_ZONE = 'Asia/Seoul'`

mysql module : ```pip install mysqlclient```

workbench에 db 생성 : `Create DATABASE mysite0215_db;`

table 생성 : `python manage.py migrate`

관리자 생성 : `python manage.py createsuperuser`

프로젝트 기동 : `python manage.py runserver`



##### **application** - table 만들기

model.py :

- ```python
  from django.db import models
  
  # polls_question => db에 생성되는 table명
  class Question(models.Model):
      question_text = models.CharField(max_length=200)
      pub_date = models.DateTimeField()
  
      def __str__(self):
          return self.question_text
  
  class Choice(models.Model):
      choice_text = models.CharField(max_length=200)
      votes = models.IntegerField(default=0)
      question = models.ForeignKey(Question,
                                   on_delete=models.CASCADE)
  
      def __str__(self):
          return self.choice_text
  ```

- 명세서만들기 : python manage.py makemigrations
- 명세서 기반 table 만들기 : python manage.py migrate

admin.py : 

- class 등록하기

  ```python
  from django.contrib import admin
  from polls.models import Question, Choice
  
  admin.site.register(Question)
  admin.site.register(Choice)
  ```

admin 페이지에서 데이터 추가하기



##### **application** - url 변경

mysite/urls.py

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('polls/', include('polls.urls'))
]
```

polls/urls.py

```python
from django.urls import path, include
from polls import views

app_name = 'polls'

urlpatterns = [
    path('', views.index, name='index')
]
```



##### **application** - view 생성

view.py

- polls>templates>polls>index.html 생성

  ```python
  from django.shortcuts import render
  from polls.models import Question
  
  def index(request):
      # 데이터베이스에서 질문객체를 가져와요
      question_list = Question.objects.all().order_by('-pub_date')
      context = {
          "q_list": question_list
      }
  
      # render는 HttpResponse객체를 생성하는 함수
      return render(request, "polls/index.html", context)
  ```

index.html

- ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
      <ul>
          {% for question in q_list %}
          <li>{{ question.question_text }}</li>
          {% endfor %}
      </ul>
  </body>
  </html>
  ```



http://127.0.0.1:8000/polls/ 프로젝트 브라우저에서 실습한 내용이 나오는지 확인















