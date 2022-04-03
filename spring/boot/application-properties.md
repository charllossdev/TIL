# 참조
* https://www.latera.kr/reference/java/2019-09-29-spring-boot-config-externalize/

# Spring boot application.properties 설정
application.properties란 SpringBoot 어플리케이션에서 사용하는 여러가지 설정 값을 정의할 수 있는 설정 파일로 애플리케이션을 구동할 때 자동으로 로딩

* Spring Boot는 동일한 애플리케이션 코드를 다른 환경에서 작업할 수 있도록 설정을 외부에서 전달할 수 있습니다.

* 사용 가능한 방법
  + `.properties` 파일
  + `YAML` 파일
  + 환경 변수
  + 커맨드 라인 인자

## 우선 순위
application.properties를 설정할 수 있는 방법은 매우 다양하며, 설정에 우선순위가 있다.

1. 홈 디렉토리에 있는 spring-boot-dev-tools.properties([전역 설정 프로퍼티](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.devtools))
2. 테스트 코드 @TestPropertySource
3. @SpringBootTest properties attr
4. 커맨드 라인 args(ex:` --spring.config.location`)
5. SPRING_APPLICATION_JSON (환경 변수 또는 시스템 프로티) 에 들어있는 프로퍼티
6. `ServletConfig` 초기 파라미터
7. `ServletContext` 초기 파라미터
8. `java:comp/env` JNDI 애트리뷰트
9. `System.getProperties()` 자바 시스템 프로퍼티
10. OS 환경 변수
11. `random.*`의 프로퍼티 `RandomValuePropertySource`
12. JAR 밖에 있는 특정 프로파일용 `application-{profile}.properties`
13. JAR 안에 있는 특정 프로파일용 `application-{profile}.properties`
14. JAR 밖에 있는 `application.properties`
15. JAR 안에 있는 `application.properties`
16. `@Configuration` 클래스의 `@PropertySource`
17. 기본(Default) 프로퍼티 (SpringApplication.setDefaultProperties)

* **우선 순위 역순으로 설정들이 오버라이딩되어 설정**

### application.properties 파일 적용
`Spring application`은 다음 경로의 `application.properties`에서 프로퍼티를 불러와 `Spring Enviroment`에 추가

우선 순위
1. `file:./config/`
2. `file:./`
3. `classpath:/config/`
4. `classpath:/`

설정 위치는 역순으로 검색하여 적용
기본값으로 설정된 경로들은 classpath:/,classpath:/config/,file:./,file:./config/
4 -> 3 -> 2 -> 1 순서로 검색되어 오버라이딩 적용
