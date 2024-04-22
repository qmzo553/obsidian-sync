### 주제 : CGI

### 날짜 : 2024-04-22 11:01
----
### 메모
> CGI
> 	- Common Gateway Interface
> 	- 웹 서버가 외부 프로그램을 실행할 수 있도록 해주는 인터페이스 명세(specification)
> 	- 외부 프로그램은 동적 웹 컨텐츠를 생성하는 역할이다. (c, c++, java 등)
> 	- 웹 서버와 CGI 프로그램 간의 규칙
> 	![[Pasted image 20240422110454.png]]

> CGI Spec
> 
> 입출력
> 	- 주로 표준 입출력 사용
> 
> Meta-Variables(메타 변수)
> 	- 웹 서버에서 CGI 프로그램으로 전달되는 요청 관련 데이터이다.
> 	- 주로 환경변수(environment variable) 형태로 구현한다.
> 		1. SERVER_NAME
> 		2. SERVER_PORT
> 		3. REMOTE_ADDR
> 		4. REQUEST_METHOD
> 		5. CONTENT_TYPE
> 		6. CONTENT_LENGTH
> 
> Script
> 	- 서버에 의해 호출되는 소프트웨어
> 	- 런타임에 해석되는 일련의 명령문
> 	- 장점 : 언어, 플랫폼에 독립적이다. 구조가 단순하고 다른 서버 사이드 프로그래밍 언어에 비해 쉽게 수행가능하다.
> 	- 단점 : 
> 		1. 속도가 느리다.(매 요청마다 DB Connection을 새로 열어야 한다.)
> 		2. Http 요청마다 새로운 프로세스를 만들어 서버 메모리를 사용한다.
> 		3. 데이터가 메모리에 캐시 될 수 없다.
> 	![[Pasted image 20240422111046.png]]

> Java CGI Program
> 
> Java Application은 컴파일 방식?
> 	- .class 형태로 컴파일 된 Java는 컴파일 방식으로 실행 불가능 하다. -> JVM은 Java를 실행할 수 있지만 Server간의 통신은 불가능 하다.
> 	- 웹 서버와 Java Application 사이에서 서로 통신할 수 있도록 한 JCGI가 있어야 한다.
> 	![[Pasted image 20240422111330.png]]
> 	

### 출처(참고 문헌)
-

### 연결 문서
-
