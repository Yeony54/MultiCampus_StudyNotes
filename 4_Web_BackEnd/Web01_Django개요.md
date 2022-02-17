Web BackEnd

## Web BackEnd Django 개요

- Web Server 역사
- Framework란?
- Django 란?
- Django 동작 방법
- Django 프로젝트 생성

---



#### Web Server 역사

Web Server는 이전 FrontEnd 에서도 다루었었다.

1. Static Web

   Web Client 와 Web Server가 통신할 때 HTTP/HTTPS 규약을 따른다.

2. Dynamic Web

   Web Server가 프로그램을 설치한 후 직접 호출한다.

   Web Server와 CGI Program 간 통신할 때 CGI 규약을 따른다.

3. WAS

   Dynamic Web에서 Web Server가 호출하고 실행하니 부하가 발생한다.

   Web Application Server를 두어 Web Server가 직접 하지 않고, WAS에 위임

   WAS가 프로그램을 실행하고, response를 넘기는 일을 한다.

4. WSGI (python)

   WSGI module에서 호출하여 WSGI Process가 Framework로 실행

   Framework 안에 Python module이 위치한다.



#### Framework

Library vs Framework

- Library

  어떤 특별한 일을 수행하게 해주는 도구(함수, 클래스)

  기능을 제공하지만, 실질적인 작업은 알고리즘 작성이 필요하다

- Framework

  도구를 포함해서, 프로그램이 동작하는 규칙, 절치가 정해져 있다.(Library+방식)

  전체 시스템이 도는것은 일정하다. 그래서 유지보수가 쉽다.

  전체 시스템이 도는 방식을 숙지해야 한다.

  ex) react, vue, Angular



Django

- Python으로 만들어진 무료 Web application Framework
- Web application을 개발할 때 기본적으로 구현하는 부분을 Django가 쉽게 이용할 수 있는 코드를 제공한다.



MVC pattern

- Design Pattern : 42개의 패턴 중 17개의 대표적인 패턴이 있고, 그중 6개가 자주 쓰인다.
- 가장 많이 사용하는 패턴은 MVC pattern 이다.
  - Model - View - Controller
- 프로그램을 담당하는 기능에 따라 나누어서 짜는 특징이 있다.
- Django는 MVC 의 변형인 MVT 패턴을 이용한다.



MV



