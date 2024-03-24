### 주제 : Stream 기초

### 날짜 : 2024-03-25 08:30
----
### 메모
> Overview
> 이 문서에서는 Java 8에서 추가된 주요 기능 중 하나인 "스트림"에 대해 간단히 살펴보겠습니다.
> 스트림이란 무엇인지 설명하고, 간단한 예제를 통해 스트림의 생성과 기본적인 작업을 소개하겠습니다.

> Stream API
> Java 8에서의 주요 새로운 기능 중 하나는 스트림 기능(`java.util.stream`)의 도입입니다. 이 기능은 요소 시퀀스를 처리하기 위한 클래스를 포함합니다.
> 중심 API 클래스는 `Stream<T>`입니다. 다음 섹션에서는 기존 데이터 제공 소스를 사용하여 스트림을 생성하는 방법을 보여줍니다.
 
> 1. Stream Creation
>  다양한 요소 소스에서 스트림을 생성할 수 있습니다. 예를 들어, 컬렉션 또는 배열에서 `stream()` 및 `of()` 메서드를 사용할 수 있습니다:
```
String[] arr = new String[]{"a", "b", "c"};
Stream<String> stream = Arrays.stream(arr);
stream = Stream.of("a", "b", "c");
```
>  **`Collection` 인터페이스에는 `_stream()_` 기본 메서드가 추가되었으며, 이를 통해 어떤 컬렉션도 요소 소스로 사용하여 `_Stream<T>_`를 생성할 수 있습니다.**
``` 
Stream<String> stream = list.stream();
``` 
> 2. Multi-threading With Streams
>  **Stream API는 parallelStream() 메서드를 제공하여 스트림의 요소를 병렬 모드로 처리하여 다중 스레딩을 간단하게 할 수 있습니다.**
>  아래 코드는 스트림의 각 요소에 대해 doWork() 메서드를 병렬로 실행할 수 있도록 합니다:
```
list.parallelStream().forEach(element -> doWork(element));
```
>  다음 섹션에서는 기본적인 Stream API 작업을 소개하겠습니다.
### 출처(참고 문헌)
- [https://www.baeldung.com/java-8-streams-introduction]

### 연결 문서
-
