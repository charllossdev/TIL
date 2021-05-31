
# BDD
* BDD는 (Behavior Driven Development)로 TDD를 근간으로 파생된 개발 방법
* BDD는 시나리오를  기반으로 테스트 케이스를 작성하며 함수 단위 테스트를 권장하지 않음
* 시나리오
  + Feature : 테스트에 대상의 기능/책임을 명시합니다
  + Scenario : 테스트 목적에 대한 상황을 설명합니다
  + Given : 시나리오 진행에 필요한 값을 설정, 테스트의 상태를 설정
  + When : 시나리오 진행 필요 조건 명시, 테스트 하고자 하는 행동
  + Then : 시나리오를 완료했을 때 보장해야하는 결과 명시, 예상되는 변화 설명
* 시나리오 예제
  ```ruby
  Feature: 지하철 경로 탐색 기능

  Background: 지하철, 노선 등록
    Given 지하철역 등록되어 있음지(출발지, 목적지)
    And 지하철 노선 등록되어 있음(테스트를 위해 여러 노선)
    And 지하철 노선에 지하철역 등록되어 있음
    And 지하철 노선에 구간 등록되어 있음

  Scenario: 지하철 경로 탐색
    When 출발역와 도착역 경로 요청
    Then 연결된 한 노선의 최단거리 조회
    Then 포함된 여러 노선의 구간 거리를 비교하여 최단거리 조회
  ```
  ```java
  @BeforeEach
  void setUp() {
    지하철_초기_데이터_생성();
  }

  private void 지하철_초기_데이터_생성() {
    소요산역 = 전철역_생성(1L, "소요산역");
    인천역 = 전철역_생성(2L, "인천역");
    시청역 = 전철역_생성(3L, "시청역");
    강남역 = 전철역_생성(4L, "강남역");
    주안역 = 전철역_생성(5L, "주안역");
    동암역 = 전철역_생성(6L, "동암역");
    부평역 = 전철역_생성(7L, "부평역");
    구로역 = 전철역_생성(8L, "구로역");

    line1 = 라인_생성("1호선", "blue", 인천역, 소요산역, 500);
    line2 = 라인_생성("2호선", "green", 시청역, 강남역, 300, 900);
    구간추가(line1, 인천역, 주안역, 10);
    구간추가(line1, 주안역, 동암역, 20);
    구간추가(line1, 동암역, 부평역, 30);
    구간추가(line1, 부평역, 구로역, 40);
    구간추가(line1, 구로역, 시청역, 50);
  }

  @DisplayName("PathFinder 경로검색 테스트")
  @Test
  void createPathFinderTest() {
    // given
    List<Line> lines = Arrays.asList(line1, line2);
    PathFinder finder = new PathFinder(lines);

    // when
    finder.selectShortPath(인천역, 강남역);

    // then
    assertAll(
      () -> assertThat(finder.stations()).isNotNull(),
      () -> assertThat(finder.stations()).hasSize(7),
      () -> assertThat(finder.distance()).isEqualTo(Distance.of(450))
    );
  }
  ```

  ```ruby
  Feature: 즐겨찾기를 기능

  Background: 지하철, 노선, 회원
    Given 지하철역 등록되어 있음
    And 지하철 노선 등록되어 있음
    And 지하철 노선에 지하철에 등록되어 있음
    And 회원 등록되어 있음
    And 로그인 되어 있음

  Scenario: 즐겨찾기 관리 기능
    When 즐겨찾기 생성을 요청
    Then 즐겨찾기 생성됨
    When 즐겨찾기 목록 조회 요청
    Then 즐겨찾기 목록 조회 됨
    When 즐겨찾기 삭제 요청
    Then 즐겨찾기 삭제됨
  ```

  ```java

  @BeforeEach
  public void setUp() {
    super.setUp();

    강남역 = StationAcceptanceTest.지하철역_등록되어_있음("강남역").as(StationResponse.class);
    양재역 = StationAcceptanceTest.지하철역_등록되어_있음("양재역").as(StationResponse.class);
    교대역 = StationAcceptanceTest.지하철역_등록되어_있음("교대역").as(StationResponse.class);
    인천역 = StationAcceptanceTest.지하철역_등록되어_있음("인천역").as(StationResponse.class);
    남부터미널역 = StationAcceptanceTest.지하철역_등록되어_있음("남부터미널역").as(StationResponse.class);

    신분당선 = LineAcceptanceTest.지하철_노선_등록되어_있음("신분당선", "bg-red-600", 강남역.getId(), 양재역.getId(), 10);
    이호선 = LineAcceptanceTest.지하철_노선_등록되어_있음("이호선", "bg-red-600", 교대역.getId(), 강남역.getId(), 10);
    삼호선 = LineAcceptanceTest.지하철_노선_등록되어_있음("삼호선", "bg-red-600", 교대역.getId(), 양재역.getId(), 5);

    LineSectionAcceptanceTest.지하철_노선에_지하철역_등록_요청(삼호선, 교대역, 남부터미널역, 3);

    MemberAcceptanceTest.회원_생성을_요청(MemberAcceptanceTest.EMAIL, MemberAcceptanceTest.PASSWORD,
      MemberAcceptanceTest.AGE);

    로그인_토큰 = AuthAcceptanceTest.로그인_토큰_요청(MemberAcceptanceTest.EMAIL, MemberAcceptanceTest.PASSWORD)
      .as(TokenResponse.class)
      .getAccessToken();
  }
  
  @DisplayName("즐겨찾기 조회 테스트")
  @Test
  void showFavoriteTest() {
    // given
    given(memberService.findMemberById(1L)).willReturn(회원);
    given(favoriteRepository.findAllByMember(회원)).willReturn(Arrays.asList(
      new Favorite(1L, 회원, 시청역, 서울역),
      new Favorite(2L, 회원, 시청역, 주안역),
      new Favorite(3L, 회원, 시청역, 강남역),
      new Favorite(4L, 회원, 시청역, 양재역)
    ));

    // when
    List<FavoriteResponse> favorites = favoriteService.findFavorites(회원.getId());

    // then
    assertAll(
      () -> assertThat(favorites).isNotNull(),
      () -> assertThat(favorites).hasSize(4)
    );
  }
  ```

  ```java
  @DisplayName("지하철 즐겨찾기 목록 조회 요청함")
  @Test
  void showFavoriteTest() {
    // given
    즐겨찾기_생성_요청(로그인_토큰, 교대역.getId(), 양재역.getId());
    즐겨찾기_생성_요청(로그인_토큰, 강남역.getId(), 양재역.getId());
    즐겨찾기_생성_요청(로그인_토큰, 강남역.getId(), 교대역.getId());
    즐겨찾기_생성_요청(로그인_토큰, 양재역.getId(), 인천역.getId());

    // when
    ExtractableResponse<Response> response = 즐겨찾기_조회_요청(로그인_토큰);

    // then
    즐겨찾기_목록_조회됨(response, 4);
  }
  ```
