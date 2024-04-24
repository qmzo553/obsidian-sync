### 주제 : Reflection 이란?

### 날짜 : 2024-04-25 08:37
----
### 메모
> Reflection
>	- 실행 중인 JAVA 프로그램이 자체적으로 검사하거나 프로그램 내부 속성을 조작할 수 있다.
>	- 자체적으로 생성된 객체의 class type을 알지 못하더라도 해당 class의 메소드, 타입, 변수들에 접근할 수 있도록 해주는 API
>	- 다른 클래스에 대한 상세한 사항을 알아낼 수 있게 하는 것이 reflection의 기능이다.
>	- java 프로그램 내에서 class를 읽고, 변수, 메서드, 생성자를 알아내어 작업을 할 수 있다.
```java
public static void main(String[] args) {
    Class c = ArrayList.class;
    Method m[] = c.getDeclaredMethods();
    for(int i=0; i<m.length; i++){
        System.out.println(m[i].toString());
    }
}
```
> Reflection Method
> 	- Class.forName(className) : 물리적인 클래스 파일명을 인자로 넘겨주면 이에 해당하는 클래스를 반환한다.
> 	- Clazz.getCons

### 출처(참고 문헌)
-

### 연결 문서
-
