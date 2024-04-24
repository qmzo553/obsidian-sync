### 주제 : maven scope

### 날짜 : 2024-04-24 22:42
----
### 메모

|      | compile | provided | runtime | test | system |     |
| ---- | ------- | -------- | ------- | ---- | ------ | --- |
| 컴파일시 | 포함      | 포함       | 미포함     | 미포함  |        |     |
| 런타임시 | 미포함     | 미포함      | 포함      | 미포함  |        |     |
| 테스트  | 안 나와 있음 | 포함       | 포함      | 포함   |        |     |
> Maven Scope
> 	- Maven Project에서 외부 라이브러리 및 모듈 사용을 위해 의존성을 설정한다.
> 	- 이때 scope section을 통해서 해당 의존성이 포함되는 시점을 결정할 수 있다.
> 
> Compile
> 	- 해당 프로젝트를 dependency로 불러온 다른 프로젝트에도 포함시킨다.
> 	- scope를 명시하지 않았을 때는 기본적으로 compile이 적용된다.
> 
> Provided
> 	- Java EE, Servlet Container, JDK와 같은 컨테이너(웹 애플리케이션 서버)에서 실행될때 제공됨
> 
> System
> 	- repository에서 검색되는 라이브러리가 아닌 직접 경로를 명시하여 JAR 파일을 

### 출처(참고 문헌)
-

### 연결 문서
-
