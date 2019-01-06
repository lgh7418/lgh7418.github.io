---
title: "190101 Servlet"
layout: default
categories: JSP
---  

> 인프런 / 실전 JSP (ver.2018) – 신입 프로그래머를 위한 강좌

# Servlet Life-Cycle

1. @PostConstruct : 생성 준비
1. init() : 서블릿 생성
1. service : 실행
1. destroy() : 종료
1. @PreDestrou : 종료 이후 처리

실행 역할은 service 메소드는 잘 안쓰고 doGet()이나 doPost() 메소드를 씀


```java
@WebServlet("/TS")
public class TestServlet extends HttpServlet {
	
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.getWriter().append("Served at: ").append(request.getContextPath());
		System.out.println("--- doGet() ---");	 // 메소드 실행순서 확인 용도
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}
	
	@PostConstruct
	public void funPc() {
		System.out.println("--- @PostConstruct ---");
	}
	
	@Override
	public void init() throws ServletException {
		System.out.println("--- init() ---");
	}
	
	@Override
	public void destroy() {
		System.out.println("--- destroy() ---");
	}
	
	@PreDestroy
	public void funPd() {
		System.out.println("--- @PreDestroy ---");
	}
	
}

```

이 코드를 run on server로 실행시키면

--- @PostConstruct ---  
--- init() ---  
--- doGet() ---  

콘솔창에 이렇게 뜨고(실행 순서), 서버를 중지시키면

--- destroy() ---  
--- @PreDestroy ---  

이렇게 뜸



# form 데이터 처리

브라우저를 통해서 http request가 전송되는 것은

form 태그에서 사용자가 전송하면 request 객체로 받는 것!

|form 태그 | request 객체| |
|:---:|:---:|-----|
| method="get" | doGet() | 사용자 정보가 URL에 노출 |
| method="post" | doPost() | 사용자 정보 노출 X (맵핑 정보만 노출) |

### 서블릿 파일로 Request
* **html 파일**

	`<form action="mSignUp" method="post">`

	action 속성값: 블릿의 맵핑 정보 표시 -> submit을 누르면 여기로 찾아감

* **java(servlet 파일)**

	`@WebServlet("/mSignUp")`

	doPost() 메소드는 호출되면 doGet() 메소드로 정보를 보내줌( 그냥 메소드를 한 곳에 모으려고...)

### HttpServletRequest 객체로 값 받아오기

* **html form 태그**

	`<input type="text" name="m_name">`

* **servlet doGet 메소드**

	`String m_name = request.getParameter("m_name");`

### 다중선택 체크박스 값 받아오기

* **html form 태그**

    ```html
    <input type="checkbox" name="m_hobby" value="sport">Sport
    <input type="checkbox" name="m_hobby" value="cooking">cooking
    <input type="checkbox" name="m_hobby" value="reading">reading
    ```

* **servlet doGet 메소드**

    ```java
    String[] m_hobbys = request.getParameterValues("m_hobby");
    System.out.println(Arrays.toString(m_hobbys));
    ```

* **콘솔에 출력**

	[sport, cooking, reading]

