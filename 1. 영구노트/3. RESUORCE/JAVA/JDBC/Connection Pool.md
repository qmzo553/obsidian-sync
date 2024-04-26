### 주제 : Connection Pool

### 날짜 : 2024-04-26 13:31
----
### 메모
> Connection Pool이란?
> 	- Connection Pool 은 데이터베이스에 접근하기 위한 패턴
> 	- 미리 Connection 객체를 생성하여 Pool 또는 Container(tomcat)에 배치
> 	- Application에서 Connection 객체가 필요할 때, 새로운 객체를 생성하는 대신 Pool에서 해당 객체를 가져와 사용하고 재사용을 위해서 사용된 객체는 Pool에 반납한다.
> 	![[Pasted image 20240426133448.png]]
> Connection Pool 장점
> 	- 데이터베이스에 Connection을 생성할 때 소요되는 시간 및 자원을 줄일 수 있다.
> 	- Connection 수를 제한 할 수 있어 과다한 접속으로 인한 서버 자원 고갈을 예방한다.
> 	- 메모리 영역에서 Connection을 관리하기 때문에 클라이언트가 데이터베이스 작업을 빠르게 진행할 수 있다.
> 	![[Pasted image 20240426133929.png]]
> Connection Pool 구현
> 	1. DataBase Driver를 사용하여 DataBase 연결
> 	2. 데이터 읽기 / 쓰기를 위한 TCP / Socket Open
> 	3. Socket을 통해서 데이터 읽기 / 쓰기
> 	4. DataBase 연결 닫기
> 	5. TCP / Socket Close

### 출처(참고 문헌)
-

### 연결 문서
-
