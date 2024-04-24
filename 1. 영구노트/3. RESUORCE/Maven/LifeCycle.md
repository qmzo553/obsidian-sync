### 주제 : maven lifecycle

### 날짜 : 2024-04-24 22:08
----
### 메모
> Maven
> 	- maven은 다음 4가지 개념들을 기반으로 한다.
> 	- Plugin
> 	- Goal
> 	- Phase
> 	- LifeCycle
> 
> LifeCycle
> 	- 3가지 LifeCycle을 제공한다. (Clean, Default, Site)
> 	- 각 Build LifeCycle은 사전에 정의된 Phase들을 가지고 있다.
> 		1. Clean - 3개
> 		2. Default - 21개
> 		3. Site - 4개
> 
> Phase
> 	- Phase 순서에 따라 Phase에 바인딩된 Goal이 실행되는 구조를 가지고 있다.
> 	- 각 Phase는 의존관께를 가지고 있으며 순서대로 실행이 되어야 한다.
> 	- Phase에 아무런 Goal이 없다면 해당 Phase는 실행이 되지 않는다.
> 	- Phase에 Goal을 바인딩하기 위해서는 Plugin을 추가해야 한다.
> 
> Clean
> 	- 프로젝트의 결과물/산출물을 제거
> 	- 기본적으로 Maven은 target 폴더를 새로 생성하여 산출물을 저장하기 때문에 target폴더를 삭제
> 
> Default
> 	- 소스코드 컴파일, 테스트, 압축(패키징), 배포
> 	![[img1.daumcdn.jpg]]
> 
> Site
> 	- 프로젝트의 웹 사이트 생성

### 출처(참고 문헌)
-

### 연결 문서
-
