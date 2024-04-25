### 주제 :  JDBC Type

### 날짜 : 2024-04-25 14:08
----
### 메모
> Driver or JDBC-ODBC Bridge
> 	- JDBC와 ODBC 사이의 Bridge 역할을 한다. JDBC 호출은 ODBC 호출로 변환한 다음 ODBC Driver에게 요청을 보낸다.
> 	- ODBC : 마이크로소프트가 작성한 DBMS 접근 표준이다.
> 	- 사용하기는 쉽지만, 실행시간이 느린 단점이 있다.
> 	![[Pasted image 20240425145415.png]]
> 
> Driver or Native API Partly Java Driver
> 	- JDBC 드라이버는 JNI(Java Native Interface)를 이용해서 데이터베이스 전용 네이티브 클라이언트를 호출한다.
> 	- 실행속도가 빠른 편이지만 네이티브 라이브러리를 설치해야 하고 스프트웨어 관리/개발 비용이 증가한다.
> 	- 데이터베이스 제품을 바꾼다면 응용시스템에 많은 수정이 필요할 수 있다.
> 	![[Pasted image 20240425152402.png]]
> 
> Network Protocol Driver(fully java driver)
> 	- JDBC 드라이버는 JDBC 미들웨어 서버와 독점 프로토콜로 통신한다.
> 	- JDBC 미들웨어는 요청된 프로토콜을 데이터베이스 호출로 변환한다.
> 	- 드라이버와 미들웨어는 데이터베이스 제품을 바꾸더라도 영향을 받지 않는다. (Database Independent)
> 	- 많은 네트워크 호출을 하므로 상대적으로 느린 편이다.
> 	![[Pasted image 20240425152623.png]]
> Thin Driver (F)

### 출처(참고 문헌)
-

### 연결 문서
-
