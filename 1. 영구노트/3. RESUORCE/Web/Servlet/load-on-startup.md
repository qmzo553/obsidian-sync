### 주제 : load on startup

### 날짜 : 2024-04-22 14:03
----
### 메모
> Servlet의 문제점
> 	- Servlet은 브라우저의 최초 요청시 init() 메서드(초기화) 과정을 통해서 메모리에 로드되어 기능을 수행한다.
> 	- 이는 최초 요청에 대해서 실행시간이 길어질 수 있는 단점이 있다.
> 	- 지연 초기화(lazy initialization)
> 
> load-on-startup 특징
> 	- 0 보다 크면 tomcat container가 미리 servlet을 초기화 한다.
> 	- 숫자의 순서에 의해서 초기화 된다.

> Servlet class 계층도
> 	![[Pasted image 20240422140555.png]]

> GenericServlet 이란?
> 	- http 이외의 프로토콜을 위한 범용 Servlet
> 	- http protocol -> HttpServlet 확장
> 	- http 이외의 protocol -> GenericServlet 확장
> 	- 

> Servlet lifecycle 정리
> 	- init() method
> 		1. Servlet Container가 Servlet을 생성한 후 초기화 작업을 수행하기 위해 호출
> 		2. 클라이언트의 요청을 처리하기 전에 준비할 작업이 있는 경우 여기에서 처리
> 	- service() method는 굳이 override 할 필요 없음
> 	- GET, POST, PUT, DELETE 각각의 http method에 대해 구현이 필요한 doXXX() method override해서 구현
> 	- destroy() method는 Servlet Container가 종료되거나 해당 서블릿을 비활성화시킬 때 호출 -> 서비스 수행을 위해 확보되었던 자원 해제, 데이터 저장등의 마무리 작업 시 여기에서 처리

### 출처(참고 문헌)
-

### 연결 문서
- [[ServletContext]]
