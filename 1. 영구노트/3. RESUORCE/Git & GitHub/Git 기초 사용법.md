### 주제 : Git 기초 사용법

### 날짜 : 2024-04-15 19:36
----
### 메모
> 파일 수정과 상태 변경
> 	- 워킹 디렉토리의 파일은 Tracked와 Untracked로 나뉜다.
> 	- Traked : 이미 스냅샷에 포함
> 	![[Pasted image 20240415193833.png]]
> 	- 파일 수정 : open in 기능을 이용하여 저장소가 위치한 곳으로 쉽게 이동 가능하다.

> 브랜치
> 	- 가상의 작업 공간
> 	- 중요한 문제가 생겨서 해결하는 hotfix를 만들어야 한다면 새로운 이슈를 처리하기 전의 운영 브랜치로 이동하여 hotfix 테스트를 마치고 운영 브랜치로 merge한다.

> Git이 데이터를 저장하는 방법
> 	- 커밋을 하면 Git은 커밋 개체를 생성한다.
> 	![[Pasted image 20240415200239.png]]
> 	- 데이터의 스냅샷에 대한 포인터
> 	- 메타 데이터 : 저자, 커밋 메세지 등
> 	- 이전 커밋에 대한 포인터
> 	- 다시 파일을 수정하고 커밋하면 이전 커밋이 무엇인지도 저장
> 	![[Pasted image 20240415200415.png]]
> 	- Git의 브랜치는 커밋을 가리키는 포인터이다.
> 	![[Pasted image 20240415200457.png]]

> Git-flow
> 	- 브랜치 관리 모델 . 중하나로 Vincent Driessen이 주장
> 
> main branch
> 	- 밑의  두 브랜치는 항상 존재하는 메인 브랜치 이다.
> 	- master(main) : 배포된 소스가 있다.
> 	- develop : 다음 배포를 위한 소스가 있다. 개발이 완료되면 일련의 과정을 통해 master(main)으로 merge한다.
> 	![[Pasted image 20240415203312.png]]
> 
> 서포팅 브랜치
> 	- master와 develop 외에 팀 멤버들이 병렬로 일할 수 있도록 도와주는 브랜치가 있다.
> 	- 메인 브랜치와는 다르게 필요할 때 생성하였다가 삭제한다.
> 		1. feature branch
> 		2. release branch
> 		3. hotfix branch
> 
> feature branch
> 	- branch 생성 : develop으로 부터
> 	- merge : develop으로
> 	- prefix: feature/
> 	- feature brach는 특정 기능 하나에 대하여 develop으로부터 생성하여 개발하며 개발이 완료되면 다시 develop으로 merge
> 	- 이때 각 기능 별로 개발한 커밋을 구별할 수 있도록 fast-forward를 사용하지 않는다.
> 	![[Pasted image 20240415203703.png]]
> 
> release branch
> 	- branch 생성 : develop으로 부터
> 	- merge : develop과 mater로
> 	- prefix : release/
> 	- release branch는 배포를 위한 준비를 할 수 있는 브랜치이다.
> 	- release branch에서는 각종 메타 데이터를 변경하거나 작은 버그를 수정한다.
> 	- 배포 준비가 완료되면 release branch를 master와 develop에 각각 merge한다.
> 	- master에는 버전 태그를 붙인다.
> 	- release branch를 따로 가져가기 때문에 develop branch에서는 바로 다음 배포를 위한 기능을 시작할 수 있다.
> 	- release branch를 다시 develop으로 merge하기 때문에 release 브랜치의 변경 사항이 develop에 반영된다.
> 	![[Pasted image 20240415204333.png]]
> 
> hotfix branch
> 	- branch 생성 : master로 부터
> 	- merge : develop과 master로
> 	- prefix : hotfix/
> 	- hotfix branch는 배포된 버전에 긴급한 변경 사항이 있을 때 활용한다.
> 	- hotfix branch는 master로부터 생성한다.
> 	- 긴급한 이슈가 해결되면 다시 master와 develop에 merge한다.
> 	- hotfix branch 역시 따로 가져가기 때문에 develop branch에서는 다음 배포를 위한 기능 개발을 계속 진행할 . 수있다.
> 	- hotfix branch를 develop으로 merge하기 때문에 hotfix branch의 변경 사항이 develop에 반영된다.
> 	![[Pasted image 20240415204631.png]]
> 
> 요약
> 	![[Pasted image 20240415204703.png]]

### 출처(참고 문헌)
-

### 연결 문서
-
