톰캣에 있는것 로그를 모두 버리고, log4j로 되도록 한다.

# [log4j와 logback정리](http://goddaehee.tistory.com/45)

요즘은 slf4j는 기본이고 그것을 사용하는 api라이브러리를 정해야한다.
api라이브러리는 크게 3개로 나누면 될것같다.
    > log4j
    > logback
    > log4j2 

여기서는 log4j를 써보도록 하겠다.(log4j2를 쓴것같은데 아닌가 보다 ㅎㅎㅎlog4j.xml을 참조하네?

# 설치사항
## maven에서 logback을 설치하면  slf4j가 설치된다.
### logback-classic
### https://github.com/sonegy/how-to-use-logback
## log4j와 log4j2는 slf4j 라이브러리를 설치하고 log4j api와 log4j2 api 중에서 맞는것을 설치해야한다.
## [설치 참조](https://examples.javacodegeeks.com/enterprise-java/logback/logback-vs-log4j-example/)

설정파일 위치 : 사람들은 설명을 할때 설정파일 위치를 참~ 안가르쳐 준다. 
> 예제를 보니 classpath의 루트부분으로 보인다. 이크립스에서는 resource바로 밑에 넣어두면 될것같다.
> 설정파일 위치를 바꾸려면 web.xml에서 수정하는 것을 본것 같은데... 확실하지는 않다. 
> 파일명도 일정해야하는것으로 보인다. 파일은 두가지 타입으로 할수 있다. properites와 XML.. 그중에 xml이 더 명확하게 보여서 괜찮은것 같다.

예제
> log4j : log4j.properties, log4j.xml
> log4j2: log4j2.properties, log4j2.xml
> logback:logback.xml ( 프로퍼티파일도 있을란가? 부트스트랩에서는 로그 파일없어도 잘돌아가는 것같다)

1. log4j.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">
<log4j:configuration debug="true">
	<appender name="DAILYLOG"
		class="org.apache.log4j.DailyRollingFileAppender">
		<param name="File" value="logs/log4j1/demo.log" />
		<param name="Append" value="true" />
		<!-- Rollover at midnight each day -->
		<param name="DatePattern" value="'.'yyyy-MM-dd" />
		<layout class="org.apache.log4j.EnhancedPatternLayout">
			<param name="ConversionPattern"
				value="%d{yyyy-MM-dd'T'HH:mm:ss.SSSZZZ} llevel=%-5p, lthread_id='%t',lclass=%C{2.}.%L,lmethod=%M %m%n" />
		</layout>
	</appender>
	<appender name="CONSOLE"
		class="org.apache.log4j.ConsoleAppender">
		<param name="Target" value="System.out" />
		<layout class="org.apache.log4j.EnhancedPatternLayout">
			<param name="ConversionPattern"
				value="%d{yyyy-MM-dd'T'HH:mm:ss.SSSZZZ} llevel=%-5p, lthread_id='%t',lclass=%C{2.}.%L,lmethod=%M %m%n" />
		</layout>
	</appender>

	<logger name="kr.pe.deity">
		<level value="DEBUG" />
	</logger>

	<root>
		<priority value="DEBUG" />
		<appender-ref ref="DAILYLOG" />
		<appender-ref ref="CONSOLE" />
	</root>
</log4j:configuration>
```
2. logback.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <include resource="org/springframework/boot/logging/logback/defaults.xml" />
    <include resource="org/springframework/boot/logging/logback/console-appender.xml" />    

    <!-- 변수 지정 -->
    <property name="LOG_DIR" value="../logs" />
    <property name="LOG_PATH_NAME" value="${LOG_DIR}/data.log" />

    <!-- FILE Appender -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>${LOG_PATH_NAME}</file>
        <!-- 일자별로 로그파일 적용하기 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${LOG_PATH_NAME}.%d{yyyyMMdd}</fileNamePattern>
            <maxHistory>60</maxHistory> <!-- 일자별 백업파일의 보관기간 -->
        </rollingPolicy>
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss} [%-5p] [%F]%M\(%L\) : %m%n</pattern>
        </encoder>
    </appender>

    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
      <layout class="ch.qos.logback.classic.PatternLayout">
        <pattern>%d{yyyy-MM-dd HH:mm:ss} [%-5p] [%F]%M\(%L\) : %m%n</pattern>
      </layout>
    </appender>

    <root level="DEBUG">
        <appender-ref ref="FILE" />
        <appender-ref ref="STDOUT" />
    </root>
</configuration>
```

logback에 대한사항
0. 설치사항
> logback-classic : STS에서 add로는 안보인다. 메이븐 레파지토리 웹에서 찾아서 넣자.
>> scope가 test로 되어있으므로 수정하자.
> logback-access : STS에서 add로 찾아서 설치
> log4j-over-slf4j : STS에서 add로 찾아서 설치

1. 로그연관 api
> log4jdbc-log4j2 : DB의 쿼리를 정렬해서 보여준다. 
>> 내가 알기로는 DB쿼리를 보여주고 결과까지 보여주는 api가 있었던거 같은데...
> log4j-over-slf4j : log4j로그를 slf4j로 전환해준다. 
>> 스프링로그가 log4j로 전환되어서 나오는데 이 라이브러리를 안쓰면 안나오게 된다.

2. 로그백 클래스 분석
> logback-core : 로그백 핵심 코어
> logback-classic : 핵심코어 컴포넌트
> logback-access : 웹어플리케이션에서 http 디버깅이 가능하게 한다. 어떻게?

확인사항(확인완료)
> 톰캣로그와 중복으로 남는지 확인
>> 톰캣로그와 로그는 별개로 남는다.
>> 톰캣로그를 없앨려면은 톰캣에서 안남게 따로 설정하자.
>> System.out.println는 톰캣로그에만 남는다.
> 로컬에 톰캣을 설치해서 확인하자. 
>> 배포가 되는지 확인. 현재는 war로 배포했다. 나중에는 아마존같은곳에 배포해보자.
> DB로그 확인필요


이후 조절할 것들
# 로그 길이좀 줄이자. 인간적으로 왜케들 기냐.
# 쿼리 로그 : 쿼리 로그를 어디까지 보여줄것인가? 
# 개발과 운영의 로그 보여주는것 분리
# 재기동 없이 로그 등급 변경 반영여부
