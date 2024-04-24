### 주제 : MVC

### 날짜 : 2024-04-24 09:03
----
### 메모
> MVC
> 	![[Pasted image 20240424092503.png]]
> 	- JSP에서 모든 로직과 출력을 처리한다.
> 	- 즉 JSP 페이지에서 비지니스 로직을 처리하기 위한 코드와 웹브라우저에 결과를 출력하는 코드가 섞여 있다.
> 	![[Pasted image 20240424092614.png]]
> 		- 모든 요청을 서블릿이 받아 처리하고 JSP 페이지로 포워드 한다.
> 		- 서블릿은 클라이언트(브라우저) 요청을 구분하여 처리한다.
> 		-> MVC Pattern
> 
> MVC Pattern
> 	- Model : 비즈니스 로직 및 데이터 처리 담당
> 	- View : 모델이 처리한 결과를 데이터의 화면 생성 담당
> 	- Controller : 요청 처리 및 흐름 제어 담당
> 
> MVC Pattern 장점
> 	- 유연하고 확장이 용이
> 	- 협업이 용이
> 	- 유지보수 용이
> 
> Servlet의 공통 처리 부분
> 	FrontServlet
> 	 ![[Pasted image 20240424093218.png]]
> 		 1. 모든 요청을 FrontServlet이 다 받아서 
> 			 - FrontServlet이 받을 요청은 .do 확장자를 사용
> 			 - 실제 요청은 .do 확장자가 없음
> 			 - /foods.do : FrontServlet이 처리
> 			 - /foods : 실제 요청은 Servlet에서 처리
> 		 1. 요청 URL에 따라 실제 요청을 처리할 Servlet으로 요청을 전달
> 		 2. 실제 요청을 처리한 Servlet은 처리 결과를 어떤 jsp에서 view 할 건지를 반환
> 		 3. 실제 요청을 처리한 Servlet이 전달해 준 jsp로 view 처리를 위임
> 		 4. JSP는 실제 요청을 처리한 Servlet에서 ServletRequest에 설정한 속성을 이용해 view 처리를 수행
> 		 5. FrontServlet이 요청에 대해 응답

### 출처(참고 문헌)
-

### 연결 문서
-
