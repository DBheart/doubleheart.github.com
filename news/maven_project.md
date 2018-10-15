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
      - /setting/org.eclipse.wst.common.project.facet.core.xml
      - 윈도우는 바로 이동할수 있는 Resource에서 클릭하여서 프로젝트 폴더로 이동할수 있다.
      - 다 한뒤에 maven update
3. pom.xml 수정
    - name명 수정 : 수정안하면 project 를 톰캣에 추가할때 contex가 이상하게 들어간다.
    - properties 추가 : jdk버전, project_name, build encoding, report encoding
    - 빌드 플러그인 추가 : 프로젝트에서 오른쪽키 > Maven > Add Plugn
4. 톰캣 띄워서 되는지 보기 : http://localhost:9090/컨택스명

---

Servlet 3.1 wbe.xml
```
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" 
	version="3.1"> 
</web-app>
```

pom.xml  
```
1. name 수정
<name>deityWebapp</name>

2. properties 수정
    <properties>
        <jdk.version>1.8</jdk.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>        
        <project.name>modelMap</project.name>
    </properties>

3. build 수정
    <build>
        <finalName>${project.name}</finalName>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.1</version>
                    <configuration>
                    <source>${jdk.version}</source>
                    <target>${jdk.version}</target>
                    </configuration>
                </plugin>
            </plugins>    
    </build>    
```

