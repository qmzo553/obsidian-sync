### 주제 : HttpServletRequest,HttpServletResponse

### 날짜 : 2024-04-22 15:08
----
### 메모
> HttpServletRequest
```java
public interface HttpServletRequest extends ServletRequest {
    String getMethod();
    String getPathInfo();
    String getServletPath();
    String getContextPath();
    String getRequestURI();
    StringBuffer getRequestURL();
    String getHeader(String var1);
    Cookie[] getCookies();
    HttpSession getSession(boolean var1);
    HttpSession getSession();
    //...
}
```

### 출처(참고 문헌)
-

### 연결 문서
-
