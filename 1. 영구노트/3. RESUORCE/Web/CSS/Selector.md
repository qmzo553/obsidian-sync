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

>CSS 속성 셀렉터
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

### 출처(참고 문헌)
-

### 연결 문서
-
