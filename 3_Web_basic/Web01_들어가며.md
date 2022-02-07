Web

## Web 시작

- Internet이란?
---
#### 용어

LAN(Local Area Network) : 지역 네트워크

Gate Way : Network 끼리 연결하여 큰 범위의 Network를 형성

WAN(Wide Area Network)

MAN(Metropolitan Area Network)

**Internet** : 전세계적으로 형성된 네트워크망

**Service** : Internet 위에서 동작하는 응용프로그램 (Email, Web, Torent 등)


#### Web 용어, 동작방법

- Web은 CS 구조를 가짐 (Client/Server구조)
- Web Client 세계 5대 브라우저 : Edge(MS), Chrome(Google), Safari(Apple), Opera(Opera), FireFox(Mozila)
- Web Server : apach(ASF), Nginx, IIS(MS), Oracle

Web상에서 Client와 Server는 Internet을 통해 정보를 주고받는다.

Stream이란 프로그램적으로 만들어진 가상의데이터 통로를 통해 데이터를 주고 받는다.

데이터를 주고 받기 위해서는 어디로 전달할지 주소 정보가 필요하다.

- **IP Address** : 컴퓨터의 논리적인 주소
- NIC (Network Interface Card) : IP주소가 부여되는 장비 
- **PORT** : IP주소를 보고 도착한 컴퓨터에서 프로그램을 찾기 위해 부여된 번호
- DNS (Domain Name Server) : 외우기 힘든 IP Address를 대신하기위한 Domain name을 저장하는 Server
    - 127.0.0.1 : local host
    - 122.37.64.5 : www.naver.com
    - 231.12.118.10 : www.daum.net
- MAC Address : 기기에 고유하게 부여된 물리적인 주소.
IP Address는 논리적인 주소이기 때문에 변경될 수 있다. 실제로 컴퓨터에 찾아가기 위해서는 MAC Address로 변경해야 한다.
- **HTTP** (Hyper Text Transfer Protocol) : Web 통신규약

주소정보를 알아낸 후 Client가 Browser를 통해 Server에 `request`를 요청한다. 


```
https:// (IP주소 Domain name):(PortNumber)/(원하는 작업)
```

Server는 Client의 request를 해석, 처리한 결과를 `response`로 답해준다.

Client는 Server가 전달해준 response를 해석하여 `rendering`하여 Browser에 그린다.

예를들어 `www.naver.com + enter` 를 하게 되면 위의 과정을 수행한 후 response를 redering 하여 네이버의 시작화면이 나타나게 되는것이다.

#### Web 종류

Web Server는 Client의 요청에 따라 원하는 파일을 response로 응답하여 준다.
 
이때 response로 보내줄 resorce가 정적인가, 동적인가에 따라 web종류가 다르다.

- 정적 Web (Static Web) : Web Client가 Web server 쪽에 이미 존재하는 resorce를 요청하는 작업
- 동적 Web (Dynamic Web) : Web Client가 Web server 쪽에 존재하는 Program을 실행시켜 response를 생성하고 결과를 요청하는 작업


#### Web 동작하기

- HTML
    - Domtree (Document Object Model Tree)
- CSS
- JavaScript : HTML, CSS로 browser에 rendering된 환경을 동적으로 제어
    - 문서객체 (Document Object) : Comoponent를 javascript 객체화
- jQuery : 모든 browser에서 동작하는 Client javascript library
    - selector
    - method
    - event : 사용자가 하는 행위를 처리
- CDN (Content Delivery Network) : jQuery를 HTML Tag를 이용해서 library를 동적으로 download해서 사용하는 방식
- Ajax (Asyncronous JavaScript And XML) : 동적 Web을 실행시킬 때 Web Server에 부하가 가지 않도록 WAS로 따로 분리하여 프로그램을 처리
    - WAS (Web Application Server) : Web application 동작 수행
- Round-Trip 방식의 Web : response를 받을 때 마다 새로 페이지를 재구성 - page refresh 발생
- SPA (Single Page Application) : Ajax의 통신방법으로, 처음 페이지를 구성한 이후로는 데이터만 받아 화면에 데이터를 적용하는 방식을 사용하여 page refresh를 방지

#### 데이터 전송방식

- CSV (common seperated value)
    - ex) `아이유, 20, 서울, 김연아, 30, 대구`
    - comma로 구분되어 나열된 데이터
    - 장점 : redundent(부가적인) 데이터가 적어서 많은양의 데이터 전송에 적합
    - 단점 : Data parser를 직접 구현해야 한다. 유지보수가 어렵다.
    - 데이터 길이가 짧아 보통 대용량 데이터를 보내는 용도로 사용
- XML (Extended Markup Language) 
    - ex) `<name>아이유</name><age>20</age><address>서울</address>`
    - 장점 : parser가 있어 유지보수 용이하다. Tag를 통해 데이터 구조화가 가능하다.
    - 단점 : 실제 데이터 보다 redudent 데이터가 더 많다.
- JSON (JavaScript Object Notion)
    - ex) `{name:"아이유", age:20, address:"서울"}`
    - 장점 : 유지보수 용이, 데이터구조화 가능, 길이도 짧음