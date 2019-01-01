HTTP
하이퍼텍스트 웹문서를 전달하기 위해 사용되는 규약

WWW(World Wide Web)
‘하이퍼텍스트’ 기능 혹은 ‘HTTP(HyperText Transfer Protocol)’ 프로토콜을 사용하여 인터넷상에
분산되어 존재하는 온갖 종류의 정보를 통일된 방법으로 찾아볼 수 있게 하는 서비스 혹은
소프트웨어

ip
인터넷 상에서 내 컴퓨터를 식별하기위한 주소(숫자로 이루어짐)
210.89.164.90
// 웹사이트의 ip주소 확인하는 법: cmd에서 `tracert naver.com`

DNS
도메인 이름(naver.com)을 ip주소(210.89.164.90)로 바꿔줌

http://www.google.com:80/index.html|
|||
|---|---|
|http | protocol |
|www | 인터넷 서비스 구분|
|google.com | 도메인|
|:80 |port (자동 설정)|
|index.html|경로 (자동 설정)|

Web Server가 처리하는 데이터
정적 데이터
요청한 정보를 html 파일 그대로 response
동적 데이터
사용자의 request에 따라 데이터의 새로운 가공이 필요함
container로 보내서 처리


javac.exe : 컴파일러
java.exe : jvm 구동 명령 (실행 역할)
환경변수(path) 설정 : 다른 디렉토리에서도 실행할 수 있도록 함

Apache Tomcat : 웹 컨테이너 (웹 서버)

xxx.jsp를 통해 request
웹 컨테이너(tomcat)으로 이동
1. xxx_jsp.java 파일로 변환
2. xxx_jsp.class 파일로 변환 (javac.exe가 컴파일)
3. xxx_jsp.obj로 변환 (링크 작업)
---
사용자에게 response는 html 형식으로 함

서버를 실행시킨 후
jsp파일을 브라우저를 통해 실행하면 응답된 페이지가 뜸
페이지 소스보기를 하면 html 소스만 뜨고 jsp는 뜨지 않음

C:\apache-tomcat-9.0.14\work\Catalina\localhost\testProject\org\apache\jsp
여기 가보면 xxx_jsp.java 파일, xxx_jsp.class 파일이 생성된 걸 확인할 수 있음

---
# servlet

jsp 파일이 아닌 java파일을 가지고 web 서버에 연결하는 것

C:\Java_workspace\test_servlet\build\classes\test_servlet
여기 가보면 xxx.class 파일이 생성된 걸 확인할 수 있음
