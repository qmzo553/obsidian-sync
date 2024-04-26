### 주제 : jdbc statement

### 날짜 : 2024-04-25 15:56
----
### 메모
> Statement
> 	- Java에서 SQL 문을 실행하기 위해서는 Statement 클래스를 이용한다.
> 	- SQL 문 실행 결과를 얻어오기 위해서는 ResultSet 클래스를 이용한다.
> 
> Statement 사용
> 	- SQL 문을 데이터베이스로 보내고 결과를 받기 위한 Statement를 Connection 객체를 이용해서 생성한다.
```java
Statement statement = connection.createStatement();
ResultSet resultSet = statement.executeUpdate("select * from jdbc_students where id='marco'");
```
> Statement의 Methods(Query, Update)
> 	- executeQuery() : SELECT 쿼리를 실행할 때 사용한다. ResultSet을 결과로 반환한다.
> 	- executeUpdate() : INSERT 등의 DDL을 실행할 때 사용한다. int 타입으로 성공 여부나 처리된 데이터 수를 반환한다.
> 
> ResultSet
> 	- ResultSet 객체는 현재 데이터의 행(레코드 위치)을 가리키는 커서(cursor)을 관리한다.
> 	- 초기 값은 첫 번째 행 이전(Beginning Of File)을 가리키도록 되어 있다.
> 	- ResultSet 클래스는 주로 커서의 위치와 관련된 메소드와 레코드를 가져오는 메소드를 제공한다.
> 	![[Pasted image 20240425160347.png]]

> PreparedStatement
> 	- Precompile(미리 컴파일된) SQL을 보내고 싶을 때 사용한다.
> 	- DBMS에서 동일하거나 비슷한 데이터베이스 문을 높은 효울성으로 반복적으로 실행하기 위해 사용되는 기능이다.
> 	- 템플릿의 형태를 취하며, 그 템플릿 안으로 특정한 상숫값이 실행 때마다 대체된다.
> 	- 데이터베이스에서 cache를 조회하여 이전에 Pre-compilation된 쿼리를 사용한다.
> 	- SQL injection을 방어한다.
> 	- 배치 실행을 지원한다.

### 출처(참고 문헌)
-

### 연결 문서
- [[Connection Pool]]
