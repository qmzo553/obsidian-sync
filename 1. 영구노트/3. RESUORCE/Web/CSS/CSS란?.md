### 주제 : Cascading Style Sheet

### 날짜 : 2024-04-16 13:48
----
### 메모
> Cascading Style Sheet
> 	- Cascading : 폭포처럼 위에서 아래로 흐르는..., 상속 또는 종속하는 ...
> 	- 문서의 표현을 기술하는 스타일 시트 언어
> 	![[Pasted image 20240416134942.png]]

> CSS 적용
>  
>  Inline
> 	- 각 태그마다 스타일을 모두 적어야 하므로 관리가 쉽지 않다.
> 	- 우선 순위가 가장 높기 때문에 특별한 경우가 아니면 쓰지 말아야 한다.
> 	- 메일 본문 스타일을 만들 때 주로 사용한다.
```html
<div style="display: none;"></div>
```
> Embeded
> 	- 보통 head안에 Style을 감싸서 넣는다.
> 	- CSS가 간단한 페이지 일 경우 사용
> 	- 사용자에게 초기 로딩시 보여주는 화면을 구성할 때 사용
```html
<head>
    <style>
    	div {display: none;}
    </style>
</head>
```
> External
> 	- 별도의 CSS 파일로 분리
> 	- 관심사 분리와 재사용이 가능
> 	- 가장 많이 사용하는 방법이다.
```html
<link rel="stylesheet" href=""../src/css/index.css>
```

> CSS 상속
> 	![[Pasted image 20240416135504.png]]
> 	상속이 되는 속성이 있고 안되는 속성이 있다.
### 출처(참고 문헌)
-

### 연결 문서
-
