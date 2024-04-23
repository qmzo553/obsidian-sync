### 주제 : JSP Action Tag

### 날짜 : 2024-04-23 13:44
----
### 메모
> JSP Action Tag
> 	- JSP 페이지 내에서 어떤 동작을 하도록 지시하는 태그
> 	- XML 태그 형식
> 	- JSP Action Tags는 페이지 간 플로우를 제어한다.
> 	- JSP Action Tags는 Java Bean을 사용하기 위해 사용한다.

>JavaBeans
>	- 자바로 작성된 소프트웨어 컴포넌트
>	- 빌더 형식의 개발도구에서 가시적으로 조작이 가능하고 또한 재사용이 가능한 소프트웨어 컴포넌트이다.
>	- EJB(Enterprise JavaBeans)가 아님
>	- Spring Bean이 아님
> 
> JavaBeans 제약조건
> 	- public default (no ~ arg) constructor
> 	- getter/setter
> 	- implements java.io.Serializable
> 
> JSP Action tag (JavaBeans 사용)
> 
> <jsp:userBean>
> 	- 기존에 있던 객체(bean)을 찾거나 없으면 새로운 객체(bean)을 생성해서 반환
> 		1. 지정된 scope에 설정한 id 와 같은 이름의 속성(attribute)이 있으면 해당 bean을 반환
> 		2. 없으면 새로운 bean을 생성해서 지정된 scope에 id와 같은 이름의 속성(attribute)으로 설정함
> 	- 밑의 두 코드는 같다.
```jsp
<jsp:useBean id="numberList" scope="request"
             type="java.util.List<java.lang.Integer>"
             class="java.util.ArrayList" />
```
```java
List<Integer> numberList = request.getAttribute("numberList");
if (Objects.isNull(numberList)) {
    numberList = new ArrayList<>();
    request.setAttribute("numberList", numberList);
}
```
> <jsp:setProperty>
> 	- Java bean의 프로퍼티 값을 설정
> 	- 밑의 두 코드는 같다.
```jsp
<jsp:useBean id="user1" scope="request" class="com.nhnacademy.domain.User" />
<jsp:setProperty name="user1" property="age" value="35" />
```
```java

```
### 출처(참고 문헌)
-

### 연결 문서
-
