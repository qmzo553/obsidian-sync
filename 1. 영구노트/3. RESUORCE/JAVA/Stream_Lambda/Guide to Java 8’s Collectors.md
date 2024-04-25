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
> Set은 중복 요소를 포함하지 않습니다. 우리의 컬렉션에 서로 동일한 요소가 포함되어 있으면, 결과 Set에는 한 번만 나타납니다. 아래는 이를 보여주는 예제 코드입니다:
```java
List<String> listWithDuplicates = Arrays.asList("a", "bb", "c", "d", "bb");
Set<String> result = listWithDuplicates.stream().collect(toSet());
assertThat(result).hasSize(4);
```
###### 3.2.1. Collectors.toUnmodifiableSet()
> Java 10부터는 toUnmodifiableSet() 수집기를 사용하여 변경할 수 없는 Set을 쉽게 만들 수 있습니다. 아래는 이를 사용하는 예제 코드입니다:
```java
Set<String> result = givenList.stream()
							  .collect(toUnmodifiableSet());
```
> 다음은 수정 시도가 UnsupportedOperationException으로 끝날 것임을 나타냅니다:
```java
assertThatThrownBy(() -> result.add("foo"))
							  .isInstanceOf(UnsupportedOperationException.class);
```
##### 3.3. Collectors.toCollection()
> 우리가 이미 언급한 바와 같이, toSet 및 toList 수집기를 사용할 때, 그들의 구현에 대해 가정을 할 수 없습니다. 사용자 정의 구현을 사용하려면 선택한 컬렉션을 제공하여 toCollection 수집기를 사용해야 합니다.
> 
> 이제 요소 시퀀스를 나타내는 Stream 인스턴스를 생성하고, 그것들을 LinkedList 인스턴스로 수집해 봅시다:
```java
List<String> result = givenList.stream()
							  .collect(toCollection(LinkedList::new))
```
> 이는 변경할 수 없는 컬렉션과는 작동하지 않음을 주의하세요. 이런 경우에는 사용자 정의 수집기 구현을 작성하거나 collectingAndThen을 사용해야 합니다.
##### 3.4. Collectors.toMap()
> toMap 수집기는 Stream 요소를 Map 인스턴스로 수집하는 데 사용할 수 있습니다. 이를 위해 두 가지 함수를 제공해야 합니다:
> 
> - keyMapper
> - valueMapper
  >
  우리는 keyMapper를 사용하여 Stream 요소에서 Map 키를 추출하고, valueMapper를 사용하여 주어진 키에 연관된 값을 추출할 것입니다.
>
> 이제 그 요소들을 문자열을 키로 하고 그 길이를 값으로 하는 Map으로 수집해 봅시다:
```java
Map<String, Integer> result = givenList.stream()
									.collect(toMap(Function.identity(), String::length));
```
###### 3.4.1. Collectors.toUnmodifiableMap()
> 리스트와 세트와 유사하게, Java 10에서는 Stream 요소를 변경할 수 없는 맵으로 수집하는 간단한 방법을 소개했습니다.
```java
Map<String, Integer> result = givenList.stream()
						.collect(toUnmodifiableMap(Function.identity(), String::length));
```
> 우리가 볼 수 있듯이, 결과 맵에 새 항목을 넣으려고 하면 UnsupportedOperationException을 받게 됩니다.
```java
assertThatThrownBy(() -> result.put("foo", 3))
							.isInstanceOf(UnsupportedOperationException.class);
```
##### 3.5. Collectors.collectingAndThen()
> CollectingAndThen은 수집이 끝난 후 결과에 대해 바로 다른 작업을 수행할 수 있게 해주는 특별한 수집기입니다.
> 
> 스트림 요소를 List 인스턴스로 수집한 다음 결과를 ImmutableList 인스턴스로 변환해 봅시다.
```java
List<String> result = givenList.stream()
						  .collect(collectingAndThen(toList(), ImmutableList::copyOf))
```
##### 3.6. Collectors.joining()
> Joining 수집기는 `Stream<String>` 요소를 결합하는 데 사용할 수 있습니다.
> 
> 다음과 같이 그들을 함께 결합할 수 있습니다:
```java
String result = givenList.stream()
						.collect(joining());
```
> 결과는 다음과 같습니다:
```java
"abbcccdd"
```
> 우리는 사용자 정의 구분 기호, 접두사, 접미사를 지정할 수도 있습니다:
```java
String result = givenList.stream()
						.collect(joining(" "));
```
> 결과는 다음과 같습니다:
```java
"a bb ccc dd"
```
> 우리는 또한 다음과 같이 작성할 수도 있습니다:
```java
String result = givenList.stream()
					  .collect(joining(" ", "PRE-", "-POST"));
```
>  결과는 다음과 같습니다:
```java
"PRE-a bb ccc dd-POST"
```
##### 3.7. Collectors.counting()
> Counting은 모든 스트림 요소의 개수를 세는 간단한 수집기입니다.
> 
> 이제 다음과 같이 작성할 수 있습니다:
```java
Long result = givenList.stream()
					  .collect(counting());
```
##### 3.8. Collectors.summarizingdouble / Long / Int()
> SummarizingDouble/Long/Int는 추출된 요소의 숫자 데이터에 대한 통계 정보를 포함하는 특수한 클래스를 반환하는 수집기입니다.
> 
> 문자열 길이에 대한 정보를 얻을 수 있습니다. 다음과 같이 수행합니다:
```java
DoubleSummaryStatistics result = givenList.stream()
										  .collect(summarizingDouble(String::length));
```
> 이 경우에는 다음이 참일 것입니다:
```java
assertThat(result.getAverage()).isEqualTo(2);
assertThat(result.getCount()).isEqualTo(4);
assertThat(result.getMax()).isEqualTo(3);
assertThat(result.getMin()).isEqualTo(1);
assertThat(result.getSum()).isEqualTo(8);
```
##### 3.9. Collectors.averagingDouble / Long / int()
> AveragingDouble/Long/Int는 추출된 요소의 평균을 반환하는 수집기입니다.
> 
> 다음과 같이 문자열 길이의 평균을 구할 수 있습니다:
```java
Double result = givenList.stream()
						.collect(averagingDouble(String::length));
```
##### 3.10. Collectors.summingDouble / Long / int()
> SummingDouble/Long/Int는 추출된 요소의 합을 반환하는 수집기입니다.
```java
Double result = givenList.stream()
						.collect(summingDouble(String::length));
```
##### 3.11. Collectors.maxBy() / minBy()
> MaxBy/MinBy 수집기는 제공된 Comparator 인스턴스에 따라 스트림의 가장 큰/가장 작은 요소를 반환합니다.
> 
> 다음과 같이 가장 큰 요소를 선택할 수 있습니다:
```java
Optional<String> result = givenList.stream()
								  .collect(maxBy(Comparator.naturalOrder()));
```
> 우리는 반환된 값이 Optional 인스턴스로 래핑되어 있음을 볼 수 있습니다. 이는 사용자가 빈 컬렉션 코너 케이스를 다시 생각하도록 강제합니다.
##### 3.12. Collectors.groupingBy()
> GroupingBy 수집기는 어떤 속성에 따라 객체를 그룹화한 다음 결과를 Map 인스턴스에 저장하는 데 사용됩니다.
> 
> 우리는 문자열 길이에 따라 그룹화하고, 그룹화된 결과를 Set 인스턴스에 저장할 수 있습니다:
```java
Map<Integer, Set<String>> result = givenList.stream()
										  .collect(groupingBy(String::length, toSet()));
```
> 이로 인해 다음이 참이 됩니다:
```java
assertThat(result)
.containsEntry(1, newHashSet("a"))
.containsEntry(2, newHashSet("bb", "dd"))
.containsEntry(3, newHashSet("ccc"));
```
> 우리는 groupingBy 메서드의 두 번째 인수가 수집기라는 것을 볼 수 있습니다. 게다가, 우리는 자유롭게 원하는 수집기를 사용할 수 있습니다.
##### 3.13. Collectors.partitioningBy()
> PartitioningBy는 Predicate 인스턴스를 허용하고, 그런 다음 Stream 요소를 Boolean 값을 키로, 컬렉션을 값으로 저장하는 Map 인스턴스로 수집하는 groupingBy의 특수한 경우입니다. "true" 키 아래에는 주어진 Predicate와 일치하는 요소의 컬렉션이 있고, "false" 키 아래에는 주어진 Predicate와 일치하지 않는 요소의 컬렉션이 있습니다.
> 
> 다음과 같이 작성할 수 있습니다:
```java
Map<Boolean, List<String>> result = givenList.stream()
										.collect(partitioningBy(s -> s.length() > 2));
```
> 이렇게 하면 다음과 같은 맵이 생성됩니다:
```java
{false=["a", "bb", "dd"], true=["ccc"]}
```
##### 3.14. Collectors.teeing()
> 지금까지 배운 수집기를 사용하여 주어진 스트림에서 최대 및 최소 숫자를 찾아봅시다:
```java
List<Integer> numbers = Arrays.asList(42, 4, 2, 24);
Optional<Integer> min = numbers.stream().collect(minBy(Integer::compareTo));
Optional<Integer> max = numbers.stream().collect(maxBy(Integer::compareTo));
// do something useful with min and max
```
> 여기서는 두 가지 다른 수집기를 사용하고, 그 두 가지의 결과를 결합하여 의미 있는 결과물을 만들고 있습니다. Java 12 이전에는 이와 같은 사용 사례를 다루기 위해 주어진 스트림에 대해 두 번 작업하고 중간 결과를 임시 변수에 저장한 다음 이러한 결과를 결합해야 했습니다.
> 
> 다행히도, Java 12는 이러한 단계를 대신 처리해주는 내장 수집기를 제공합니다. 우리가 해야 할 일은 두 개의 수집기와 결합 함수를 제공하는 것뿐입니다.
> 
> 이 새로운 수집기는 주어진 스트림을 두 가지 다른 방향으로 향하게 하기 때문에 teeing이라고 불립니다:
```java
numbers.stream().collect(teeing(
  minBy(Integer::compareTo), // The first collector
  maxBy(Integer::compareTo), // The second collector
  (min, max) -> // Receives the result from those collectors and combines them
));
```
#### 4. Custom Collectors
> 만약 우리가 자체적인 Collector 구현을 작성하려면, Collector 인터페이스를 구현하고 그 세 가지 제네릭 매개변수를 명시해야 합니다:
```java
public interface Collector<T, A, R> {...}
```
> 매개변수를 세 가지로 명시해야 합니다:
> 
> - T: 수집 대상 객체의 유형
> - A: 변경 가능한 누산기 객체의 유형
> - R: 최종 결과의 유형
> 
> 이제 올바른 유형을 지정하여 요소를 ImmutableSet 인스턴스로 수집하는 예제 수집기를 작성해 보겠습니다:
```java
private class ImmutableSetCollector<T>
  implements Collector<T, ImmutableSet.Builder<T>, ImmutableSet<T>> {...}
```
> 내부 수집 작업 처리에 변경 가능한 컬렉션이 필요하기 때문에 ImmutableSet을 사용할 수 없습니다. 대신 다른 변경 가능한 컬렉션 또는 우리를 위해 임시로 객체를 축적할 수 있는 다른 클래스를 사용해야 합니다. 이 경우에는 ImmutableSet.Builder를 사용하겠습니다. 이제 5개의 메서드를 구현해야 합니다:
> 
> - `Supplier<ImmutableSet.Builder<T>> supplier()`
> - `BiConsumer<ImmutableSet.Builder<T>, T> accumulator()`
> - `BinaryOperator<ImmutableSet.Builder<T>> combiner()`
> - `Function<ImmutableSet.Builder<T>, ImmutableSet<T>> finisher()`
> - `Set<Characteristics> characteristics()`
> 
> `supplier()` 메서드는 빈 누산기 인스턴스를 생성하는 Supplier 인스턴스를 반환합니다. 따라서 이 경우에는 간단히 다음과 같이 작성할 수 있습니다:
```java
@Override
public Supplier<ImmutableSet.Builder<T>> supplier() {
    return ImmutableSet::builder;
}
```
> `accumulator()` 메서드는 새로운 요소를 기존의 누산기 객체에 추가하는 데 사용되는 함수를 반환합니다. 그래서 단순히 Builder의 add 메서드를 사용하겠습니다:
```java
@Override
public BiConsumer<ImmutableSet.Builder<T>, T> accumulator() {
    return ImmutableSet.Builder::add;
}
```
> `combiner()` 메서드는 두 개의 누산기를 병합하는 데 사용되는 함수를 반환합니다:
```java
@Override
public BinaryOperator<ImmutableSet.Builder<T>> combiner() {
    return (left, right) -> left.addAll(right.build());
}
```
> `finisher()` 메서드는 누산기를 최종 결과 유형으로 변환하는 데 사용되는 함수를 반환합니다. 이 경우에는 Builder의 build 메서드를 사용하겠습니다:
```java
@Override
public Function<ImmutableSet.Builder<T>, ImmutableSet<T>> finisher() {
    return ImmutableSet.Builder::build;
}
```
> `characteristics()` 메서드는 Stream에 내부 최적화에 사용되는 추가 정보를 제공하는 데 사용됩니다. 이 경우에는 Set에서 요소의 순서에 주의를 기울이지 않으므로 Characteristics.UNORDERED를 사용합니다. 이 주제에 대한 자세한 정보를 얻으려면 Characteristics의 JavaDoc을 확인하세요:
```java
@Override public Set<Characteristics> characteristics() {
    return Sets.immutableEnumSet(Characteristics.UNORDERED);
}
```
> 다음은 완전한 구현과 사용 예제입니다:
```java
public class ImmutableSetCollector<T>
  implements Collector<T, ImmutableSet.Builder<T>, ImmutableSet<T>> {

@Override
public Supplier<ImmutableSet.Builder<T>> supplier() {
    return ImmutableSet::builder;
}

@Override
public BiConsumer<ImmutableSet.Builder<T>, T> accumulator() {
    return ImmutableSet.Builder::add;
}

@Override
public BinaryOperator<ImmutableSet.Builder<T>> combiner() {
    return (left, right) -> left.addAll(right.build());
}

@Override
public Function<ImmutableSet.Builder<T>, ImmutableSet<T>> finisher() {
    return ImmutableSet.Builder::build;
}

@Override
public Set<Characteristics> characteristics() {
    return Sets.immutableEnumSet(Characteristics.UNORDERED);
}

public static <T> ImmutableSetCollector<T> toImmutableSet() {
    return new ImmutableSetCollector<>();
}
```
> 마지막으로, 여기서 실제로 동작하는 것을 확인할 수 있습니다:
```java
List<String> givenList = Arrays.asList("a", "bb", "ccc", "dddd");

ImmutableSet<String> result = givenList.stream()
									  .collect(toImmutableSet());
```
### 출처(참고 문헌)
- [https://www.baeldung.com/java-8-collectors]

### 연결 문서
-
