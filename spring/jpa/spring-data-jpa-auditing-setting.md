
# JPA Auditing으로 생성일/수정일 자동화하기
https://velog.io/@conatuseus/2019-12-06-2212-%EC%9E%91%EC%84%B1%EB%90%A8-1sk3u75zo9

현재 진행중인 프로젝트에서 해당 데이터의 생성시간과 수정시간을 관리해야 할 부분이 있었습니다.
예를 들어, 주문 도메인에서 주문한 시간과 주문 내용을 수정한 시간이 필요했습니다.
그리고 결제 도메인에서는 결제 요청한 시간과 결제 내용을 수정하는 시간이 필요했습니다.

현재 개발 초기 단계이지만 벌써 두 곳에서 생성시간/수정시간이 필요했습니다.
언제 만들어졌는지, 언제 수정되었는지 등은 차후 더 필요해질 것이라 생각 생각했습니다.

여기저기 찾아보다가 <스프링 부트와 AWS로 혼자 구현하는 웹서비스 - 이동욱님> 책에 해당 내용이 있었습니다. 이제 그 내용을 읽고 적용한 것을 같이 공유하고자 합니다.


## JPA Auditing으로 생성시간/수정시간 자동화하기
보통 엔티티는 해당 데이터의 생성시간과 수정시간을 포함합니다.
그렇다 보니 매번 DB에 insert하기 전, update하기 전에 날짜 데이터를 등록/수정하는 코드가 여기저기 들어갑니다. 아래와 같이 말이죠.

```java
// 생성일 추가 코드 예제
public void savePosts() {
  ...
  posts.setCreateDate(new LocalDate());
  postsRepository.save(posts);
  ...
}
```
이런 단순하고 반복적인 코드가 모든 테이블과 서비스 메서드에 포함되어야 한다고 생각하면 어마어마하게 귀찮고 코드가 지저분해집니다. 그래서 이 문제를 해결할 수 있는 것이 JPA Auditing입니다.

## 적용하기

### Jpa Auditing Entity 생성

```java
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseTimeEntity {

    @CreatedDate
    private LocalDateTime createdDate;

    @LastModifiedDate
    private LocalDateTime modifiedDate;

    public LocalDateTime getCreatedDate() {
        return createdDate;
    }

    public LocalDateTime getModifiedDate() {
        return modifiedDate;
    }
}
```

먼저 BaseTimeEntity 클래스를 만듭니다.
이 클래스는 모든 Entity의 상위 클래스가 되어 Entity 들의 createdDate, modifiedDate를 자동으로 관리하는 역할입니다.

* @MappedSuperclass : JPA Entity 클래스들이 BaseTimeEntity를 상속할 경우 필드들(createdDate, modifiedDate)도 칼럼으로 인식하도록 합니다.
* @EntityListeners (AuditingEntityListener.class): BaseTimeEntiy 클래스에 Auditing 기능을 포함시킵니다.
* @CreatedDate: Entity가 생성되어 저장될 때 시간이 자동 저장됩니다.
* @LastModifiedDate: 조회한 Entity의 값을 변경할 때 시간이 자동 저장됩니다.

### Extens Jpa Auditing Entity

그리고 저는 Order 클래스가 BaseTimeEntity를 상속하도록 했습니다.
현재 개발 초기 단계라서 다른 데이터 없이 id, 생성시간, 수정시간만 가지도록 했습니다.

```java
@Entity
@Table(name = "ORDERS")
public class Order extends BaseTimeEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    public Order() {
    }
}
```

### Jpa Auditing Set

마지막으로 JPA Auditing 어노테이션들을 모두 활성화할 수 있도록 Application 클래스에 활성화 어노테이션을 추가합니다.

```java
@EnableJpaAuditing
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(CaffeineApplication.class, args);
    }
}
```

* @EnableJpaAuditing: JPA Auditing을 활성화 하기 위한 어노테이션입니다.

### Test

```java
@SpringBootTest
public class OrderTest {

    @Autowired
    OrderRepository orderRepository;

    @Test
    public void BaseTimeEntity_등록() {
        //given
        LocalDateTime now = LocalDateTime.of(2019, 12, 6, 0, 0, 0);
        orderRepository.save(new Order());

        //when
        List<Order> orders = orderRepository.findAll();

        //then
        Order order = orders.get(0);

        System.out.println(">>>>> createDate = "+order.getCreatedDate() + ", modifiedDate = "+order.getModifiedDate());

        assertThat(order.getCreatedDate()).isAfter(now);
        assertThat(order.getModifiedDate()).isAfter(now);
    }
}
```
