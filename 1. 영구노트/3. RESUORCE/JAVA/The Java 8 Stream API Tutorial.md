### 주제 : 

### 날짜 : 2024-03-25 12:11
----
### 메모
#### 1. Overview
> 이 포괄적인 튜토리얼에서는 Java 8 스트림의 실제 활용 방법을 생성부터 병렬 실행까지 살펴볼 것입니다. 이 자료를 이해하기 위해서는 독자들이 Java 8의 기본 지식(람다 표현식, Optional, 메서드 참조)과 Stream API를 가지고 있어야 합니다. 이러한 주제에 대해 더 익숙해지려면 이전의 기사인 "Java 8의 새로운 기능"과 "Java 8 스트림 소개"를 참조해주세요.
#### 2. Stream Creation
> 다양한 소스에서 스트림 인스턴스를 생성하는 여러 가지 방법이 있습니다. 한 번 생성된 인스턴스는 소스를 수정하지 않으므로 단일 소스에서 여러 인스턴스를 생성할 수 있습니다.
##### 2.1. Empty Stream
> 빈 스트림을 생성할 때는 `empty()` 메서드를 사용해야 합니다.
```java
Stream<String> streamEmpty = Stream.empty();
```
> 빈 요소를 가진 스트림을 반환하는 경우에는 null을 반환하지 않도록 `empty()` 메서드를 사용하는 것이 일반적입니다.
```java
public Stream<String> streamOf(List<String> list) {
	return list == null || list.isEmpty() ? Stream.empty() : list.stream();
}
```
##### 2.2. Stream Of Collection
> 우리는 컬렉션(Collection), 리스트(List), 세트(Set)와 같은 모든 종류의 컬렉션으로부터 스트림을 생성할 수도 있습니다.
```java
Collection<String> collection = Arrays.asList("a", "b", "c"); Stream<String> streamOfCollection = collection.stream();
```
##### 2.3. Stream of Array
> 배열 또한 스트림의 소스가 될 수 있습니다.
```java
Stream<String> streamOfArray = Stream.of("a", "b", "c");
```
> 기존 배열이나 배열의 일부를 사용하여 스트림을 생성할 수도 있습니다.
```java
String[] arr = new String[]{"a", "b", "c"};
Stream<String> streamOfArrayFull = Arrays.stream(arr);
Stream<String> streamOfArrayPart = Arrays.stream(arr, 1, 3);
```
##### 2.4. Stream.builder()
> 빌더를 사용할 때는 원하는 유형을 명시적으로 지정해야 합니다. 그렇지 않으면 `build()` 메서드가 `Stream<Object>`의 인스턴스를 생성합니다.
```java
Stream<String> streamBuilder = Stream.<String> builder().add("a").add("b").add("c").build();
```
##### 2.5. Stream.generate()
> `generate()` 메서드는 요소 생성을 위한 `Supplier<T>`를 인수로 받습니다. 결과 스트림이 무한하기 때문에 개발자는 원하는 크기를 명시해야 합니다. 그렇지 않으면 generate()4 메서드는 43메모리 한계에 도달할 때까지 작동합니다.
```java
Stream<String> streamGenerated = Stream.generate(() -> "element").limit(10);
```
> 위의 코드는 "element"라는 값을 가진 문자열을 10개 포함하는 시퀀스를 생성합니다.
##### 2.6. Stream.iterate()
> 무한 스트림을 생성하는 또 다른 방법은 `iterate()` 메서드를 사용하는 것입니다.
```java
Stream<Integer> streamIterated = Stream.iterate(40, n -> n + 2).limit(20);
```
##### 2.7. Streamof Primitives
##### 2.8. Stream of String
##### 2.9. Stream of File
#### 3. Referencing a Stream
#### 4. Stream Pipeline
#### 5. Lazy Invocation
#### 6. Order of Execution
#### 7. Stream Reduction
##### 7.1 The reduce() Method
##### 7.2. The collect() Method
#### 8. Parallel Streams
#### 9. Conclusion

### 출처(참고 문헌)
-

### 연결 문서
-
