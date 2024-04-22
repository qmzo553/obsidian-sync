### 주제 : web.xml

### 날짜 : 2024-04-22 15:10
----
### 메모
> 배치 기술서(Deployment Descriptor: DD)
> 	- 웹 애플리케이션의 배치 정보를 담고 있는 XML 파일
> 	- /WEB-INF/ 디렉터리 하위에 위치
> 	- web-app 이라는 하나의 태그 하위로 설정을 기술
> 	- 웹 애플리케이션의 구성 요소 : 서블릿, 필터, 리스너 등과 같은 구성 요소를 정의할 수 있다.
> 		1. 서블릿 매핑: 웹 애플리케이션에서 URL과 서블릿 클래스 사이의 매핑을 정의할 수 있다.
> 		2. 필터 설정 : HTTP 요청 및 응답을 변경하거나 필터링하는 데 사용되는 필터를 정의할 수 있다.
> 		3. 보안 설정 : 웹 애플리케이션에 대한 보안 설정을 정의할 수 있다.
> 		4. 초기화 매개변수 : 웹 애플리케이션에 대한 초기화 매개변수를 정의할 수 있다.

> web.xml 파일내 web-app 하위 태그들
> 	- servlet : Servlet 등록 정보
> 	- servlet-mapping : servlet과 URL 매핑 정보
> 	- context-param : servletContext의 초기 파라미터
> 	- welcome-file-list : welcome file list(index.html 같은 파일 -> 기본 페이지)
> 	- error-page
> 	- filter : servlet filter 등록 정보
> 	- filter-mapping : servlet filter와 URL 맵핑 정보
> 	- listener : Listener 등록 정보

### 출처(참고 문헌)
-

### 연결 문서
- [[RequestDispatcher]]
