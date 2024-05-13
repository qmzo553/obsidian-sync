### 주제 : 톰캣에 대하여

### 날짜 : 2024-05-13 23:18
----
### 메모
> Tomcat
> 	- 아파치 소프트웨어 재단에서 후원을 하고있는 오픈소스 프로젝트이다.
> 	- WAS(web application server), 웹 컨테이너, 서블릿 컨테이너라고 불린다.
> 	- JSP와 Servlet을 구동하기 위한 Servlet Container 역할을 수행한다.
>
> WAS
> 	- DB 처리, 로직 처리를 요구하는 동적타입을 제공하는 소프트웨어 프레임워크를 의미한다.
> 	- 프로그램 실행 환경과 데이터베이스 접속 기능을 제공한다.
> 	- 여러 개의 트랜잭션을 관리한다.
> 	- 업무를 처리하는 비즈니스 로직을 수행한다.
> 
> Servlet Container
> 	- JSP, Servlet들을 모아서 관리한다.
> 	- 새로운 요청이 들어올 때마다 새로운 쓰레드를 생성한다. -> 멀티 쓰레드로 구동
> 	- 작업이 끝난 Servlet 쓰레드는 자동 제거한다.
> 
> apache tomcat 으로 부르는 이유?
> 	![[Pasted image 20240513233133.png]]
> 	- 기본적으로 위의 사진처럼 apache와 tomcat의 기능은 나뉘어져 있지만, tomcat 안에 있는 container를 통해 일부 apache의 기능을 발휘하기 때문에 보통 합쳐서 부르곤 한다.
> 
> apache 소프트웨어 재단
> 	- 오픈 소스 소프트웨어 프로젝트를 운영하는 비영리 단체이다.
> 	- 개발자들의 탈중앙화를 지원해준다.
> 	- 주요 프로젝트
> 		1. 아파치 HTTP 서버
> 		2. Tomcat
> 		3. jakarta
> 		4. maven
> 		5. groovy

### 출처(참고 문헌)
- [[https://velog.io/@kdhyo/Apache-Tomcat-%EB%91%98%EC%9D%B4-%EB%AC%B4%EC%8A%A8-%EC%B0%A8%EC%9D%B4%EC%A7%80]]

### 연결 문서
-
