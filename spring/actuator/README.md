# Actuator

3.1 Health 체크 커스텀 하기 - 1
healthIndecator 를 구현하여 Health 를 커스텀 할 수 있다.

@Component
public class MyHealthIndicator implements HealthIndicator {

    @Override
    public Health health() {
        int errorCode = check();
        if (errorCode != 0) {
            return Health.down().withDetail("Error Code", errorCode).build();
        }
        return Health.up().build();
    }

    private int check() {
        // perform some specific health check
        return ...
    }

}






3.1 Health 체크 커스텀 하기 - 2
@Component
public class ApplicationHealthIndicator implements HealthIndicator {
    private final AtomicReference<Health> healthRefer = new AtomicReference<>(Health.down().build());

    @Override
    public Health health() {
        return healthRefer.get();
    }

    public void setHealth(Health health) {
        this.healthRefer.set(health);
    }
}
@Slf4j
@RestController
@RequestMapping(path = "/health")
@RequiredArgsConstructor
public class L7CheckApi {
    private final ApplicationHealthIndicator healthIndicator;

    @PutMapping(path = "/up")
    public void up() {
        final Health up = Health.up().build();
        healthIndicator.setHealth(up);
    }

    @PutMapping(path = "/down")
    public void down() {
        final Health down = Health.down().build();
        healthIndicator.setHealth(down);
    }
}


https://truehong.tistory.com/124
