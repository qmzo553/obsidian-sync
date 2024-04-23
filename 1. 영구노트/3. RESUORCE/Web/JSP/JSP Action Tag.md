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
> 	- Java bean의 property 값을 설정
```jsp
<jsp:useBean id="user1" scope="request" class="com.nhnacademy.domain.User" />
<jsp:setProperty name="user1" property="age" value="35" />
```
```java
@NoArgsConstructor
@Getter
@Setter
public class User implements Serializable {
    private String name;
    private int age;
}
```
> <jsp:getProperty>
> 	- Java bean의 property 값을 반환

> Java Beans
> 	- 객체 지향 프로그래밍의 가장 큰 이점 중 하나는 다른 프로그램에서도 객체를 다시 사용할 수 있다는 것이다.
> 	- JavaBeans은 규격이 존재하여 엄격한 지침을 따라서 다른 객체와 아주 쉽게 쓰일 수 있게 된다.
> 	- 즉, JavaBeans는 java로 작성된 재사용 가능한 소프트웨어 컴포넌트이다.
> 
> POJO(Plain Old Java Object)
> 	- 2000년 9월에 마틴 파울러, 레베카 파슨, 조쉬 맥킨지 등이 사용하기 시작한 용어이다.
> 	- 특정 기술과 환경에 종속되어 의존하게 된 자바 코드는 가독성이 떨어져 유지보수가 어렵고 확장성이 매우 떨어지는 단점이 있다.
> 	- 주요 JAVA 오브젝트 모델, 컨벤션 또는 프레임워크를 따르지 않는 Java 오브젝트를 의미한다.
> 
> POJO 조건
> 	- 특정 규약에 종속
### 출처(참고 문헌)
-

### 연결 문서
-
