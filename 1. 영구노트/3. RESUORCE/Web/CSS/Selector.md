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
```htm
```

### 출처(참고 문헌)
-

### 연결 문서
-
