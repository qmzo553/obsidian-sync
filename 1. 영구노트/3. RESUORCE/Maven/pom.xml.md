### 주제 : pom.xml에 대해서

### 날짜 : 2024-04-29 08:16
----
### 메모
> pom.xml이란?
> 	- Maven의 Project Object Model을 정의한다. 이는 프로젝트 관리 및 구성의 기반이 된다.
> 	- `<project>` 태그로 시작하며, XML 스키마 위치를 포함한다.
> 
> project tag 정보
> 	- groupId : 프로젝트를 생성하는 조직의 그룹 ID, 일반적으로 도메인 이름을 역순으로 사용
> 	- artifactId : 프로젝트의 아티팩트(빌드 결과물) ID
> 	- version : 프로젝트의 현재 버전
> 	- packaging : 프로젝트의 패키징 유형을 지정한다. (jar, war, ear 등 기본값은 jar)
> 	- name : 프로젝트의 표시 이름을 제공
> 	- scope : 의존성의 범위를 정의한다.
> 
> build tag
> 	- apache maven plugin들을 사용할 수 있다.
> 	- build 과정(compile + link + deploy을 컨트롤 한다.
> 	- `<resource>` 와 `<diretory>` tag를 함꼐 작성하여 배포할 때 해당 디렉토리의 파일들이 포함(jar로 패키지 할때 함께 배포)

### 출처(참고 문헌)
- [[https://wookim789.tistory.com/26]]

### 연결 문서
-
