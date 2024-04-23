### 주제 : JSP 동작구조

### 날짜 : 2024-04-23 12:59
----
### 메모
> 	![[Pasted image 20240423130011.png]]
> 	- 컨테이너는 JSP 파일을 HttpJspPage 인터페이스를 구현한 서블릿 클래스로 변환하여 생성한다.
> 
> 주요 api
> 	- jsplinit() : servlet의 init() 메소드에서 호출한다, 재정의 가능
> 	- jspDestory() : servlet의 destory() 메소드에서 호출한다, 재정의 가능
> 	- jspService() : servlet의 service() 메소드에서 호출한다, 재정의 불가능
> 
> 우리가 작성한 jsp코드를 받아서 jspService() method를 만드는 일은 Container를 만드는 벤더가 할 일(즉, tomcat에서 할 일)

### 출처(참고 문헌)
-

### 연결 문서
-
