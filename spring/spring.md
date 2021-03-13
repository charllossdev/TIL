
# Spring
CS지식 및 면접 준비로 Spring 관련한 키워드 정리

* [Srping IoC](#ioc)

## IoC
IoC : Inversion of Control

+ IoC Container -> ApplicationContext -> BeanFactory
  - [Application Context](#application-context)
+ 역활
  - Application의 Component 중앙 저장소(@Bean 저장소)
  - @Bean 인스턴스 생성 및 의존 관계 설정
  - @Bean 설정 소스 부터 @Bean 정의를 참조하여 @Bean 을 구성하고 제공
+ 특징
  - 싱글톤 scope으로 빈을 등록하여 프로세스 관리(멀티쓰레드 환경에서 싱글톤 Scope으로 객체를 관리 및 의존성 주입)
  - `<->` 프로토타입은 싱글톤이 아닌 매번 다른 객체를 생성하는 @Bean
+ @Autowired
  - [Autowired](#autowired)

## Application Context
[Interface ApplicationContext](https://docs.spring.io/spring-framework/docs/5.0.8.RELEASE/javadoc-api/org/springframework/context/ApplicationContext.html) : BeanFactory 를 상속하는 인터페이스
+ 기능
  - 메세지 소스 처리 기능(i18n)
  - 이벤트 발행 기능
  - 리소스 로딩 기능
+ 설정
  - ClassPathXmlApplicationContext (XML)
  - AnnotationConfigApplicationContext (Java)

## Bean
[Spring IoC Container](#ioc) 가 관리하는 객체 인스턴스
+ 역활
  - 의존성 관리 `ex) @Mock Test`
  - 라이프 사이클 인터페이스를 통해 관여 가능
+ 등록
  - @ComponentScan: Application이 최초 로드 될때, @ComponentScan 을 통해 @Component로 등록된 객체를 등록
    * 특정 패키지 이하의 모든 클래스 중에 @Component 클래스를 @Bean 으로 자동 등록
    * @Component 객체: 어노테이션으로 등록(@Controller, @Service, @Repository ...)
+ 생존주기(스코프)
  - 싱글톤: 하나의 인스턴스
  - 프로토타입: 매번 다른 인스턴스
    * Request
    * Session
    * WebSocket
+ 라이프사이클 인터페이스

## Autowired
@Autowired: 필요한 의존 객체의 타입에 해당하는 @Bean을 찾아 [의존성 주입(Dependency Injection)](#dependency-injection)

+ 의존성 주입 방법
  - Constructor(Spring 4.3 부터 @Autowired 생략가능)
    * 생성자 DI 장점: 필수적으로 사용해야하는 레퍼런스 없이는 인스턴스를 생성 할 수 없도록 강제하는 방법
    * 생성자 DI 단점: 순환 참조가 발생하여 에러가 발생 할 수 있다.
  - Setter
  - Filed
+ 같은 타입의 빈이 여러개 일때
  - **@Primary**
  - Qualifier: 빈 이름으로 주입(빈 이름을 String으로 입력해야해서, not type safe)
+ 동작원리
  - Application 최초 로딩 시, [모든 @Bean을 등록](#bean)을 하고(@ComponentScan), [의존성 주입(Dependency Injection)](#dependency-injection)한다.
  - BeanPostProcessor: 새로 만든 빈 인스턴스를 수정할 수 있는 라이프 사이클 인터페이스
  - AutowiredAnnotationBeanPostProcessor

## Dependency Injection





## Spring AOP
## Proxy parttern
## Spring PSA
  + 생성자 단점: 순환 참조가 발생하여 에러가 발생 할 수 있다.
## Spring MVC
## Spring Transaction
