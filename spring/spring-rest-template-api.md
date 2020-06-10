# Spring Rest Template API
기존 API통신을 사용하다가, Spring에서 지원하는 기술이 있어서 변경

HTTP 클라이언트 라이브러리를 통해 높은 수준의 API를 제공한다. REST 엔드포인트를 코드 한줄로 호출하기 쉽게 해준다. 오버로드된 메소드들은 다음과 같다.


## RestTemplate Init

기본 생성자는 java.net.HttpURLConnection 라이브러리를 사용한다. ClientHttpRequestFactory를 사용하여 다른 HTTP 라이브러리로 바꿀 수 있다. 스프링은 Apache HttpComponents, Netty, OkHttp를 지원한다.

```java
RestTemplate template = new RestTemplate(new HttpComponentsClientHttpRequestFactory());
```

각 ClientHttpRequestFactory는 기본 HTTP 클라이언트 라이브러리(예: 자격 증명, 연결 풀링 등)에 대한 구성 옵션을 제공한다. 주의할 점은 java.net 패키지의 HTTP 구현체를 사용할 경우 401 상태를 가진 응답 객체에 접근할 때 익셉션이 발생할 수 있으므로, 이럴 경우 다른 HTTP 라이브러리 사용해야 한다.


## URIs
대부분의 RestTemplate 메소드는 String vararg 또는 Map<String, String>을 통해 URI 템블릿과 URI 템플릿 변수를 허용한다.

```java
/* String vararg */ String result = restTemplate.getForObject( "http://example.com/hotels/{hotel}/bookings/{booking}", String.class, "42", "21"); /* Map<String, String> */ Map<String, String> vars = Collections.singletonMap("hotel", "42"); String result = restTemplate.getForObject( "http://example.com/hotels/{hotel}/rooms/{hotel}", String.class, vars);

```

URI 템플릿은 자동으로 인코딩 된다.

``` java
restTemplate.getForObject("http://example.com/hotel list", String.class); // 요청 url: "http://example.com/hotel%20list"

```
RestTemplate의 uriTemplateHandler 속성을 사용하여 URI 인코딩 방법을 지정할 수 있다 또는 java.net.URI를 사용하여 이를 사용하는 RestTemplate 메소드에 인자로 전달할 수 있다.
 

 ## Headers
 exhcnage() 메소드를 사용하여 요청 헤더를 지정할 수 있다.

```java
String uriTemplate = "http://example.com/hotels/{hotel}"; URI uri = UriComponentsBuilder.fromUriString(uriTemplate).build(42); RequestEntity<Void> requestEntity = RequestEntity.get(uri) .header(("MyRequestHeader", "MyValue") .build(); ResponseEntity<String> response = template.exchange(requestEntity, String.class); String responseHeader = response.getHeaders().getFirst("MyResponseHeader"); String body = response.getBody();

```

ResponseEntity를 반환하는 RestTemplate 의 여러 메소드를 통해 응답 헤더를 얻을 수 있다.


## Body

RestTemplate 메서드에 전달되고 반환되는 객체는 HttpMessageConverter의 도움으로 raw content로 변환된다.

POST 메서드에서 입력된 객체는 요청 body에 직렬화된다.

```java
URI location = template.postForLocation("http://example.com/people", person);
```

요청의 Content-Type 헤더를 명시적으로 설정할 필요는 없다. 대부분의 경우 소스 객체 타입에 따라 호환되는 메시지 컨버터를 찾을 수 있고, 선택한 메시지 컨버터가 적절히 content-type을 설정한다. 필요한 경우 exchange 메서드를 사용하여 Content-Type 요청 헤더를 명시적으로 제공할 수 있으며, 이는 선택된 메시지 컨버터에 영향을 미칠 수 있다.

GET 메서드에서는 응답의 body가 출력 객체로 역직렬화된다.
```java
Person person = restTemplate.getForObject("http://example.com/people/{id}", Person.class, 42);

```

요청의 Accept 헤더는 명시적으로 설정할 필요가 없다. 대부분의 경우 Accept 헤더를 예상 응답 유형에 따라 호환되는 메시지 컨버터를 찾을 수 있다. 이 컨버터는 Accept 헤더를 채우는데 도움이 된다. 필요한 경우 exchange 메서드를 사용하여 Accept헤더를 명시적으로 제공할 수 있다.

기본적으로 RestTemplate은 선택적인 변환 라이브러리가 있는지 확인하는데 도움이 되는 클래스패쓰 검사에 따라 모든 내장 메시지 컨버터들을 등록한다. 또, 명시적으로 메시지 컨버터를 설정할 수 있다.

