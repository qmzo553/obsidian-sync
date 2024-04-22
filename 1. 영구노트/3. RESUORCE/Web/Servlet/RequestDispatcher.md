### 주제 : RequestDispatcher

### 날짜 : 2024-04-22 16:11
----
### 메모
> RequestDispatcher
> 	- Servlet API의 일부이다.
> 	- 현재의 요청에 대한 정보를 저장했다가 다른 자원(Servlet, JSP, HTML 등)으로 전달(forward, include)하는 기능을 제공
> 	- 웹 애플리케이션에서 Model-View-Controller(MVC) 아키텍처를 구현하는 데 일반적으로 사용된다.
> 	- forward() : JSP 페이지와 같은 다른 리소스로 제어를 전송한다.
> 	- include() : 다른 리소스의 출력을 현재 페이지의 출력에 포함시키는 데 사용된다.

> re.forward() vs response.sendRedirect()
> 
> response.sendRedirect()
> 	1. /aaa 요청을 처리
> 	2. Http Status Code : 302 응답
> 	3. Browser는 서버로부터 응답받은 코드를 확인하고 /bbb로 요청을 보냄 -> 새로운 페이지 /bbb로 이동한다.
> 	![[Pasted image 20240422164350.png]]
> 	![[Pasted image 20240422164356.png]]
> 
> rd.forward()
> 	1. /aaa 요청을 처리하고 HttpServletRequest, HttpServletResponse 생성됨
> 	2. /bbb에 /aaa 에서 생성 된 HttpServletRequest와 HttpServletResponse를 보냄
> 	3. /bbb 는 요청을 처리하고 Browser에 응답
> 	- 즉 새로운 페이지 /bbb 로 이동하지 않고 /aaa로 유지 한다. -> /aaa에서 요청했던 데이터가 유지된다.
> 	- redirect와 동작방식은 비슷하지만 서버에서 동작한다.
> 	![[Pasted image 20240422164820.png]]
> 	

### 출처(참고 문헌)
-

### 연결 문서
-