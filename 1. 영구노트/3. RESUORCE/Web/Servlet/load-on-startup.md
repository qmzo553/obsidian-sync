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

### 출처(참고 문헌)
-

### 연결 문서
-
