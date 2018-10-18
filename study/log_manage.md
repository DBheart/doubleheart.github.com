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

log4j.xml
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


확인사항
> 톰캣로그와 중복으로 남는지 확인
> 어떻게 확인하지? 로컬에서는 안되는것 같고... 로컬 톰캣에 해봐야하나.. ㅃ


이후 조절할 것들
# 쿼리 로그 : 쿼리 로그를 어디까지 보여줄것인가? 
# 개발과 운영의 로그 보여주는것 분리
# 재기동 없이 로그 등급 변경 반영여부
