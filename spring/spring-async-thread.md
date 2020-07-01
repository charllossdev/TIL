# Spring Async Thread

Spring Async annotation를 이용하여 간단하게 비동기 처리가 가능하다.
`@async` 를 선언한 메소드를 호출한 호출자는 즉시 리턴하고 실제 실행은 Spring TaskExecutor에 의해 실행.
메서드는 Future 타입 값을 리턴하여 해당 Future에 get() 메서드를 이용하여 작업 수행을 할 수 있다.



### Spring TaskExecutor
Executor는 스레드 풀의 개념으로 Java 5에서 도입된 개념. 구현체가 실제 Pool이라고 확신 할 수 없어 Executor(직역: 집행자)라 사용.
TaskExecutor 인터페이스는 실행하는 Task를 받고 execute 메서드를 갖는다.

### TaskExecutor 종류

* SimpleAsyncTaskExecutor
  - 이 구현에는 어떤 스레드도 재사용하지 않고 호출마다 새로운 스레드를 시작
  - 동시접속 제한(concurrency limit)을 지원 제한 수가 넘어서면 빈 공간이 생길 때까지 모든 요청을 block
* SyncTaskExecutor
  - 호출을 비동기적으로 수행하지 않는다. 대신, 각각의 호출은 호출 쓰레드로 대체된다. 간단한 테스트케이스와 같이 필요하지 않은 멀티쓰레드 상황에서 사용된다.
* ConcurrentTaskExecutor
  - java.util.concurrent.Executor Wrapper.
* SimpleThreadPoolTaskExecutor
  - Spring의 생명주기 콜백을 듣는 Quartz의 SimpleThreadPool의 하위클래스.
  - Quartz와 Quartz가 아닌 컴포넌트간에 공유될 필요가 있는 쓰레드 풀
* ThreadPoolTaskExecutor
  - 자바 5에서 가장 일반적으로 사용.
  - java.util.concurrent.ThreadPoolExecutor를 구성하는 bean 프로퍼티를 노출하고 이를 TaskExecutor로 감싼다.
* TimerTaskExecutor
  - 지원되는 구현물 중 하나의 TimerTask를 사용.
  - 쓰레드에서 동기적이더라도 메소드 호출이 개별 쓰레드에서 수행되어 SyncTaskExecutor와 다르다.
* WorkManagerTaskExecutor
  - 지원되는 구현물 중 하나로 CommonJ WorkManager을 사용
  - Spring 컨텍스트에서 CommonJ WorkManager참조를 셋팅하기 위한 중심적이고 편리한 클래스
  - SimpleThreadPoolTaskExecutor와 유사하게, 이 클래스는 WorkManager인터페이스를 구현하고 WorkManager만큼 직접 사용
