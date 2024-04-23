### 주제 : JSP implicit object

### 날짜 : 2024-04-23 13:11
----
### 메모
| 객체          | 타입                             | 설명                   |
| ----------- | ------------------------------ | -------------------- |
| page        | javax.servlet.jsp.HttpJspPage  | page의 Servlet 인스턴스   |
| config      | javax.servlet.ServletConfig    | ServletConfig        |
| request     | HttpServletRequest             | 요청 객체                |
| response    | HttpServletResponse            | 응답 객체                |
| out         | javax.servlet.jsp.JspWriter    | page 컨텐트 출력용 스트림     |
| session     | javax.servlet.http.HttpSession | 세션                   |
| application | javax.servlet.ServletContext   | ServletContext       |
| pageContext | javax.servlet.jsp.PageContext  | JSP page의 실행 context |
| exception   | java.lang.Throwable            | 처리되지 않은 에러나 예외       |
> page
> 	- scope : JSP 페이지 내에서만 사용할 수 있는 scope
> 	- PageContext 내장객체를 사용함
> 	- jsp에서는 pageContext 내장 변수를 사용함
> 	- forward가 될 경우 해당 Page scope에 지정된 변수는 사용할 수 없다.
> 	- 지역변수처럼 사용할 수 있음
> 
> request
> 	- scope : 하나의 요청을 기준으로 서버가 클라이언트에게 응답을 보낼 때까지 사용할 수 있는 scope 
> 	- jsp에서는 request 내장 변수를 사용함
> 	- forward에서 값을 유지할 수 있음
> 
> session
> 	- scope : session 객체가 생성되고 소멸할 때까지
> 	- jsp에서는 session 내장 변수를 사용함
> 
> application
> 	- scope : application이 생성되고 소멸될 때까지
> 	- 하나의 서버(tomcat)에는 여러 개의 application이 구동될 수 있음
> 	- jsp에서는 application 내장 객체를 사용함

### 출처(참고 문헌)
-

### 연결 문서
-
