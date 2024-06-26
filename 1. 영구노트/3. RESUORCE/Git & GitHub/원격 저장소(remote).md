### 주제 : 원격 저장소

### 날짜 : 2024-04-16 08:01
----
### 메모
> 원격 저장소
> 	- Git은 로컬 저장소만 사용할 수도 있지만 원격 저장소를 추가하여 사용할 수 있다.
> 	- 우리는 GtiHub의 저장소를 복제했을 때 git은 자동으로 GitHub에 있는 원격 저장소를 origin이라는 이름으로 추가한다.

>로컬 브랜치와 원격 브랜치
>	- local branch인 main과 원격 브랜치인 origin/main은 서로 별개의 브랜치이다.
>	- Git이 origin/main을 체크아웃하여 로컬 브랜치인 main을 생성하였다.
>	![[Pasted image 20240416080507.png]]
>	- A 사람과 B라는 사람의 main 또한 별개의 브랜치이다.
>	![[Pasted image 20240416080553.png]]

> Fetch
> 	- 원격 저장소의 변경 사항을 내려 받는 것을 fetch라고 한다.
> 	- Fetch까지만 하면 변경 사항을 받았을 뿐 아직 로컬 브랜치에는 merge되지 않은 상태이다.
> 	- local branch에 원격 저장소의 변경 사항을 반영하고 싶다면 수동으로 원격 브랜치를 로컬 브랜치로 merge해야 한다.
> 	![[Pasted image 20240416080847.png]]

> Pull
> 	- fetch + merge를 같이 해주는 명령어이다.

> Push
> 	- 로컬 저장소의 변경 사항을 원격 저장소로 올리는 것을 push라고 한다.
> 	![[Pasted image 20240416080942.png]]

> Fork
> 	- 다른 사람의 원격 저장소를 copy하여 내 로컬 저장소에 저장하는 기능이다.
> 	- pull request를 통해 원격 저장소로 다른 사람의 변경 사항을 반영할 수 있다.
> 	- 원격 저장소의 주인이 다른 사람의 pull request를 허용하거나 거부할 수 있다.
> 	- 원격 저장소의 변경 사항을 다른 사람이 반영하기 위해서는 원격 저장소를 remote 해야한다. 이때 이름은 보통 upstream

### 출처(참고 문헌)
-

### 연결 문서
-
