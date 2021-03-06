# Spring Inversion of Control
일반적인 의존상태 대한 제어권: "내가 사용할 의존성은 내가 만든다."
> Spring IoC : 의존성 제어의 역전

* 내가 사용할 의존성을 외부에서 설정하여 의존성을 주입하는 방법


# Spring IoC(Inversion of Control) Container

* BeanFactory == IoC Container
* ApplicationContext <- BeanFactory 상속받는다.

직접사용하는것이 아니라, Bean으로 등록된 인스턴스들을 관리하는 것이 ApplicationContext 이고,

싱글톤 스코프(객체 하나를 어플리케이션 전체에서 사용 할 수 있다.)
멀티 쓰레드 환경에서 싱글 스코프를 관리하는일은 굉장히 어려운 일이지만, IoC 컨테이너에 등록되어있는 빈을 가져와서 사용하는 환경이라면 쉽게 사용이 가능하다.

# Bean
IoC Container -> 즉 ApplicationContext에 담고있는 객체를 빈이라고 빈이라고 한다.
빈(@Bean)을 만들고 엮어주며 제공해주는 역활

빈 설정
* 이름 또는 ID
* 타입
* 스코프

Component Scanning
@Component
@Repository
@Service
@Controller
@Configuration
또는 직접 일일히 XML이나 자바 설정 파일에 등록

라이프 사이클 콜백 -> 어노테이션 프로세서로 인해서 @Component로 등록된 어노테이션을 모두 빈으로 등록한다. -> 컴포넌트 스캔

> Repository 같은 경우 JPA를 통해서 Repository 상속받고 있는 인터페이스의 구현체를 만들어서 그 클래스를 빈으로 등록된다.
