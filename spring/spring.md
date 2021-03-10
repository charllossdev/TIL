
# Spring
CS지식 및 면접 준비로 Spring 관련한 키워드 정리

* Spring IoC
  + Inversion of Control
  + IoC Container -> ApplicationContext -> BeanFactory
  + 싱글톤 scope으로 빈을 등록하여 프로세스 관리(멀티쓰레드 환경에서 싱글톤 Scope으로 객체를 관리 및 의존성 주입)
    - 프로토타입은 싱글톤이 아닌 매번 다른 객체를 생성하는 @Bean
* Bean
  + 의존성 관리 `ex) @Mock Test`
  + 라이프 사이클 인터페이스를 통해 관여 가능
  + 등록 과정: @ComponentScan 이 @Component로 등록된 객체를 등록
  + 등록: @Component 어노테이션으로 등록(@Controller, @Service, @Repository ...)
* Dependency Injection
  + 생성자
    - 생성자 DI 장점: 필수적으로 사용해야하는 레퍼런스 없이는 인스턴스를 생성 할 수 없도록 강제하는 방법
    - 생성자 DI 단점: 순환 참조가 발생하여 에러가 발생 할 수 있다.
  + @Autowired

* Spring AOP
* Proxy parttern
* Spring PSA
  + 생성자 단점: 순환 참조가 발생하여 에러가 발생 할 수 있다.
* Spring MVC
* Spring Transaction
