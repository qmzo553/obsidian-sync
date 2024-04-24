### 주제 : command pattern

### 날짜 : 2024-04-24 23:08
----
### 메모
> Command Pattern
> 	- 요청을 객체의 형태로 캡슐화하여
> 	- command를 저장하거나 메서드에 전달하거나 다른 객체들 처럼 변환할 수 있게 해주는 디자인 패턴
> 	- GUI 애플리케이션에서는 메뉴나 버튼 등의 요소들과 이벤트 핸들러 등에서 사용된다.
> 	- 웹 애플리케이션에서는 HTTP 요청과 응답 처리에 적용할 수 있다.
> 
> Command Pattern 구성 요소
> 	- Command : 요청을 캡슐화하는 인터페이스를 정의한다. excute() method를 선언한다.
> 	- ConcreteCommand : Command 인터페이스를 구현한 구체적인 클래스이다. excute() method를 구현하여 요청 처리
> 	- Invoker : 요청을 수신하는 객체를 정의한다. Command 객체를 유지하고, execute() method를 호출하여 요청 처리
> 	- Receiver : 실제 요청 처리를 수행하는 객체이다. ConcreteCommand는 Receiver 객체를 호출하여 실체 요청 처리
> 
> Command Pattern 장점
> 	- 요청 처리 과정을 캡슐화하므로, 요청 처리 과정의 변경이나 확장에 유연하게 대응할 수 있다.
> 	- 요청 처리에 대한 로깅, 취소, 다시 실행 등의 기능을 구현하기 쉽다.
> 	- 객체 간의 의존성을 줄일 수 있으며, 객체 간의 결합도를 낮출 수 있다.
> 	![[Pasted image 20240424231459.png]]
> 	


### 출처(참고 문헌)
-

### 연결 문서
-
