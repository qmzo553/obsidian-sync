### 주제 : Functional Interfacces in Java 8

### 날짜 : 2024-03-26 08:01
----
### 메모
#### 1. Introduction
> 이 튜토리얼은 Java 8에 있는 다양한 함수형 인터페이스와 그들의 일반적인 사용 사례, 표준 JDK 라이브러리에서의 사용에 대한 가이드입니다.
#### 2. Lambdas in Java 8
> Java 8는 람다 표현식의 형태로 강력한 새로운 문법적 개선을 가져왔습니다. 람다는 익명 함수로, 일급 언어 시민으로 다룰 수 있습니다. 예를 들어, 메서드에 전달하거나 메서드에서 반환할 수 있습니다.
> 
> Java 8 이전에는 단일 기능을 캡슐화해야 할 경우에 매번 클래스를 생성하는 것이 일반적이었습니다. 이는 원시 함수 표현으로 사용되는 것을 정의하기 위해 많은 불필요한 보일러플레이트 코드를 의미했습니다.
> 
> “Lambda Expressions and Functional Interfaces: Tips and Best Practices”라는 기사는 더 자세히 함수형 인터페이스와 람다 사용에 대해 설명하고 있습니다. 이 가이드는 java.util.function 패키지에 있는 특정한 함수형 인터페이스에 초점을 맞추고 있습니다.
#### 3. Functional Interfaces
> 모든 함수형 인터페이스에는 정보를 제공하는 @FunctionalInterface 주석을 달아야 합니다. 이는 인터페이스의 목적을 명확하게 전달하며, 주석이 달린 인터페이스가 조건을 충족하지 않을 경우 컴파일러가 오류를 생성할 수 있도록 합니다.
#### 4. Functions
> SAM(Single Abstract Method)을 갖는 모든 인터페이스는 함수형 인터페이스이며, 해당 구현은 람다 표현식으로 처리될 수 있습니다.
> 
> Java 8의 기본 메서드는 추상적이지 않으며 세어지지 않습니다. 함수형 인터페이스는 여전히 여러 기본 메서드를 가질 수 있습니다. 이를 Function의 문서를 통해 확인할 수 있습니다.
#### 5. Primitive Function Specializations
> 가장 간단하고 일반적인 람다의 경우는 하나의 값만 받고 다른 값을 반환하는 메서드를 가진 함수형 인터페이스입니다. 이러한 단일 인수 함수는 인수와 반환 값의 유형에 의해 매개변수화된 Function 인터페이스에 의해 나타납니다:
```java
public interface Function<T, R> { … }
```
> 표준 라이브러리에서 Function 유형의 사용 중 하나는 Map.computeIfAbsent 메서드입니다. 이 메서드는 맵에서 키에 해당하는 값을 반환하지만, 키가 맵에 이미 존재하지 않는 경우 값 계산을 수행합니다. 값을 계산하기 위해 전달된 Function 구현을 사용합니다:
```java
Map<String, Integer> nameMap = new HashMap<>();
Integer value = nameMap.computeIfAbsent("John", s -> s.length());
```
> 이 경우에는 함수를 키에 적용하여 값을 계산하고, 맵 안에 넣고, 메서드 호출에서 반환할 것입니다. **전달된 값 유형과 반환된 값 유형과 일치하는 메서드 참조로 람다를 대체할 수 있습니다.**
> 
> 우리가 메서드를 호출하는 객체는 사실상 메서드의 암시적인 첫 번째 인수입니다. 이를 통해 인스턴스 메서드 length 참조를 Function 인터페이스로 캐스트할 수 있습니다.
```java
Integer value = nameMap.computeIfAbsent("John", String::length);
```
> Function 인터페이스에는 여러 함수를 결합하여 하나의 함수로 만들고 순차적으로 실행할 수 있는 기본 compose 메서드도 있습니다.
#### 6. Two-Arity Function Specializations
#### 7. Suppliers
#### 8. Consumers
#### 9. Predicates
#### 10. Operators
#### 11. Legacy Runctional Interfaces


### 출처(참고 문헌)
-

### 연결 문서
-
