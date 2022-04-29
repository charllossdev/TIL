# Kotlin
* `NullSafe`, `?`, `?.let{}`
* `var` vs `val`
  + var: mutable object
  + val: immutable object



* let null check
* https://tourspace.tistory.com/208


## Retrofit
Retrofit은 위에서 나온 "Square"라는 회사가 만든 OkHttp 라이브러리의 상위 구현체입니다.
Retrofit은 OkHttp를 네트워크 계층으로 활용하고 그 위에 구축 되었습니다.

일단 Retrofit은 3가지 구성요소가 있습니다.

DTO(POJO): 'Data Transfer Object', 'Plain Old Java Object' 형태의 모델(Model) / JSON 타입변환에 사용
Interface: 사용할 HTTP CRUD동작(메소드) 들을 정의해놓은 인터페이스
CRUD ( Create / Read / Update / Delete ) -> HTTP Method ( POST / GET / PUT / DELETE )
Retrofit.Builder Class: Interface를 사용할 인스턴스, baseUrl(URL) / Converter(변환기) 설정

https://velog.io/@gosgjung/%EC%BD%94%ED%8B%80%EB%A6%B0%EC%96%B8%EC%96%B4-%EA%B8%B0%EB%B3%B8%EA%B0%9C%EB%85%90-%EC%B4%9D%EC%A0%95%EB%A6%AC-%EC%8A%A4%EC%95%95%EC%A3%BC%EC%9D%98


## Feign Client

https://kangwoojin.github.io/programing/open-feign-1/

### Gradle dependencies

```properties
dependencies {
    ...
    implementation("org.springframework.cloud:spring-cloud-starter-openfeign")
    ...
}
```

### Open feign setting

```java
@EnableFeignClients
```

* `@EnableFeignClients` 를 추가
  + `@FeignClient` 어노테이션이 붙어 있는 Client들을 Bean으로 등록


### Logging Config setting

```java
@Configuration
class LoggingConfiguration {
    @Bean
    fun feignLoggerLevel(): Logger.Level {
        return Logger.Level.FULL
    }
}
```

* Configuration @Bean 등록

```java
  @FeignClient(configuration = [LoggingConfiguration::class])
```

* `@FeignClient` configuration 속성에 추가
