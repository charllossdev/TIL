# LogBack
* java opensource framework
* SLF4J 구현체
* Spring boot 기본으로 설정(별도 라이브러리 추가 X)
* log4j, log4j2 등과 성능을 비교했을때, logback이 더 훌륭한 성능을 보여준다.
  
## LogBack Setting
* logback을 이용해 로깅을 하기 위해 필요한 주요 설정
  + Logger
  + Appender
  + Encoder
* logback 설정 파일을 찾아서 참조
  1. `classpath` 경로(`resources` 디렉토리 밑)에 `logback-srping.xml` 설정파일을 찾는다.
  2. `logback-spring.xml` 파일이 없다면, `application.properties(yml)` 파일에서 logback 설정을 찾는다.
  3. 만약, `logback-spring.xml` 과 `application.properties(yml)` 에 설정이 동시에 있다면, 
     1. `application.properties(yml)` 설정을 먼저 적용
     2. 그 후 `logback-spring.xml` 적용


