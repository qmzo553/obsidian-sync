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
> 결과 스트림의 첫 번째 요소는 iterate() 메서드의 첫 번째 매개변수입니다. 다음 요소를 생성할 때마다 지정된 함수가 이전 요소에 적용됩니다. 위의 예제에서 두 번째 요소는 42가 됩니다.
##### 2.7. Stream of Primitives
> Java 8에서는 세 가지 기본 유형(int, long 및 double)의 스트림을 생성할 수 있는 기능을 제공합니다. `Stream<T>`는 제네릭 인터페이스이므로 제네릭과 기본 유형을 형식 매개변수로 사용할 수 없습니다. 따라서 IntStream, LongStream, DoubleStream 세 가지 새로운 특수 인터페이스가 만들어졌습니다. 새로운 인터페이스를 사용하면 불필요한 자동 박싱을 줄일 수 있어 생산성이 향상됩니다.
```java
IntStream intStream = IntStream.range(1, 3); LongStream longStream = LongStream.rangeClosed(1, 3);
```
> range(int startInclusive, int endExclusive) 메서드는 첫 번째 매개변수부터 두 번째 매개변수까지의 정렬된 스트림을 생성합니다. 연속 요소의 값을 1씩 증가시킵니다. 결과에는 마지막 매개변수가 포함되지 않습니다. 이것은 시퀀스의 상한만을 나타냅니다.
> 
> rangeClosed(int startInclusive, int endInclusive) 메서드는 두 번째 매개변수가 포함된다는 점을 제외하고 동일한 작업을 수행합니다. 이 두 메서드를 사용하여 기본 유형의 스트림을 생성할 수 있습니다.
> 
> Java 8부터 Random 클래스는 기본 유형의 스트림을 생성하기 위한 다양한 메서드를 제공합니다. 예를 들어, 다음 코드는 세 개의 요소를 포함하는 DoubleStream을 생성합니다:
```java
Random random = new Random();
DoubleStream doubleStream = random.doubles(3);
```
##### 2.8. Stream of String
> 우리는 또한 String을 스트림을 생성하는 소스로 사용할 수 있습니다. 이를 위해 String 클래스의 chars() 메서드를 사용합니다. JDK에는 CharStream을 나타내는 인터페이스가 없기 때문에, 대신 IntStream을 사용하여 문자 스트림을 나타냅니다.
```java
IntStream streamOfChars = "abc".chars();
```
> 다음 예제는 지정된 정규식에 따라 문자열을 하위 문자열로 분할합니다:
```java
Stream<String> streamOfString = Pattern.compile(", ").splitAsStream("a, b, c");
```
##### 2.9. Stream of File
> 또한 Java NIO 클래스 Files를 사용하여 lines() 메서드를 통해 텍스트 파일의 `Stream<String>`을 생성할 수 있습니다. 텍스트의 각 줄은 스트림의 요소가 됩니다.
```java
Path path = Paths.get("C:\\file.txt");
Stream<String> streamOfStrings = Files.lines(path);
Stream<String> streamWithCharset = Files.lines(path, Charset.forName("UTF-8")); 
```
> Charset은 `lines()` 메서드의 인수로 지정할 수 있습니다.
#### 3. Referencing a Stream
> 중간 연산만 호출되는 한 스트림을 인스턴스화하고 액세스 가능한 참조를 가질 수 있습니다. 최종 연산을 실행하면 스트림에 액세스할 수 없습니다. 이를 설명하기 위해 일련의 작업을 연결하는 것이 최선의 방법이라는 것을 잠시 잊어 보겠습니다. 불필요한 번잡함은 있지만, 기술적으로 다음 코드는 유효합니다.
```java
Stream<String> stream = Stream.of("a", "b", "c").filter(element -> element.contains("b")); Optional<String> anyElement = stream.findAny();
```
>   그러나 최종 작업을 호출한 후에 동일한 참조를 재사용하려고 시도하면 IllegalStateException이 발생합니다.
```java
Optional<String> firstElement = stream.findFirst();
```
> IllegalStateException은 RuntimeException이므로 컴파일러가 문제를 신호화하지 않습니다. 따라서 Java 8 스트림을 재사용할 수 없다는 것을 기억하는 것이 매우 중요합니다.
> 
> 이러한 종류의 동작은 논리적입니다. 우리는 스트림을 함수형 스타일로 요소 소스에 대한 유한한 일련의 작업을 적용하기 위해 설계했기 때문에 요소를 저장하기 위한 것이 아닙니다.
> 
> 따라서 이전 코드가 올바르게 작동하도록 하려면 몇 가지 변경이 필요합니다:
```java
List<String> elements = Stream.of("a", "b", "c")
								.filter(element -> element.contains("b"))
								.collect(Collectors.toList());
Optional<String> anyElement = elements.stream().findAny();
Optional<String> firstElement = elements.stream().findFirst();
```
#### 4. Stream Pipeline
> 데이터 소스의 요소에 대해 일련의 작업을 수행하고 결과를 집계하려면 세 가지 부분이 필요합니다: 소스, 중간 작업 및 최종 작업입니다.
> 중간 작업은 새로운 수정된 스트림을 반환합니다. 예를 들어, 기존 스트림에서 일부 요소를 제외한 새로운 스트림을 생성하려면 `skip()` 메서드를 사용해야 합니다:
```java
Stream<String> onceModifiedStream = Stream.of("abcd", "bbcd", "cbcd").skip(1);
```

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
