[maven project create](http://jaesu.tistory.com/entry/Maven-web-project-%EB%A7%8C%EB%93%A4%EA%B8%B0)

1. eclipse project - setting
    > Project encoding Update : UTF-8
    > Deployment Assembly : "MavenDependencies" check
    > Java Build Path : jdk version
2. servlet version : update
    > "web.xml" update
    >> [servlet version - web.xml](http://antop.tistory.com/145)
    > Project Facets : jdk version, servlet version
      >> The servlet version must modify the following eclipse configuration file:
      >>> /setting/org.eclipse.wst.common.project.facet.core.xml
      >> The window can be moved to the project folder directly by clicking on the resource.
      >> maven update
3. "pom.xml" Update
    > name Updadte : 수정안하면 project 를 톰캣에 추가할때 contex가 이상하게 들어간다.
    > properties Add : jdk버전, project_name, build encoding, report encoding
    > build plugin Add : 프로젝트에서 오른쪽키 > Maven > Add Plugn
4. "tomcat" run : http://localhost:9090/context_name
    > port Update
    > context name Update

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
1. "name" Update
<name>deityWebapp</name>

2. "properties" Update
    <properties>
        <jdk.version>1.8</jdk.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>        
        <project.name>modelMap</project.name>
    </properties>

3. "build" Update
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

