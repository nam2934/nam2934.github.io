---
title:  "[Spring] Web Server와 WAS(Web Application Server)"
excerpt: ""

categories:
  - Spring
tags:
  - [spring, java]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2024-01-19
last_modified_at: 2024-01-21
---

Spring 공부를 하던 중, Spring은 Tomcat이라는 WAS(Web Application Server) 위에서 동작한다는 사실을 알게 되었다.<br>
내가 Django 프로젝트를 할 때 알던 Web Server는 Nginx 인데, 'Nginx와 Tomcat 둘다 Web Server 아니야?', 'Web Server와 WAS는 다른건가?', '둘이 어떤 역할을 하는거지?'와 같은 생각이 들고, 알고 사용해야 그 기술 스택이 내 것이 된다는 생각에 이 내용에 대해 자세히 알아보고자 한다.<br>

## Web Server
Web Server의 정의를 찾아보면 여러가지 자료가 나온다.<br>

### Wikipedia
> A web server is computer software and underlying hardware that accepts requests via HTTP (the network protocol created to distribute web content) or its secure variant HTTPS.<br>

즉, Web Server는 HTTP또는 HTTPS를 통해 request를 수락하는 컴퓨터 소프트웨어 및 하드웨어이다.<br>
이 설명만 보고는 무엇인지 감이 오질 않는다. 다음 설명을 보자<br>

### MDN Web Docs
> The term web server can refer to hardware or software, or both of them working together.<br>
- Hardware Side<br>
  - A web server is a computer that stores web server software and a website's component files (for example, HTML documents, images, CSS stylesheets, and JavaScript files)<br>
  - A web server connects to the Internet and supports physical data interchange with other devices connected to the web.<br>
- Software Side<br>
  - A web server includes several parts that control how web users access hosted files.<br>
  - At a minimum, this is an **HTTP server**<br>
- What is HTTP server?
  - An HTTP server is software that understands URLs (web addresses) and HTTP (the protocol your browser uses to view webpages)<br>
  - An HTTP server can be accessed through the domain names of the websites it stores, and it delivers the content of these hosted websites to the end user's device.<br>

Web Server software와 website의 컴포넌트 파일들이 저장되어있는 물리적인 곳을 Web Server의 hardware side라고 표현한다.<br>
즉, 이는 흔히 사용하는 데스크탑일수도 있고, 클라우드 서버일 수도 있는 것이다.<br>
여기서 중요한것은 이 hardware는 internet과 연결되어 있고, 다른 device들과 물리적인 데이터 교환을 할 수 있어야 한다.<br>
<br>
Software 측면에서 web server는 web user가 hosted files에 access하는 여러 부분들을 포함하고 있는 것이다.<br>
웹 브라우저(보통 client라고 표현)에서 HTTP를 통해 hardware에 저장된 파일들을 접근하기 위해 일련의 소프트웨어(HTTP Server)를 포함하는 것이 Web Server인 것이다.<br>

아래 그림과 같이 이해해보자.
<p style="text-align: center;">
  <img width="500" alt="스크린샷 2024-01-19 오후 10 26 06" src="https://github.com/nam2934/nam2934.github.io/assets/41818011/55a55c00-9c7c-42bf-8f32-7501ae396594">
</p>
<br>
1. Web Browser에서 web server에 호스트 되고 있는 파일중 필요한 파일이 있으면 HTTP를 통해 file request를 보낸다.<br>
2. HTTP Server가 이 request를 받으면 필요한 파일을 찾고, HTTP를 통해 browser로 이 파일을 보낸다.<br>

이 사이트에서의 Web Server의 정의와 동작을 요약하자면 다음과 같다.<br>
- Web Server는 하드웨어와 소프트웨어 측면으로 나뉜다.<br>
  - 하드웨어 측면에서는 웹서버 소프트웨어와 파일들을 저장하는 일종의 컴퓨터이다.<br>
  - 소프트웨어 측면에서는 Browser가 보낸 request를 받아 처리하는 역할을 하는데, 이 역할은 HTTP Server가 수행한다.<br>
HTTP Server는 Browser가 HTTP request를 보내면 이를 받고, 필요한 파일들을 Web Server hardware에서 찾아 이를 Browser로 보내는 역할을 하는 것이다.<br>

이 모든 내용을 통합하여 포괄적으로 정리하면 다음과 같이 정의할 수 있다.
> Web Server란 Web Browser의 HTTP request에 대한 response로 HTML, file, image, video와 같은 **static content**를 제공하는 server이다.<br>

여기까지는 가장 기초적인 Web Server의 개념이다.<br>

## WAS(Web Application Server) or Application Server
한국에서는 WAS로 많이 불리지만, 구글에 Web Application Server로 검색해보면 영어권에서는 Application Server로 용어를 사용하는 것을 볼 수 있다.<br>
이 포스팅에서는 Web Application Server로 term을 통일하도록 하겠다.<br>

### Wikipedia
> An application server is a server that hosts applications or software that delivers a business application through a communication protocol.<br>

WAS는 communication protocol을 통해 business application을 제공하는 소프트웨어이다.<br>
Web Server에서는 HTTP로 protocol이 국한되었지만, **WAS에서는 다른 protocol도 사용**한다.<br>
역시나 Wikipedia 설명은 불친절하다. 다음 설명을 보자.<br>

### IBM Docs
> An application server typically can deliver web content too, but its primary job is to enable interaction between end-user clients and server-side application code—the code representing what is often called business logic—to generate and deliver dynamic content, such as transaction results, decision support, or real-time analytics

WAS는 web content도 제공하지만, 주요 작업은 client와 application code(business logic)간의 상호 작용을 활성화하여 **dynamic content**를 생성하고 전달하는 것이다.<br>
여기서 dynamic content란 request가 발생할 때 서버에서 동적으로 생성되거나, client측에서 runtime에 변경되는 컨텐츠이다.<br>
dynamic content에 대해 우리가 아는 쉬운 예시를 들면, 흔히 웹 개발에 입문할때 javascript로 만들어보는, 버튼을 누르면 숫자가 증가하는 웹 컨텐츠가 dynamic content이다.<br>

Web Server에서는 client의 request에 따라 static content를 제공했다면, WAS에서는 dynamic content를 제공한다!<br>
다만 이때 사용하는 protocol의 종류는 HTTP일수도 있고, 다른 protocol일 수도 있다.<br>
WAS의 예시에는 Apache Tomcat, JBoss등이 있는데, Spring boot에서 사용되는 Apache Tomcat과 Java 개발 환경에서 사용하는 application server의 구조에 대해서는 다른 포스트에서 작성하도록 하겠다.<br>

> WAS란 dynamic content를 생성하는 buisness logic을 처리하기 위한 server이다.<br>

## Nginx
Nginx는 Web Server이다.<br>
Nginx에서 Web Server의 정의를 한번 살펴보자.<br>

> A web server stores and delivers the content for a website – such as text, images, video, and application data – to clients that request it.
- The most common type of client is a web browser program, which requests data from your website when a user clicks on a link or downloads a document on a page displayed in the browser.
- A web server communicates with a web browser using the Hypertext Transfer Protocol (HTTP). 
- The content of most web pages is encoded in Hypertext Markup Language (HTML). 
- The content can be **static** (for example, text and images) or **dynamic** (for example, a computed price or the list of items a customer has marked for purchase). 
  - To deliver **dynamic** content, most web servers support server‑side scripting languages to encode business logic into the communication. 
  - Commonly supported languages include Active Server Pages (ASP), Javascript, PHP, Python, and Ruby.

Web Server 파트에서 설명하는 내용과 거의 흡사하지만, static과 dynamic에 관한 내용이 추가되었다.<br>
- static content는 text, image같은 file이고 이는 웹 서버가 HTTP Server를 통해 제공하는 *파일*들이다.<br>
  - 조금 더 자세히 정의하자면, 미리 생성된 HTML 파일, image, style sheet등과 같이 **request 시점에 변하지 않는 컨텐츠**이다.<br>
- dynamic content는  **request가 발생할 때 서버에서 동적으로 생성되거나, client측에서 runtime에 변경되는 컨텐츠**이다.<br>

그러면 질문이 생긴다.<br>
- "위에서 설명한 것은 HTTP Server가 HTTP request를 받고 필요한 파일들을 찾아 Web Browser로 보내는 것이 Web Server라고 하셨는데, 여기에 dynamic content 관련한 내용은 없잖아요?"<br>
- "dynamic content를 제공하려면 이를 수행할 수 있는 무언가가 더 있어야 하는것 아닌가요?"<br>

맞다.<br>
사실 근본적인 정의로는 Web Server는 static content를 전달하고, **Application Server(또는 WAS, Web Application Server)가 동적인 응답을 생성하고 비즈니스 로직을 수행한다.**<br>
"그러면 Nginx는 Application Server 아닌가요?"<br>
맞는 말이긴 하지만, 기본적으로 Nginx는 Web Server라고 불린다.<br>
그 이유는 Nginx는 static content를 사용하는데에 의도되었기 때문이다.<br>
그러나 Nginx는 로드 밸런서, reverse proxy, http cache 등의 역할도 할 수 있다.<br>
또한 dynamic content를 제공하기 위해 business logic을 작성하는 script 언어(Javascript, PHP, Ruby)를 지원한다.<br>
그렇기에 Django는 Nginx만 사용하더라도 구동 가능하다. 다만 session, cookie, routing등의 기능을 수행하는 middleware가 없게 된다.<br>

## Tomcat
다른 포스팅에서 자세히 설명하겠지만,<br>
Spring의 경우, 내장되어있는 Tomcat은 application server로(완전한 application server라기에는 부족한 부분이 있음) servlet container를 포함하고 있다.<br>
여기서 container란 JSP, Servlet을 실행시킬 수 있는 소프트웨어이다. 즉, dynamic content를 제공하기 위한 business logic을 이 부분에서 처리한다.<br>

그러면 business logic을 servlet container에서 처리하는 것은 알겠는데, 어떻게 HTTP request를 받아서 web server처럼 동작할까?<br>
Tomcat에 servlet container는 Catalina라는 이름을 가지고 있고, Coyote라는 connector를 가지고 있다.<br>
이 connector는 HTTP를 지원하는데, 이를 통해 Catalina는 servlet 및 JSP를 실행하는 기능 외에도 독립형 web server로 동작할 수 있다.<br>

## 출처
[What Is a Web Server?](https://www.nginx.com/resources/glossary/web-server/)<br>
[What Is an Application Server vs. a Web Server?](https://www.nginx.com/resources/glossary/application-server-vs-web-server/)<br>
[웹 애플리케이션 서버](https://ko.wikipedia.org/wiki/%EC%9B%B9_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98_%EC%84%9C%EB%B2%84)<br>
[Application server](https://en.wikipedia.org/wiki/Application_server)<br>
[The HTTP Connector](https://tomcat.apache.org/tomcat-9.0-doc/config/http.html#Common_Attributes)<br>
[Web server vs. application server](https://www.ibm.com/kr-ko/topics/web-server-application-server)<br>
[[Web] Web Server와 WAS의 차이와 웹 서비스 구조](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)<br>
[Nginx와 Gunicorn 둘 중 하나만 써도 될까?](https://velog.io/@jimin_lee/Nginx%EC%99%80-Gunicorn-%EB%91%98-%EC%A4%91-%ED%95%98%EB%82%98%EB%A7%8C-%EC%8D%A8%EB%8F%84-%EB%90%A0%EA%B9%8C)<br>

