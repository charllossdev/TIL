# TDD

- https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto.testing
- https://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/html/boot-features-testing.html

* 단위 테스트: 메소드 단위 테스트
* 통합 테스트: 여러 작업 단위가 연계된 워크 플로우 테스트(객체 간, 서비스 간, 시스템 간)
* 기능 테스트: 공개된 API의 가장 바깥쪽에 해당하는 코드 테스트(Controller, Security, http)
* 부하 테스트: 주어진 단위 시간 동안 어플리케이션이 얼마나 많은 요청을 처리할 수 있는지 검사
* 인수 테스트: 고객 또는 대리인이 정의되어진 모든 목적에 부합되는지 확인하는 테스트

# TDD 장점

* 변화에 대한 두려움을 줄여줌 (리펙토링)
* 디버깅 시간 절약
* 동작하는 문서 역활
* 오버 엔지니어링 방지
* 설계에 대한 피드백이 빠름 -> 설계 수정 용이

## @WebMvcTest
* MVC를 위한 테스트, 컨트롤러가 예상되로 동작하는지 테스트
* @WebMvcTest 어노테이션을 사용시 하위 내용만 스캔하도록 제한(가벼운 테스팅 가능)
  - @Controller
  - @ControllerAdvice
  - @JsonComponent
  - Converter
  - GenericConverter
  - Filter
  - HandlerInterceptor
  - WebMvcConfigurer
* @MockBean, @MockMVC를 자동 구성하여 테스트
* 장점
  - Spring Security 지원
  - WebApplication 관련된 Bean들만 등록하기 때문에 통합 테스트 보다 빠름
  - 통합 테스트를 진행하기 어려운 테스트 진행 가능
* 단점
  - 요청부터 응답까지 모든 테스트를 Mock기반으로 테스트 하기 때문에 실제 환경에서는 제대로 동작하지 않을 있음

## @WebFluxTest
* 비동기-논블록킹 리액티브 개발에 사용되며 서비스간 호출이 많은 마이크로 아키텍처에 적합

## @DataJpaTest
* JPA 관련된 설정만 로드
* 설정이 정상적인지, JPA를 사용해서 데이터를 올바르게 조회,생성,수정,삭제 하는지 테스트
* @Entity 클래스를 스캔하여 스프링 데이터 JPA 저장소를 구성(다른 컴포넌트를 스캔하지 않음)
* @Transactional 어노테이션을 포함하고 있기 때문에 따로 선언하지 않아도 됨

## @RestClientTest
* @RestClientTest 를 사용하여 REST 클라이언트 테스트
* REST 통신의 JSON 형식이 예상대로 응답을 반환하는지 테스트
* Apache HttpClient나 Spring의 RestTemplate을 사용하여 외부 서버에 웹 요청을 보내는 경우에 이에 응답할 Mock서버를 만드는 것이라고 생각하면 됨

## @JsonTest
* @JsonTest 는 JSON serialization과 deserialization 테스트를 편하게 가능
* JSON의 직렬화, 역직렬화를 수행하는 라이브러리인 Gson과 Jackson의 테스트 제공
