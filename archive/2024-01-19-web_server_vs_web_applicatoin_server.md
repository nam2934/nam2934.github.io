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
last_modified_at: 2024-01-19
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

이 모든것을 요약하자면,<br>
- Web Server는 하드웨어와 소프트웨어 측면으로 나뉜다.<br>
  - 하드웨어 측면에서는 웹서버 소프트웨어와 파일들을 저장하는 일종의 컴퓨터이다.<br>
  - 소프트웨어 측면에서는 Browser가 보낸 request를 받아 처리하는 역할을 하는데, 이 역할은 HTTP Server가 수행한다.<br>
HTTP Server는 Browser가 HTTP request를 보내면 이를 받고, 필요한 파일들을 Web Server hardware에서 찾아 이를 Browser로 보내는 역할을 하는 것이다.<br>

이 설명을 보니, Wikipedia의 설명이 이해된다.<br>
*Web Server는 HTTP를 통해 request를 수락하는 컴퓨터 소프트웨어 및 하드웨어이다!*

여기까지는 가장 기초적인 Web Server의 개념이다.<br>
조금 더 나아가보자.<br>

### Nginx
> A web server stores and delivers the content for a website – such as text, images, video, and application data – to clients that request it.
- The most common type of client is a web browser program, which requests data from your website when a user clicks on a link or downloads a document on a page displayed in the browser.
- A web server communicates with a web browser using the Hypertext Transfer Protocol (HTTP). 
- The content of most web pages is encoded in Hypertext Markup Language (HTML). 
- The content can be **static** (for example, text and images) or **dynamic** (for example, a computed price or the list of items a customer has marked for purchase). 
  - To deliver **dynamic** content, most web servers support server‑side scripting languages to encode business logic into the communication. 
  - Commonly supported languages include Active Server Pages (ASP), Javascript, PHP, Python, and Ruby.

두 사이트가 설명하는 내용과 거의 흡사하지만, static과 dynamic에 관한 내용이 추가되었다.<br>
- static content는 text, image같은 file이고 이는 웹 서버가 HTTP Server를 통해 제공하는 *파일*들이다.<br>
  - 조금 더 자세히 정의하자면, 미리 생성된 HTML 파일, image, style sheet등과 같이 **request 시점에 변하지 않는 컨텐츠**이다.<br>
- dynamic content는 **request가 발생할 때 서버에서 동적으로 생성되거나, client측에서 runtime에 변경되는 컨텐츠**이다.<br>
dynamic content에 대해 우리가 아는 쉬운 예시를 들면, 흔히 웹 개발에 입문할때 javascript로 만들어보는, 버튼을 누르면 숫자가 증가하는 웹 컨텐츠가 동적 컨텐츠이다.<br>

그러면 질문이 생긴다.<br>
- "위에서 설명한 것은 HTTP Server가 HTTP request를 받고 필요한 파일들을 찾아 Web Browser로 보내는 것이 Web Server라고 하셨는데, 여기에 동적 컨텐츠 관련한 내용은 없잖아요?"<br>
- "동적 컨텐츠를 제공하려면 이를 수행할 수 있는 무언가가 더 있어야 하는것 아닌가요?"<br>

맞다.<br>
사실 근본적인 정의로는 Web Server는 정적 컨텐츠를 전달하고, **Application Server가 동적인 응답을 생성하고 비즈니스 로직을 수행한다.**<br>
"그러면 Nginx는 Web Application Server 아닌가요?"<br>
맞는 말이긴 하지만, 기본적으로 Nginx는 Web Server라고 불린다.<br>
그 이유는 Nginx는 정적 컨텐츠를 제공하는데에 특화되어 있기 때문이다.<br>


