# Java Platform(Java Enterprise Edition, J2EE)

자바 플랫폼, 엔터프라이즈 에디션(Java Platform, Enterprise Edition; Java EE)은 자바를 이용한 서버측 개발을 위한 플랫폼이다. Java EE 플랫폼은 PC에서 동작하는 표준 플랫폼인 Java SE에 부가하여, 웹 애플리케이션 서버에서 동작하는 장애복구 및 분산 멀티티어를 제공하는 자바 소프트웨어의 기능을 추가한 서버를 위한 플랫폼이다. 이전에는 J2EE라 불리었으나 버전 5.0 이후로 Java EE로 개칭되었다.

이러한 Java EE 스펙에 따라 제품으로 구현한 것을 웹 애플리케이션 서버 또는 WAS라 불린다.

J2EE의 다양한 스펙 집합 중 대표적인 것들은 다음과 같다.

1. Servlet : HTTP 요청을 처리하여 웹페이지를 동적으로 생성하는 서버측 프로그램 혹은 그 사양을 말한다.

2. JSP(Java Server Pages):  HTML내에 자바 코드를 삽입하여 웹 서버에서 동적으로 웹 페이지를 생성하여 웹 브라우저에 돌려주는 언어이다. 

3. EJB(Enterprise Java Beans) : 기업환경의 시스템을 구현하기 위한 서버측 컴포넌트 모델이다. 즉, EJB는 애플리케이션의 업무 로직을 가지고 있는 서버 애플리케이션이다. EJB 사양은 Java EE의 자바 API 중 하나로, 주로 웹 시스템에서 JSP는 화면 로직을 처리하고, EJB는 업무 로직을 처리하는 역할을 한다.

4. Remote Method Invocation(RMI): 프록시를 써서 원격에 있는 Java 객체의 메소드를 실행시키기 위한 기술이다.

5. Java Naming DirectoryInterface(JNDI): 디렉터리 서비스에서 제공하는 데이터 및 객체를 발견(discover)하고 참고(lookup)하기 위한 자바 API다.

6. Java Database Connector(JDBC): 자바에서 데이터베이스에 접속할 수 있도록 하는 자바 API이다. JDBC는 데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법을 제공한다.

7. Java Connector Architecture(JCA): 웹 애플리케이션 서버와 레가시 시스템과 연동할 수 있도록 하는 자바 기반 기술이다. JDBC는 웹 애플리케이션 서버와 데이터베이스와의 연동에 사용된다면, JCA는 웹 애플리케이션 서버와 레거시 시스템(데이터베이스 포함)과 연동하는 보다 일반적인 방법이다. 

8. Java Message Service(JMS): 자바 메시지 서비스 API는 두 개 혹은 그 이상의 클라이언트 간 메시지 통신을 위한 자바 메시지 기반 미들웨어 API(자바 메시지 지향 미들웨어 (MOM) API)이다.

Reference : [wiki - J2EE](https://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition)

## MVC 패턴

모델-뷰-컨트롤러(Model–View–Controller, MVC)는 소프트웨어 공학에서 사용되는 소프트웨어 디자인 패턴이다. 이 패턴을 성공적으로 사용하면, **사용자 인터페이스로부터 비즈니스 로직을 분리**하여 애플리케이션의 시각적 요소나 그 이면에서 실행되는 비즈니스 로직을 서로 영향 없이 쉽게 고칠 수 있는 애플리케이션을 만들 수 있다. MVC에서 모델은 애플리케이션의 정보(데이터)를 나타내며, 뷰는 텍스트, 체크박스 항목 등과 같은 사용자 인터페이스 요소를 나타내고, 컨트롤러는 데이터와 비즈니스 로직 사이의 상호동작을 관리한다.

모델-뷰-컨트롤러는 응용 프로그램을 세 가지의 구성요소로 나눈다. 각각의 구성요소들 사이에는 다음과 같은 관계가 있다. 

- 컨트롤러(Controller)는 모델에 명령을 보냄으로써 모델의 상태를 변경할 수 있다. (예: 워드 프로세서에서 문서를 편집하는 것) 또, 컨트롤러가 관련된 뷰에 명령을 보냄으로써 모델의 표시 방법을 바꿀 수 있다. (문서를 스크롤하는 것)
- 모델(Model)은 모델의 상태에 변화가 있을 때 컨트롤러와 뷰에 이를 통보한다. 이와 같은 통보를 통해서 뷰는 최신의 결과를 보여줄 수 있고, 컨트롤러는 모델의 변화에 따른 적용 가능한 명령을 추가·제거·수정할 수 있다. 어떤 MVC 구현에서는 통보 대신 뷰나 컨트롤러가 직접 모델의 상태를 읽어 오기도 한다.
- 뷰(View)는 사용자가 볼 결과물을 생성하기 위해 모델로부터 정보를 얻어 온다.

Reference : [wiki - MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)


## 아파치 톰캣 (Apache Tomcat)

### 1. Apache

아파치(Apach)란 소프트웨어 단체 이름으로 아파치 서버(Apache server)라는 것은 이 제단에서 후원하는 오픈소프 프로젝트 커뮤니티에서 만든 **Http웹서버**를 지칭하는 말이다. 아파치 웹서버는 동적인 컨텐츠 제공을 위해 클라이언트 요청(Request)을 WAS로 전달하고, WAS의 처리 결과를 클라이언트에게 응답(Response)하는 역할을 한다.

 Http 웹서버는 Http 통신을 기반으로 요청을 처리할 수 있는 웹서버이고, 아파치 Http서버는 Http요청을 처리하는 웹서버이다. 웹 브라우저 클라이언트로부터 GET, POST, DELETE 메소드를 활용하여 HTTP 요청을 보내면 이를 수신하여 정적인 컨텐츠(.html .jpeg .css 등)를 제공하는 컴퓨터 프로그램이다.

> Apache = HTTP web server

### 2. Tomcat

Tomcat은 흔히 WAS(Web Application Server)라고 말한다. WAS는 웹서버(Web server)와 웹 컨테이너(Web container)의 결합으로 다양한 기능을 컨테이너에 구현하여 DB 조회나 다양한 로직 처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 Application Server이다. 

웹 컨테이너(Web container)란 JSP, Servlet을 실행시킬 수 있는 소프트웨어를 말한다. 웹 컨테이너는 라이언트의 요청이 있을 때 내부의 프로그램 로직을 통해 동적인 결과를 만들어내고 이것을 다시 클라이언트에 전달해주는 역할을 한다.

> Tomcat = Apache + Web container

### 3. Apache와 Tomcat의 차이 (Difference between Apache & Tomcat)

그렇다면 WAS만 쓰면 되지 웹서버를 따로 쓰는지에 대한 의문이 생길 수 있다. 그 이유는 목적이 다르기 때문이다. 

- Web server는 정적인 데이터(static data)를 처리하는 서버이다. 이미지나 단순 html파일과 같은 리소스를 제공하는 서버는 웹 서버를 통하면 WAS를 이용하는 것보다 빠르고 안정적이다. 

- WAS는 동적인 데이터(dynamic data)를 처리하는 서버이다. DB와 연결되어 데이터를 주고 받거나 프로그램으로 데이터 조작이 필요한 경우에는 WAS를 활용 해야 한다.

- 그렇다면 WAS가 Web Server의 기능도 모두 수행하면 되지 않을까?

    - 기능을 분리하여 서버 부하 방지
    WAS는 DB 조회나 다양한 로직을 처리하느라 바쁘기 때문에 단순한 정적 컨텐츠는 Web Server에서 빠르게 클라이언트에 제공하는 것이 좋다.
    - WAS는 기본적으로 동적 컨텐츠를 제공하기 위해 존재하는 서버이다.
    만약 정적 컨텐츠 요청까지 WAS가 처리한다면 정적 데이터 처리로 인해 부하가 커지게 되고, 동적 컨텐츠의 처리가 지연됨에 따라 수행 속도가 느려진다. 즉, 이로 인해 페이지 노출 시간이 늘어나게 될 것이다.
    - 물리적으로 두 기능을 분리하여 보안을 강화한다.
        - SSL에 대한 암복호화 처리에 Web Server를 사용
    - 여러 대의 WAS를 연결하여 다양한 서비스 제공이 가능하다. ex) PHP와 Java application 함께 사용
    - Load Balancing을 위해서 Web Server를 사용한다.
    - fail over, fail back 처리에 유리하다.
    - 접근 허용 IP 관리, 2대 이상의 서버에서의 세션 관리 등도 Web Server에서 처리하면 효율적이다.

### 4. WAS 구조 (Web Application Server structure)

Apache Tomcat의 클라이언트 요청 처리 구조는 다음 그림과 같은 형태를 나타낸다.

![image](https://gmlwjd9405.github.io/images/web/web-service-architecture.png)

위 그림에 따른 클라이언트 요청 프로세스는 다음과 같이 진행된다.

1. Web Server는 웹 브라우저 클라이언트로부터 HTTP 요청을 받는다. (정적 페이지는 즉시 응답한다.)

2. Web Server는 클라이언트의 요청(Request)을 WAS에 보낸다.
3. WAS는 관련된 Servlet을 메모리에 올린다.
4. WAS는 web.xml을 참조하여 해당 Servlet에 대한 Thread를 생성한다. (Thread Pool 이용)
5. HttpServletRequest와 HttpServletResponse 객체를 생성하여 Servlet에 전달한다.

    5-1. Thread는 Servlet의 service() 메서드를 호출한다.

    5-2. service() 메서드는 요청에 맞게 doGet() 또는 doPost() 메서드를 호출한다.
    
6. doGet() 또는 doPost() 메서드는 인자에 맞게 생성된 적절한 동적 페이지를 Response 객체에 담아 WAS에 전달한다.
7. WAS는 Response 객체를 HttpResponse 형태로 바꾸어 Web Server에 전달한다.
8. 생성된 Thread를 종료하고, HttpServletRequest와 HttpServletResponse 객체를 제거한다.

Reference : https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html

## Servlet (서블릿)

Servlet(서블릿)은 Server Side Applet의 약자로 웹 서버, 즉 컨테이너에서 수행되는 Java 클래스이다.

- 서버 응용 프로그램을 구성하는 Servelt은 서버 프로토콜 종류에 관계없이 FTP, SMTP, HTTP 등 여러 가지 애플리케이션 기반의 응용 프로그램 개발이 가능하다.

- Serlvet은 클라이언트 요청에 대해 서블릿 컨테이너에 의해 독립된 스레드 기반으로 서비스 되는 기술로서 다중 스레드 서비스가 기본적으로 지원된다.

- Servlet Container는 클라이언트에서 전송되는 Servlet request와 resonponse에 대한 처리를 담당한다.

- Servlet Container로는 오픈 소스인 Apahce Tomcat이 대표적이며, 상용화된 WAS로는 WebLogic, WebSphere 등이 있다.

### Servlet & jsp history

1. Servlet 소스 내에 HTML 코드 포함으로 인한 Business와 Presentation Logic이 분리되지 않았다.

2. jsp가 등장하여 Servlet의 HTML 소스를 처리하였다.

3. jsp scripting 기술의 한계로 Java 코드와 HTML 및 JS 코드가 혼재하여 Presenstation 관리는 쉬워졌지만 프로그램 관리가 더 복잡해졌다.

4. Model-2 Architecture가 등장하여 Model(DAO,DTO), View(jsp,jstl), Controller(Servlet) 구조가 등장하여 유지보수 및 확장성을 제고하였다.

5. Struts, Spring framework등과 같은 오픈소스 프레임워크 등장하였다.


### Servlet life cycle

![image](https://www.tutorialspoint.com/servlets/images/servlet-lifecycle.jpg)

- init() : Sevlet 초기화 관련 부분을 수행할 수 있도록 내부적으로 자동 호출되는 메소드이다.

- service() : init()호출 후에 Servlet instance의 service()를 호출하여 클라이언트 요청을 받아 처리할 수 있도록하며 ServletRequset 객체와 ServletResponse 객체를 매개변수로 전달한다.

- destroy() : 클라이언트 요청을 처리한 Servlet thread는 gc에 의해 처리되기 전 마무리 작업을 위해 destroy()를 호출한다.

## JSP (Java Server Page)

 jsp는 웹 페이지를 동적으로 처리할 수 있는 기술 중의 하나로 Servlet 프로그램의 기능을 HTML 파일 내에 스크립트로 구현 가능하다. 이를 통해 Presentation과 Business logic을 효율적으로 분리한다. <br>
 jsp는 Component의 재사용과 JSTL, EL, Custom tag 등을 활용한 개발 용이성, 서버 자원을 효율적으로 관리한다는 장점을 가진다.

### JSP 동작과정

![image](https://www.geeksforgeeks.org/wp-content/uploads/jsplifecycle.png)

1. 최초 요청 시 
    - JSP 파일은 Servlet인 Java 소스 파일로 변환되고 다시 클래스 파일로 컴파일 된다.
    - 클래스 파일이 JSP/Servlet 컨테이너인 Tomcat 내에서 실행되어 그 결과가 최종적으로 웹 브라우저로 전달된다.

2. 재요청 시
    - 변환 및 컴파일이 최초 요청에서 이미 진행된다.
    - 이미 메모리에 적재된 클래스가 응답을 준다.

### JSP Sripting Element

1. 스크립트릿(Scrptlet) : jsp 페이지 내에서 코드 구현을 위해 사용한다.

    ```jsp
    <%
        for(int i = 1; i <= 10; ++i)
            out.println("Number" + i + "<br>");
    %>
    ```

2. 선언(Declaration) : 멤버변수나 선언이나 메소드 선언에 사용한다. Servlet으로 변환될 때 Servlet의 Member field나 Member method로 선언된다.

    ```jsp
    <%!
        String name = "Dongik";
        public boolean isExist(){
            return true;
        }
    %>
    ```

3. 표현식(Expression) : 간단한 데이터 출력 또는 메소드 호출을 통한 결과 출력을 위해 활용한다.

    ```jsp
    <%=
        result + resultSum()
    %>
    ```

### JSP 지시자 태그 (Directive tag)

Directive tag는 현재의 jsp 페이지 자체에 대해서 jsp 엔진 및 컨테이너에게 각종 처리 정보 전달하고 수행해야 할 기능을 정하는 역할을 한다.

1. page Directive tag : 컨테이너에게 현재 jsp 페이지를 어떻게 처리할 것인가에 대한 정보를 제공한다. contentType, import, errorPage, isErrorPage, session, pageEncoding, buffer, autoflush, info, language, isThreadsafe, extends 속성 등을 정의할 수 있다.
    ```jsp
        <%@ page contentType="text/html;charset=utf-8" %> 
    ```

2. include Directive tag : 공통적인 jsp 내용에 대해 한 파일에 작성 후 다른 jsp 페이지 내에서 삽입할 수 있다.
    ```jsp
        <%@ include file="header.jsp" %> 
    ```

3. taglib Directive tag : 사용자가 만든 Custom tage를 이용할 때 사용되며 jsp 페이지 내에서 불필요한 자바 코드를 줄일 수 있다.
    ```jsp
        <%@ taglib uri="/WEB-INF/taglib.tld" prefix="soccer" %> 
    ```
 

## Spring Framework
