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
##### 3.1. Collectors.toList()
###### 3.1.1. Collectors.toUnmodifiableList()
##### 3.2. Collectors.toSet()
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
