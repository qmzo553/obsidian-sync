### 주제 : JSP EL

### 날짜 : 2024-04-23 18:58
----
### 메모
> JSP EL(Expression Language)
> 	- Java Bean의 프로퍼티나 array, list, map과 같은 자료구조의 값을 쉽게 꺼낼 수 있게 해주는 표현식
> 	- javascript 에서 영감받아 만든 표현식
> 	- Scriptlet 사용 최소화
> 
> EL 표기법
> 	- ${표현식}
> 	- immediate evaluation : JSP가 실행될 때 표현식으로 지정한 값이 JSP 페이지에 즉시 반영
> 	- deferred evaluation : 표현식으로 지정된 값은 시스템에서 필요하다고 판단할 때 그 값을 사용
```jsp
my name is <jsp:getProperty name="user1" property="name"/>.<br />
=
my name is ${user1.name}.<br />
```
> EL 검색 범위
> 	- pageScope -> JspContext 객체를 참조
> 	- requestScope ->ServletRequest 객체를 참조
> 	- sessionScope -> HttpSession 객체를 참조
> 	- applicationScope -> ServletContext 객체를 참조
> 
> EL 기본 문법
> 	- 문자열 : ${"나랏말"},  ${문자}
> 	- 정수 : ${20}
> 	- 실수 : ${3.14}
> 	- boolean : ${true}
> 	- null : ${null}
### 출처(참고 문헌)
-

### 연결 문서
-
