<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>	

spring web mvc

1. pom.xml 수정 : 디펜던시 추가
    - 이곳에 모두 포함되어 있다. 코어등은 안넣어도 된다. 다른 버전 하려면 안해도되고
    - 4.x버전을 받자. 나머지는 스프링 부트버전으로 돌리자.

2. web.xml 수정 : 스프링 서블릿 등록
    - 서블릿 이름은 짧게 쓰도록 하자.
    - 스프링 설정파일 위치 설정 : 안되었을시에는 WEB-INF디렉토리에서 찾는다.
    - url 패턴 설정 : 우선은 "/"로 잡는다.
    - 이크립스에서는 템플릿으로 잡혀있다. 그래서 설정위치와 url패턴만 설정하면 되도록 템플릿이 만들어져 있다.
    
3. 스프링설정 파일 추가 : context.xml
    - resource에 넣는게 깔끔하겠지? 여기서는 /spring/context.xml로 넣는다.
    - 설정파일 [참고](https://crunchify.com/simplest-spring-mvc-hello-world-example-tutorial-spring-model-view-controller-tips/) 
    
4. jsp 파일 추가
    - 설정파일에 있는 jsp기본 위치에 폴더를 만들고 한다. WEB-INF/view로 폴더를 만들자.
    - hello.jsp 파일 추가, encoding 수정

5. Controller 추가
    - 스프링 설정파일에 component-scan의 디폴트 패키지에 클래스를 추가한다.
    - "kr.pe.deity" 패키지 추가
    - HelloController 추가
    - Controller 어노테이션 추가, RequestMapping 추가
    -- hello메서드에 리턴을 "hello"로 하도록 한다.
    
6. 서버 실행 : http://localhost:9090/hello    
    
---

```
web.xml
	<servlet>
		<servlet-name>mvcServlet</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>classpath:/spring/context.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>

	<!-- Map all requests to the DispatcherServlet for handling -->
	<servlet-mapping>
		<servlet-name>mvcServlet</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
```
    
```
스프링 설정파일 기본, context.xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans     
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/mvc 
        http://www.springframework.org/schema/mvc/spring-mvc.xsd
        http://www.springframework.org/schema/context 
        http://www.springframework.org/schema/context/spring-context.xsd">
 
    <mvc:annotation-driven />
    <context:component-scan base-package="kr.pe.deity" />
    <mvc:default-servlet-handler />
 
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/view/" />
        <property name="suffix" value=".jsp" />
    </bean>
</beans>
```
    
