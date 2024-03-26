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
> `filter()` 메서드의 일반적인 사용 사례는 컬렉션을 처리하는 것입니다.
> 
> 100점 이상의 포인트를 가진 고객 목록을 만들어 봅시다. 이를 위해 람다 표현식을 사용할 수 있습니다:
```java
List<Customer> customersWithMoreThan100Points = customers
  .stream()
  .filter(c -> c.getPoints() > 100)
  .collect(Collectors.toList());
```
> 메서드 참조를 사용할 수도 있습니다. 이는 람다 표현식의 축약형입니다:
```java
List<Customer> customersWithMoreThan100Points = customers
  .stream()
  .filter(Customer::hasOverHundredPoints)
  .collect(Collectors.toList());
```
> 이 경우에는 Customer 클래스에 hasOverHundredPoints 메서드를 추가했습니다:
```java
public boolean hasOverHundredPoints() {
    return this.points > 100;
}
```
> 두 경우 모두 동일한 결과를 얻습니다:
```java
assertThat(customersWithMoreThan100Points).hasSize(2);
assertThat(customersWithMoreThan100Points).contains(sarah, charles);
```
##### 2.2. Filtering Collections with Multiple Criteria
> 또한 `filter()`를 사용하여 여러 조건을 사용할 수 있습니다. 예를 들어, 포인트와 이름으로 필터링할 수 있습니다:
```java
List<Customer> charlesWithMoreThan100Points = customers
  .stream()
  .filter(c -> c.getPoints() > 100 && c.getName().startsWith("Charles"))
  .collect(Collectors.toList());

assertThat(charlesWithMoreThan100Points).hasSize(1);
assertThat(charlesWithMoreThan100Points).contains(charles);
```

#### 3. Handling Exceptions
> 지금까지 우리는 예외를 throw하지 않는 predicate와 함께 filter를 사용해 왔습니다. 실제로 Java의 함수형 인터페이스는 확인된 예외나 확인되지 않은 예외를 선언하지 않습니다.
> 
> 다음으로, 람다 표현식에서 예외를 처리하는 다양한 방법을 보여드리겠습니다.
##### 3.1. Using a Custom Wrapper 
> 먼저, Customer에 profilePhotoUrl을 추가하겠습니다:
```java
private String profilePhotoUrl;
```
> 게다가, 프로필의 가용성을 확인하는 간단한 `hasValidProfilePhoto()` 메서드를 추가하겠습니다:
```java
public boolean hasValidProfilePhoto() throws IOException {
    URL url = new URL(this.profilePhotoUrl);
    HttpsURLConnection connection = (HttpsURLConnection) url.openConnection();
    return connection.getResponseCode() == HttpURLConnection.HTTP_OK;
}
```
##### 3.2. Using Throwing Function
### 출처(참고 문헌)
- [https://www.baeldung.com/java-stream-filter-lambda]

### 연결 문서
-
