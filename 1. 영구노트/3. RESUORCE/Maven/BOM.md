### 주제 : BOM이란?

### 날짜 : 2024-04-24 08:03
----
### 메모
> POM
> 	- maven에서 종속성을 가지오고 프로젝트를 빌드하는 데 사용하는 정보 및 설정을 포함하는 XML 파일
> 
> BOM(Bill Of Materials, 자재 명세서)
> 	- 프로젝트 종속성의 버전을 제어하고, 해당 버전을 정의하며, 업데이트하는 중앙 위치를 제공하는 데 사용되는 특별한 종류의 POM
> 	- 의존해야 하는 버전에 대한 걱정없이, 모듈에 의존성을 추가할 수 있는 유연성을 제공한다.
> 
> Dependency Managemnet(의존성 관리)
> 	- 의존성 정보를 중앙 집중화 하는 매커니즘
> 	- 공통 부모를 상성하는 프로젝트 세트가 있는 경우 모든 의존성 정보를 BOM이라는 공유 POM 파일에 넣을 수 있다.
> 
> 일반 POM 파일
```xml
<project ...> 
	<modelVersion>4.0.0</modelVersion> 
	<groupId>baeldung</groupId> 
	<artifactId>Baeldung-BOM</artifactId> 
	<version>0.0.1-SNAPSHOT</version> 
	<packaging>pom</packaging> 
	<name>BaelDung-BOM</name> 
	<description>parent pom</description> 
	<dependencyManagement> 
		<dependencies> 
			<dependency> 
				<groupId>test</groupId> 
				<artifactId>a</artifactId> 
				<version>1.2</version> 
			</dependency> 
			<dependency>
				<groupId>test</groupId> 
				<artifactId>b</artifactId> 
				<version>1.0</version> 
				<scope>compile</scope> 
			</dependency> <dependency> 
				<groupId>test</groupId> 
				<artifactId>c</artifactId> 
				<version>1.0</version> 
				<scope>compile</scope> 
			</dependency> 
		</dependencies> 
	</dependencyManagement> 
</project>
```
> BOM
```xml
<dependencyManagement>
	<dependencies> 
		<dependency> 
			<groupId>org.springframework</groupId> 
			<artifactId>spring-framework-bom</artifactId> 
			<version>4.3.8.RELEASE</version> 
			<type>pom</type> 
			<scope>import</scope> 
		</dependency> 
	</dependencies> 
</dependencyManagement>
	<dependencies> 
		<dependency> 
			<groupId>org.springframework</groupId> 
			<artifactId>spring-context</artifactId> 
		</dependency> 
		<dependency> 
			<groupId>org.springframework</groupId> 
			<artifactId>spring-web</artifactId> 
		</dependency> 
	<dependencies>
```
> Parent POM
> 	- 공통의 프로젝트 설정을 공유하기 위해 사용
> 	- 프로젝트의 구조, 플러그인, 프로파일, 기본적인 종속성 관리 등을 정의 할 수 있게 해준다.
> 
> BOM 과 Parent POM 의 차이
> 	1. 상속 vs 관리
> 		- Child POM은 Parent POM의 설정을 상속한다. 이 상속에는 플러그인 구성, 빌드 설정, 프로퍼티 등이 포함될 수 있다.
> 		- BOM은 종속성 버전을 중앙에서 관리하는 데 초점을 맞춘다.
> 	2. 유연성
> 		- Parent POM을 상속받은 모든 설정과 종속성은 Parent POM을 변경함으로써 전체적으로 영항을 받는다.
> 		- BOM은 필요한 종속성 관리에만 사용되며, 필요에 따라 프로젝트에서 선택적으로 사용할 수 있다.
> 	3. 응용 범위
> 		- Parent POM은 특정 프로젝트 그룹 내에서 공통 설정을 공유할 때 사용된다.
> 		- BOM은 조직 전체의 여러 프로적트에서 특정 라이브러리 또는 플러그인의 버전을 일관되게 유지하려 할 때 사용된다.
> 	- 결론 : BOM은 종속성 버전 관리에 특화되어 있는 반면, Parent 

### 출처(참고 문헌)
- [[https://scshim.tistory.com/419]]

### 연결 문서
-
