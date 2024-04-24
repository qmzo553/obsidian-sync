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

### 출처(참고 문헌)
- [[https://scshim.tistory.com/419]]

### 연결 문서
-
