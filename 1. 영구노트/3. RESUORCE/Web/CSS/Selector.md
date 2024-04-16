### 주제 : selector

### 날짜 : 2024-04-16 13:56
----
### 메모
> Selector
> 	- CSS를 적용할 요소를 지칭한다.

> Tag Selector
```html
<style>
    p{
        color:red;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

> Id Selector
> 	- Id 값 앞에 '#'을 붙여서 선택
> 	- 우선순위 때문에 쓰지 않는 것이 좋음
```html
<style>
    #hello{
        color:blue;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

> Class Selector
> 	- Class 앞에 '.'을 붙여서 선택
> 	- 가장 많이 쓰이는 Selector
```html
<style>
    .hello{
        color:green;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

>CSS 속성 Selector
>	- 대괄호 안에 속성명 = "값" 형태로 사용
>	- 대괄호 안에 속성명 형태로도 사용 가능
```html
<style>
    [type="button"]{
        color: green;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

> 부모자식 관계 Selector
> 	- html 문서는 부모 자식 관계가 있다.
> 	- header와 h1, h2는 부모-자식 관계
> 	- h1 h2는 형제 관계
```html
<header>
    <h1>조 루소</h1>
    <h2>안소니 루소</h2>
</header>
```

> 후손 Selector
> 	- 부모와 후손을 선택 시 공백 사용
> 	- 여러 개의 Selector를 적용할 때 콤마로 구분
```html
<style>
    header h1{
        color:red;
    }
    header h1, header h2{
        color:red;
    }
</style>

<header>
    <h1>조 루소</h1>
    <h2>안소니 루소</h2>
    <ul>
        <li>
            <h1>안소니 루소 1세</h1>
        </li>
        <li>
            <h1>안소니 루소 2세</h1>
        </li>
        <li>
            <h1>안소니 루소 3세</h1>
        </li>
        <li>
            <h1>안소니 루소 4세</h1>
        </li>
    </ul>
</header>
```

> 자식 Selector
> 	- 부모와 자식 선택 시 꺽쇠(>) 사용
```html
<style>
    header > h1{
        color:red;
    }
    header > h1, header > h2{
        color:red;
    }
</style>

<header>
    <h1>조 루소</h1>
    <h2>안소니 루소</h2>
    <ul>
        <li>
            <h1>안소니 루소 1세</h1>
        </li>
        <li>
            <h1>안소니 루소 2세</h1>
        </li>
        <li>
            <h1>안소니 루소 3세</h1>
        </li>
        <li>
            <h1>안소니 루소 4세</h1>
        </li>
    </ul>
</header>
```

> 바로 뒤 형제 Selector
> 	- 바로 뒤 형제 선택 시 사용
```html
<style>
    h1 + p{
        color:red;
    }
</style>

<h1>h1</h1>
<p>첫 번째 자식 p</p>
<h2>h2</h2>
<p>두 번째 자식 p</p>
```

> 전체 Selector
> 	- 모든 엘리먼트 선택 시 '\*'사용
> 	- 성능에 좋지 않아 남발하지 않는 것이 좋다.
```html
<style>
    header * {
        color:red;
    }
</style>

or

<style>
    header p {
        color:red;
    }
</style>

or

<style>
    * {
        color:red;
    }
</style>

<header>
    <p>Avengers</p>
    <div>
        <p>End game</p>
    </div>
</header>
```

> 유사 class Selector
> 	-Element가 특별한 상태일 때를 선택
> 	- 마우스가 올라가 있거나, 선택되어 있거나 등
```html
<style>
    header  > p:hover  {
        color:red;
    }
</style>


<header>
    <p>Avengers</p>
    <div>
        <p>End game</p>
    </div>
</header>
```

> 유사 Element Selector
> 	- Element 내용의 앞과 뒤에 내용을 삽입
> 	- 가상요소이므로 블록 지정이 안됨
> 	- 존재하는 Element가 없는 가상의 요소를 선택
> 	- 유사 class는 상태를 선택하고, 유사 Element는 선택적인 부분을 선택
> 	- 주로 문자열을 지정할 수 있는 content 속성과 함계 사용
> 	- 콜론 두 개(\:\:)와 함계 사용
```html
<style>
    div::before{
        content: "마블's";
        color:red;
        margin-right:10px;
    }
    div::after{
        content:"시리즈";
        color:blue;
        margin-left:10px;
    }
</style>

<div>캡틴 아메리카</div>
```

> CSS 우선 순위
> 	- 하나의 Element에 여러 가지 Selector로 선택이 가능
> 	- 각 Selector로 지정한 스타일 중 우선순위에 따라 적용
> 	- Class Selector > Tag Selector
> 	- Selector 우선순위 동등 시 나중에 선언된 스타일 적용

### 출처(참고 문헌)
-

### 연결 문서
- [[Box Model]]
