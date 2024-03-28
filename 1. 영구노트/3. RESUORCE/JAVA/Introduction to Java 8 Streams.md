### 주제 : Stream 기초

### 날짜 : 2024-03-25 08:30
----
### 메모
#### 1. Overview
> 이 문서에서는 Java 8에서 추가된 주요 기능 중 하나인 "스트림"에 대해 간단히 살펴보겠습니다.
> 스트림이란 무엇인지 설명하고, 간단한 예제를 통해 스트림의 생성과 기본적인 작업을 소개하겠습니다.

#### 2. Stream API
> Java 8에서의 주요 새로운 기능 중 하나는 스트림 기능(`java.util.stream`)의 도입입니다. 이 기능은 요소 시퀀스를 처리하기 위한 클래스를 포함합니다.
> 중심 API 클래스는 `Stream<T>`입니다. 다음 섹션에서는 기존 데이터 제공 소스를 사용하여 스트림을 생성하는 방법을 보여줍니다.
 
##### 2.1. Stream Creation
>  다양한 요소 소스에서 스트림을 생성할 수 있습니다. 예를 들어, 컬렉션 또는 배열에서 `stream()` 및 `of()` 메서드를 사용할 수 있습니다:
```java
String[] arr = new String[]{"a", "b", "c"};
Stream<String> stream = Arrays.stream(arr);
stream = Stream.of("a", "b", "c");
```
>  **`Collection` 인터페이스에는 `stream()` 기본 메서드가 추가되었으며, 이를 통해 어떤 컬렉션도 요소 소스로 사용하여 `Stream<T>`를 생성할 수 있습니다.**
``` java
Stream<String> stream = list.stream();
```
##### 2.2. Multi-threading With Streams
>  **Stream API는 `parallelStream()` 메서드를 제공하여 스트림의 요소를 병렬 모드로 처리하여 다중 스레딩을 간단하게 할 수 있습니다.**
>  아래 코드는 스트림의 각 요소에 대해 `doWork()` 메서드를 병렬로 실행할 수 있도록 합니다:
```java
list.parallelStream().forEach(element -> doWork(element));
```
>  다음 섹션에서는 기본적인 Stream API 작업을 소개하겠습니다.

#### 3. Stream Operations
> 스트림에서 수행할 수 있는 많은 유용한 작업이 있습니다.
> 스트림 작업은 중간 작업(intermediate operations)과 최종 작업(terminal operations)으로 나뉩니다. 
> 중간 작업은 `Stream<T>`를 반환하고, 최종 작업은 확정된 유형의 결과를 반환합니다.
> 중간 작업은 연결(chain)할 수 있습니다.
> 또한 스트림의 작업은 소스를 변경하지 않는다는 것도 주목할 가치가 있습니다.
> 다음은 간단한 예시입니다:
```java
long count = list.stream().distinct().count();
```
> 그렇습니다. `distinct()` 메서드는 이전 스트림의 고유한 요소로 구성된 새로운 스트림을 생성하는 중간 작업을 나타내며, `count()` 메서드는 스트림의 크기를 반환하는 최종 작업을 나타냅니다.

##### 3.1. Iterating
>  스트림 API는 for, for-each 및 while 루프를 대체하는 데 도움이 됩니다. 이를 통해 요소 시퀀스를 반복하는 것이 아니라 작업 로직에 집중할 수 있습니다. 예를 들어:
```java
for (String string : list) {
	if (string.contains("a")) {
		 return true; 
	} 
}
```
> 이 코드는 Java 8 코드 한 줄로 변경할 수 있습니다:
```java
boolean isExist = list.stream().anyMatch(element -> element.contains("a"));
```

##### 3.2. Filtering
> `filter()` 메서드는 주어진 조건을 만족하는 요소로 이루어진 스트림을 선택할 수 있도록 합니다.
>  예를 들어, 다음 리스트를 고려해보겠습니다:
```java
ArrayList<String> list = new ArrayList<>();
list.add("One");
list.add("OneAndOnly");
list.add("Derek");
list.add("Change");
list.add("factory");
list.add("justBefore");
list.add("Italy");
list.add("Italy");
list.add("Thursday");
list.add("");
list.add("");
```
>  아래 코드는 `List<String>`의 `Stream<String>`을 생성하고, 이 스트림에서 "d" 문자를 포함하는 모든 요소를 찾아 필터링된 요소만 포함하는 새로운 스트림을 생성합니다:
```java
Stream<String> stream = list.stream().filter(element -> element.contains("d"));
```

##### 3.3. Mapping
>  특별한 함수를 적용하여 스트림의 요소를 변환하고, 이러한 새로운 요소들을 스트림으로 수집하기 위해 `map()` 메서드를 사용할 수 있습니다.
```java
List<String> uris = new ArrayList<>();
uris.add("C:\\My.txt");
Stream<Path> stream = uris.stream().map(uri -> Paths.get(uri));
```
>  따라서 위의 코드는 초기 스트림의 각 요소에 특정 람다 표현식을 적용하여 `Stream<String>`을 `Stream<Path>`로 변환합니다.
>  만약 각 요소가 자체 시퀀스의 요소를 포함하고 있고, 이러한 내부 요소들의 스트림을 생성하려면 `flatMap()` 메서드를 사용해야 합니다.
```java
List<Detail> details = new ArrayList<>();
details.add(new Detail());
Stream<String> stream = details.stream().flatMap(detail ->
												 detail.getParts().stream());
```
>  이 예시에서는 Detail 유형의 요소 목록이 있습니다. Detail 클래스에는 `List<String>`인 PARTS 필드가 포함되어 있습니다. `flatMap()` 메서드를 사용하여 PARTS 필드의 각 요소가 추출되고 새로운 결과 스트림에 추가됩니다. 그 후에는 초기 `Stream<Detail>`이 손실됩니다.
##### 3.4. Matching
> 스트림 API는 일련의 요소를 일정한 조건에 따라 유효성 검사할 수 있는 편리한 도구를 제공합니다. 이를 위해 다음 중 하나의 메서드를 사용할 수 있습니다: `anyMatch(), allMatch(), noneMatch().` 이들의 이름은 자명합니다. 이들은 불리언을 반환하는 최종 작업입니다.
```java
boolean isValid = list.stream().anyMatch(element -> element.contains("h")); // true boolean
isValidOne = list.stream().allMatch(element -> element.contains("h")); // false boolean
isValidTwo = list.stream().noneMatch(element -> element.contains("h"));  // false
```
> 예시로 빈 스트림에 대해 allMatch() 메서드를 사용하면 어떤 조건이 주어져도 true를 반환합니다.
```java
Stream.empty().allMatch(Objects::nonNull); // true
```
> 이것은 합리적인 기본값입니다. 왜냐하면 우리는 주어진 조건을 만족시키지 않는 요소를 찾을 수 없기 때문입니다.
> 마찬가지로, anyMatch() 메서드는 빈 스트림에 대해 항상 false를 반환합니다.
```java
Stream.empty().anyMatch(Objects::nonNull); // false
```
> 마찬가지로, 이는 합리적인 동작입니다. 왜냐하면 이 조건을 만족하는 요소를 찾을 수 없기 때문입니다.
##### 3.5. Reduction
> 스트림 API는 지정된 함수에 따라 일련의 요소를 어떤 값으로 줄이는 데 도움이 되는 `reduce()` 메서드를 제공합니다. 이 메서드는 두 개의 매개변수를 사용합니다: 첫 번째는 시작 값이고, 두 번째는 누산기 함수입니다.
> 예를 들어, `List<Integer>`가 있고 이 모든 요소의 합과 초기 Integer(이 예제에서는 23)을 가지고 싶다고 가정해보세요. 그렇다면 다음 코드를 실행할 수 있고 결과는 26이 될 것입니다 (23 + 1 + 1 + 1).
```java
List<Integer> integers = Arrays.asList(1, 1, 1);
Integer reduced = integers.stream().reduce(23, (a, b) -> a + b);
```
##### 3.6. Collecting
> 축소 작업은 Stream 유형의 collect() 메서드를 통해서도 제공될 수 있습니다. 이 작업은 스트림을 컬렉션이나 맵으로 변환하거나 스트림을 단일 문자열 형태로 표현할 때 매우 편리합니다. 거의 모든 일반적인 수집 작업에 대한 솔루션을 제공하는 유틸리티 클래스인 Collectors가 있습니다. 일부 복잡한 작업에 대해서는 사용자 정의 Collector를 만들 수도 있습니다.
```java
List<String> resultList = 
	list.stream()
		.map(element -> element.toUpperCase())
		.collect(Collectors.toList());
```
> 다음 코드는 `Stream<String>`을 `List<String>`으로 축소하기 위해 최종 `collect()` 작업을 사용합니다.
### 출처(참고 문헌)
- [https://www.baeldung.com/java-8-streams-introduction]

### 연결 문서
-
