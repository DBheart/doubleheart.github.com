[maven project create](http://jaesu.tistory.com/entry/Maven-web-project-%EB%A7%8C%EB%93%A4%EA%B8%B0)

1. eclipse project 설정
    - 프로젝트 인코딩 변경 : UTF-8
    - Deployment Assembly : MavenDependencies를 확인
    - Java Build Path : 자바버전
2. 서블릿 버전 수정
    - "web.xml" update
      - [블릿 버전별 web.xml](http://antop.tistory.com/145)
    - Project Facets : 자바버전, 서블릿 버전
      - 서블릿 버전은 이크립스 설정파일을 수정해야한다.
      - 윈도우는 바로 이동할수 있는 Resource에서 클릭하여서 프로젝트 폴더로 이동할수 있다.
3. 톰캣 띄워서 되는지 보기 : http://localhost:9090/컨택스명



---

서블릿 3.1의 web.xml 설정
Servlet 3.1
---------------------------------------------------------------------------------------------------------------
|<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" |
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" |
	version="3.1"> |
</web-app> |
---------------------------------------------------------------------------------------------------------------
      
