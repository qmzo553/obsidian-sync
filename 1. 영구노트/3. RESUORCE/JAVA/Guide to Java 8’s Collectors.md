### 주제 : Collectors

### 날짜 : 2024-03-26 08:26
----
### 메모
#### 1. Overview
> 이 튜토리얼에서는 Java 8의 Collectors를 다룰 것입니다. 이는 Stream을 처리하는 마지막 단계에서 사용됩니다.
> 
> Stream API 자체에 대해 더 읽고 싶다면, 이 기사를 확인할 수 있습니다.
#### 2. The Stream.collect() Method
> `Stream.collect()`는 Java 8의 Stream API의 종단 메서드 중 하나입니다. 이를 사용하면 Stream 인스턴스에 보유된 데이터 요소에 대해 가변 fold 작업(요소를 일부 데이터 구조로 다시 패키징하고 추가 로직을 적용하거나 연결하는 등)을 수행할 수 있습니다.
> 
> 이 작업을 위한 전략은 Collector 인터페이스 구현을 통해 제공됩니다.
#### 3. Collectors
> 모든 미리 정의된 구현은 Collectors 클래스에서 찾을 수 있습니다. 이러한 구현을 활용하기 위해 일반적으로 다음과 같은 정적 임포트를 사용하는 것이 일반적입니다.
```java
import static java.util.stream.Collectors.*;
```
> 우리는 원하는 단일 임포트 컬렉터도 사용할 수 있습니다.
```java
import static java.util.stream.Collectors.toList;
import static java.util.stream.Collectors.toMap;
import static java.util.stream.Collectors.toSet;
```
> 다음 예제에서는 다음 목록을 재사용합니다:
```java
List<String> givenList = Arrays.asList("a", "bb", "ccc", "dd");
```
##### 3.1. Collectors.toList()
> toList 수집기는 모든 스트림 요소를 List 인스턴스로 수집하는 데 사용할 수 있습니다. 이 메서드로 특정 List 구현을 가정할 수 없다는 것을 기억하는 것이 중요합니다. 이를 더 제어하려면 toCollection을 사용할 수 있습니다.
> 
> 요소 시퀀스를 나타내는 Stream 인스턴스를 생성한 다음 이를 List 인스턴스로 수집해 보겠습니다:
```java
List<String> result = givenList.stream()
							.collect(toList());
```
###### 3.1.1. Collectors.toUnmodifiableList()
> Java 10에서는 Stream 요소를 변경할 수 없는 List로 누적하는 편리한 방법을 소개했습니다.
```java
List<String> result = givenList.stream()
							  .collect(toUnmodifiableList());
```
> 이제 결과 List를 수정하려고하면 UnsupportedOperationException이 발생합니다.
```java
assertThatThrownBy(() -> result.add("foo"))
							  .isInstanceOf(UnsupportedOperationException.class);
```
##### 3.2. Collectors.toSet()
> toList 수집기는 모든 Stream 요소를 List 인스턴스로 수집하는 데 사용할 수 있습니다. 이 방법으로 특정 List 구현을 가정할 수 없습니다. 더 많은 제어를 원한다면 toCollection을 사용할 수 있습니다.
> 
> 요소의 시퀀스를 나타내는 Stream 인스턴스를 생성 한 다음 이를 Set 인스턴스로 수집해 보겠습니다:
```java
Set<String> result = givenList.stream()
  .collect(toSet());
```
###### 3.2.1. Collectors.toUnmodifiableSet()
##### 3.3. Collectors.toCollection()
##### 3.4. Collectors.toMap()
###### 3.4.1. Collectors.toUnmodifiableMap()
##### 3.5. Collectors.collectingAndThen()
##### 3.6. Collectors.joining()
##### 3.7. Collectors.counting()
##### 3.8. Collectors.summarizingdouble / Long / Int()
##### 3.9. Collectors.averagingDouble / Long / int()
##### 3.10. Collectors.summingDouble / Long / int()
##### 3.11. Collectors.maxBy() / minBy()
##### 3.12. Collectors.groupingBy()
##### 3.13. Collectors.partitioningBy()
##### 3.14. Collectors.teeing()
#### 4. Custom Collectors


### 출처(참고 문헌)
- [https://www.baeldung.com/java-8-collectors]

### 연결 문서
-
