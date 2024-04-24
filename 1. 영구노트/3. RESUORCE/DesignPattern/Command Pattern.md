### 주제 : command pattern

### 날짜 : 2024-04-24 23:08
----
### 메모
> Command Pattern
> 	- 요청을 객체의 형태로 캡슐화하여
> 	- command를 저장하거나 메서드에 전달하거나 다른 객체들 처럼 변환할 수 있게 해주는 디자인 패턴
> 
> Command Pattern 구성 요소
> 	- Command : 요청을 캡슐화하는 인터페이스를 정의한다. excute() method를 선언한다.
> 	- ConcreteCommand : Command 인터페이스를 구현한 구체적인 클래스이다. excute() method를 구현하여 요청 처리
> 	- Invoker : 요청을 수신하는 객체를 정의한다. Command 객체를 유지하고, execute() method를 호출하여 요청 처리
> 	- Receiver : 실제 요청 처리를 수행하는 객체이다. Concre


### 출처(참고 문헌)
-

### 연결 문서
-
