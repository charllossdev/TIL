
# Cross-origin resource sharing
![](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/cors_principle.png)

* CORS: 교차 출처 리소스 공유(Cross-Origin Resource Sharing)
* CORS는 최초에 리소스를 제공한 출처(origin)와 다른 출처의 리소스를 요청하는 경우(cross-origin 요청), 특정 HTTP header를 사용하여 웹 애플리케이션의 cross-origin 요청을 브라우저가 제한적으로 허용하는 정책
* 즉 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
* 웹 애플리케이션은 리소스가 자신의 출처(도메인, 프로토콜, 포트)와 다를 때 교차 출처 HTTP 요청을 실행

> `Origin` 이란
> URL의 scheme(protocol), host(domain), port로 이루어진 값
> origin이 같다는 것은 URL의 scheme과 host, port가 모두 같음을 의미

## CORS의 필요성
* 보안상 이유로 브라우저는 `SOP`(Same-Origin Policy)로 동일 출처 정책
+ `XMLHttpRequest`와 `Fetch` API는 `SOP`정책에 따라 동일한 출처에서 리소스를 요청 가능
* 웹 어플리케이션에서 다른 도메인을 가진 API 서버에 요청하는 경우가 많아지면서(cross-origin request) 안전하게 처리할 정책이 필요해지면서 CORS이 나옴
* CORS는 cross-origin 요청을 제한적으로 허용함으로서 더 안전하게 cross-origin 요청을 처리할 수 있는 정책

## CORS Request 종류
* CORS 요청을 보낼 때, `Simple`/`Preflight`와 `Credential`/`Non-Credential` 조합으로 4가지가 존재
	+ `Simple Request`
	+ `Preflight Reqeust`
	+ `Credential`
	+ `Non-Credential`
* 브라우저가 요청 내용을 분석하여 4가지 방식 중 해당되는 방식으로 서버에 요청

### Simple Request
Simple Request는 일반 요청과 동일하게 동작한다.
+ `GET`, `POST`, `HEAD` 중 한가지 방식을 사용
+ [Cors Safelisted request header](https://fetch.spec.whatwg.org/#cors-safelisted-request-header) 환경
+ `POST`요청의 경우 `Content-Type`이 셋 중 하나여야 한다.
	- `application/x-www-form-urlencoded`
	- `multipart/form-data`
	- `text/plain`
+ `XMLHttpRequestUpload` 객체에 이벤트 리스너가 등록되지 않은 경우
+ 요청에서 `ReadableStream` 객체를 사용하지 않은 경우
+ **`Access-Control-Allow-Origin` 값에 따라 브라우저가 응답을 정상적으로 처리할지 결정**


> `http://localhost:8080` -> request `http://localhost:9090/api`
```ruby
GET /api/menus HTTP/1.1

Host: localhost:9000
Referer: http://localhost:8080/
Origin: http://localhost:8080
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
```

```ruby
HTTP/1.1 200 OK

Access-Control-Allow-Origin: http://localhost:8080
Content-Type: application/json; charset=utf-8
Content-Length: 155
...
```
+ `Access-Control-Allow-Origin` 응답 헤더가 `*` 또는 `Origin`가 동일해야 정상 응답을 받을 수 있다.

### Preflight Request
Simple Request 조건에 해당하지 않는다면 브라우저는 Preflight Request 요청을 한다.
* GET, HEAD, POST 외의 다른 방식으로도 요청 가능
* application/xml 처럼 다른 Content-type으로 요청 가능
* 커스텀 헤더도 사용할 수 있다.
* `Preflight Request`의 특징은 예비 요청과 본 요청으로 나누어 전송
	1. 먼저 브라우저가 서버에 예비 요청(Preflight Request)를 보내고 -> 서버가 예비 요청 응답 (OPTION Method 요청)
	2. 그 다음 본 요청(Actual Request)를 보내고 -> 서버가 본 요청에 응답 (GET, POST, HEAD, PUT, DELETE 등으로 오는 본 요청)

```ruby
OPTIONS /resources/post-here/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,\*/\*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,\*;q=0.7
Connection: keep-alive
Origin: http://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER


HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER
Access-Control-Max-Age: 1728000
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 0
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain

POST /resources/post-here/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,\*/\*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,\*;q=0.7
Connection: keep-alive
X-PINGOTHER: pingpong
Content-Type: text/xml; charset=UTF-8
Referer: http://foo.example/examples/preflightInvocation.html
Content-Length: 55
Origin: http://foo.example
Pragma: no-cache
Cache-Control: no-cache

<?xml version="1.0"?><person><name>Arun</name></person>


HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:40 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://foo.example
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 235
Keep-Alive: timeout=2, max=99
Connection: Keep-Alive
Content-Type: text/plain
```

### Request with Credential
Http Cookie와 HTTP Authentication 정보를 인식할 수 있게 해주는 요청

* simple Credential Request

```javascript
var invocation = new XMLHttpRequest();
var url = 'http://bar.other/resources/credentialed-content/';

function callOtherDomain(){

  if(invocation) {
    invocation.open("GET", url, true);
    invocation.withCredentials = true;
    invocation.onreadystatechange = handler;
    invocation.send();
  }
}
```

* 요청 시 `xhr.withCredentials` = true 를 지정해서 Credential 요청을 보낸다.
* 서버는 **반드시 `Response Header`에 `Access-Control-Allow-Credentials: ture`를 포함해야 한다
	- `Access-Control-Allow-Credentials: ture` 설정 시
	- `Access-Control-Allow-Origin: *` 와일드 카드 설정은 불가능하며, 구체적인 Origin을 설정해야 한다.

### Non-Credential
CORS 요청은 기본적으로 Non-Credential 요청으로, Credential 관련 설정을 하지 않으면, Non-Credential 요청이다.

# CORS 관련 HTTP Response

## Access-Control-Allow-Origin
`Origin`으로 지정된 도메인으로부터의 요청만 서버의 리소스에 접근 가능 설정
* `*` 지정하면, 모든 도메인으로부터 서버 접근 허용

```ruby
Access-Control-Allow-Origin: <Origin> | *
```

## Access-Control-Expose-Headers
기본적으로 브라우저에게 노출이 되지 않지만, 브라우저 측에 접근할 수 있게 허용해주는 헤더

* 기본적으로 브라우저에 노출되는 HTTP Response Header는 6가지
  + Cache-Control
  + Content-Language
  + Content-Type
  + Expires
  + Last-Modified
  + Pragma

## Access-Control-Max-Age
Preflight Request의 결과를 캐쉬에 저장하는 시간(초) 설정

```ruby
Access-Control-Max-Age: <delta-seconds>
```

## Access-Control-Allow-Credentials
Request with Credential 방식이 사용될 수 있는지를 지정

```ruby
Access-Control-Allow-Credentials: true | false
```

* 서버에 Credential 요청이 들어왔을 때, `Access-Control-Allow-Credentials: true` 설정이 되 있지 않으면 브라우저에 의해 무시된다.
* **`Access-Control-Allow-Credentials: true` 설정을 하면, `Access-Control-Allow-Origin: *` 설정을 할 수 없다. -> 반드시 `Origin`을 명시해야 한다.**

## Access-Control-Allow-Methods
서버의 리소스에 접근할 수 있는 HTTP Method 방식을 지정

```ruby
Access-Control-Allow-Methods: <method>[, <method>] | *
```

## Access-Contorl-Allow-Headers
예비 요청에 대한 Response Header에 사용되며, 본 요청에서 사용할 수 있는 HTTP Header를 지정

```ruby
Access-Controll-Allow-Headers: <field-name>[, <field-name] | *
```



## Handling CORS on the server

```java
public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws IOException, ServletException {

HttpServletRequest request = (HttpServletRequest) req;
HttpServletResponse response = (HttpServletResponse) res;
response.setHeader("Access-Control-Allow-Origin", request.getHeader("Origin"));
response.setHeader("Access-Control-Allow-Credentials", "true");
response.setHeader("Access-Control-Allow-Methods", "POST, GET, OPTIONS, DELETE");
response.setHeader("Access-Control-Max-Age", "3600");
response.setHeader("Access-Control-Allow-Headers", "Content-Type, Accept, X-Requested-With, remember-me");
chain.doFilter(req, res);
}
```


# 출처
* [교차 출처 리소스](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)
* [Credentials 설정](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Access-Control-Allow-Credentials)
* [Fetch: Cross Origin Request](https://javascript.info/fetch-crossorigin)
