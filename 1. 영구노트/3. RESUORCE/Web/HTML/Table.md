### 주제 : table

### 날짜 : 2024-04-16 10:17
----
### 메모
> 웹 문서에서 자료를 정리할 때 가장 많이 사용하는 tag
> 	- table tag로 테이블을 시작
> 	- tr tag로 테이블을 시작
> 	- td tag로 행을 만듦
> 	- th tag는 셀의 문자를 가운데 굵게 표시(제목에 사용)
> 	![[Pasted image 20240416102036.png]]
```html
<table border="1">
    <tr>
        <td>아바타</td> <td>2009</td> <td>제임스 카메론</td>
    </tr>
    <tr>
        <td>어벤저스: 엔드게임</td> <td>2019</td>
        <td>루소 형제</td>
    </tr>
</table>
```

> 테이블의 구조 지정
> 	- caption tag : 테이블의 제목 지정
> 	- thead tag : 테이블 헤더 지정
> 	- tbody tag : 테이블의 내용
> 	- tfoot tag : 테이블의 푸터 지정
> 	![[Pasted image 20240416102045.png]]
```html
<table border="1">
    <thread>
        <tr>
            <th>제목</th>
            <th>연도</th>
            <th>감독</th>
        </tr>
    </thead>

    <tr>
        <td>아바타</td>
        <td>2009</td>
        <td>제임스 카메론</td>
    </tr>
    <tr>
        <td>어벤저스: 엔드게임</td>
        <td>2019</td>
        <td>루소 형제</td>
    </tr>
</table>
```
### 출처(참고 문헌)
-

### 연결 문서
-
