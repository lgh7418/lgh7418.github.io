servlet 맵핑
full path는 패키지 네임이랑 싹 다 들어있음
context path/서블릿 경로/패키지 경로.fullname
보안 취약, 복잡한 URL

mapping path
context path/mapping path
간결함 서블릿 이하를 간결하게

맵핑 방법
1. web.xml 파일을 이용한 방법
   ```xml
   <servlet>
      <servlet-name>servletEx</servlet-name>
      <servlet-class>com.servlet.ServletEx</servlet-class>
    </servlet>
    <servlet-mapping>
      <servlet-name>servletEx</servlet-name>
      <url-pattern>/SE</url-pattern>
    </servlet-mapping>
    ```

2. java annotation
@WebServlet("/SE1")
서블릿 파일 위에 속성값으로 넣어줌
1과2를 같이 사용하면 url 2개 모두 접속 가능(/SE, /SE1)

# Servlet request, response

요청과 응답을 객체로 만들어서 처리
Servlet 클래스를 만들려면
HttpServlet(abstract class)을 상속받아야 함
doGet과 doPost 메소드가 자동 생성
이 메소드들의 파라미터는 HttpServletRequest request, HttpServletResponse response
이는 요청과 응답에 대한 객체들임
사용자가 어떤 것을 요청했는지 파악할 때 => request 객체의 메소드를 이용
서버의 응답은 response 객체(응답에 대한 정보를 가지고 있는 객체)의 메소드 이용
