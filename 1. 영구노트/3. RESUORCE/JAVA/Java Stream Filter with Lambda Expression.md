### 주제 : Lambda Expression

### 날짜 : 2024-03-26 11:56
----
### 메모
#### 1. Introduction
> 이 간단한 튜토리얼에서는 Java에서 Stream을 다룰 때 `Stream.filter()` 메서드의 사용법에 대해 알아보겠습니다.
> 
> 이를 사용하는 방법과 확인된 예외의 특수한 경우를 처리하는 방법에 대해 살펴보겠습니다.
#### 2. Using Stream.filter()
> `filter()` 메서드는 주어진 Predicate와 일치하는 스트림 요소를 필터링하는 Stream 인터페이스의 중간 연산입니다.
```java
Stream<T> filter(Predicate<? super T> predicate)
```
> 이 작동 방식을 확인하기 위해 Customer 클래스를 생성해 보겠습니다:
```java
public class Customer {
    private String name;
    private int points;
    //Constructor and standard getters
}
```
> 게다가, 고객들의 컬렉션을 생성해 보겠습니다:
```java
Customer john = new Customer("John P.", 15);
Customer sarah = new Customer("Sarah M.", 200);
Customer charles = new Customer("Charles B.", 150);
Customer mary = new Customer("Mary T.", 1);

List<Customer> customers = Arrays.asList(john, sarah, charles, mary);
```
##### 2.1. Filtering Collections
> filter() 메서드의 일반적인 사용 사례는 컬렉션을 처리하는 것입니다.

100점 이상의 포인트를 가진 고객 목록을 만들어 봅시다. 이를 위해 람다 표현식을 사용할 수 있습니다:
##### 2.2. Filtering Collections with Multiple Criteria

#### 3. Handling Exceptions
##### 3.1. Using a Custom Wrapper 
##### 3.2. Using Throwing Function
### 출처(참고 문헌)
- [https://www.baeldung.com/java-stream-filter-lambda]

### 연결 문서
-
