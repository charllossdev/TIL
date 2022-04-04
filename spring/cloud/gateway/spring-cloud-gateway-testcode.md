# Spring cloud gatyeway 테스트
* SCG는 MSA 패턴 중 Edge Server 패턴을 구현할 수 있게 해주는 라이브러리
* 지금까지 Edge Server는 Netflix zuul을 사용해 왔었는데, 2018년 12월에 deprecated 되고 후속타로 Pivotal에서 만든 Reactive 방식의 Spring cloud gateway
* SCG의 기본적인 역활은 라우팅과 인증
  + 이 과정을 테스트 하기 위해서는 라우팅이 된 후에 접근하게 될 upstream 서버를 흉내낼 수 있는 대역이 필요
  + 인증 테스트를 위해 Spring Security가 필요
  > upstream: 클라이언트나 로컬 기기(PC or Mobile)가 서버나 원격 호스트로 보내지는(전송되는) 데이터 또는 보내는 과정

* `@WebFluxTest` 테스트는 라우팅 설정이 반영되지 않은 테스트 서버 인스턴스가 구동되므로, 무겁더라도 모슨 인스턴스를 구동하는 `@SpringBootTest` 테스트로 진행
* upstream 서버 대역 테스트
  + Srping Mock Rest Service Server
  + Spring Cloud Contract WireMock


# Spring Mock Rest Service Server

### 구현 필요!!!

# Spring Cloud Contract WireMock Test Code

```java

// server.port 로 지정된 포트로 Edge Server 인스턴스 실행
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.DEFINED_PORT)
class EdgeServerApplicationTests {

    private static final WireMockServer wireMockServer = new WireMockServer(WireMockSpring.options().port(8080));  // upstream 서버의 port 지정

    private WebTestClient client;

    @Autowired
    private Environment environment;

    @BeforeAll
    static void beforeAll() {
        wireMockServer.start();
    }

    @BeforeEach
    void beforeEach() {
        // client는 Edge Server에 요청을 보내도록 설정
        client = WebTestClient.bindToServer().baseUrl("http://localhost:" + environment.getProperty("server.port")).build();
    }

    @AfterEach
    void afterEach() {
        wireMockServer.resetAll();
    }

    @AfterAll
    static void afterAll() {
        wireMockServer.shutdown();
    }


    @DisplayName("인증 없이 Seller를 조회하면 401이 반환된다.") // 테스트 작성 당시(Security 추가 안 된 상태)에는 그냥 404 반환
    @Test
    void findSellerWithoutAuthenticated() {

        wireMockServer.stubFor(
                WireMock.get(WireMock.urlEqualTo("/v1/sellers/1"))
                        .willReturn(WireMock.aResponse().withStatus(HttpStatus.OK))
        );


        client.get()
                .uri("/v1/sellers/1")
                .exchange()
                .expectStatus().isUnauthorized();
    }
  }
```

## 설정을 통해 포트 설정 코드

```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.DEFINED_PORT)
class EdgeServerApplicationTests {

    // 8080 으로 하드코딩하지 않고 application.yml 에 지정된 값을 이용해서 static 변수 초기화 트릭 사용
    @Value("${upstream.monolith.port}")
    void setUpstreamServerPort(int port) {
        if (wireMockServer == null) {
            wireMockServer =
                    new WireMockServer(WireMockSpring.options().port(port));
            wireMockServer.start();
        }
    }
  }
```

# Spring Cloud Contract WireMock
