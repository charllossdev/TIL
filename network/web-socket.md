
# WebSocket

실시간 양방향 통신을 위한 WebSocket 기술을 흡족하게 사용하면서 2가지 문제를 직면했습니다.
1. WebSocket 미지원 웹 브라우저: 과거 브라우저를 많이 사용하는 보험 환경 이슈(구 익스플로러)-> Socket.io, sockJS
2. 웹 브라우져가 아닌 클라이언트 -> STOMP

## 정의
* 표준 WebSocket의 API는 W3C에서 관장하고, 프로토콜은 IETF에서 관장
* WebSocket은 HTTP(S)를 사용하여 연결요청, UTF-8 및 이진 메시지를 모두 지원하는 웹을 통해 클라이언트와 서버 간의 빠르고 안전한 양방향 통신을 위한 메커니즘
  - HTTP 통신으로 80 or 443포트로 통신
  - 과정을 handshake라고 하며, http를 Websocket 프로토콜로 바꾸는 Protocol switching
  - 단일 소켓 연결으로, 실시간으로 두 엔드포인트에서 데이터를 주고 받을 수 있음
  - 서버와 클라이언트의 양방향 통신이 가능
  - 상태를 유지하는 프롤토콜(Stateful protocol)으로 서버와 클라이언트 간에 Socket Connection을 유지해 언제든 통신 및 데이터 전송 가능

## 오버헤드 비교
폴링(Polling) 방식:
요청/응답 헤더 데이터 용량: (871 Byte)

1. 1000명 *  헤더 데이터 용량  = 871,000  Byte
2. 10000명 *  헤더 데이터 용량  = 8,710,000  Byte
3. 100000명 *  헤더 데이터 용량  = 87,100,000 Byte

WebSocket 방식:
메시지 데이터 용량: (2 Byte)
1. 1000명 *   메시지 데이터 용량   = 2,000  Byte
2. 10000명 *   메시지 데이터 용량   = 20,000  Byte
3. 100000명 *   메시지 데이터 용량   = 200,000 Byte

출처: https://mohwaproject.tistory.com/entry/ㅁㅁㅁ


## 연결 설정
서버와 클라이언트 간의 WebSocket 연결은 HTTP 기반 핸드쉐이크가 필요
* 클라이언트 요청
  ```http
  GET /chat HTTP/1.1
  Host: server.example.com
  Upgrade: websocket
  Connection: Upgrade
  Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
  Sec-WebSocket-Protocol: chat, superchat
  Sec-WebSocket-Version: 13
  Origin: http://example.com
  ```
  - 요청 시 HTTP 헤더에 Upgrade 속성과, WebSocket 보안 키를 전송
* 서버 응답
  ```http
  HTTP/1.1 101 Switching Protocols
  Upgrade: websocket
  Connection: Upgrade
  Sec-WebSocket-Accept: HSmrc0sMlYUkAGmm5OPpG2HaGWk=
  Sec-WebSocket-Protocol: chat
  ```
  - Switching Protocols 상태인 101과 요성한 WebSocket 보안 키를 응답
  - 통신이 서로 성공하면 애플리케이션 계층 프로토콜이 이전에 설정된 TCP 연결을 사용하여 HTTP에서 WebSocket으로 **업그레이드**

---

> 주로 실시간이 요구되는 Real-time web application구현을 위해 사용하는 기술로서 실시간이 요구되는 프로덕션 환경에 주로 적용하여 구현했습니다.
> - 타사와 제휴한 자동차 및 중고차 시승보험 영업 서비스
> - 인천공항 주차장비 및 키오스크 장비 실시간 장애 체크 및 장비제어
>
> 코로나 이슈로 비대면 영업이 활성화 되면서, 실시간으로 전화 영업으로 인한 자동차 보험 가입 상태를 파악해 자동차 딜러에게 안내해 주는 서비스와 인천공항의 모든 주 장비의 상태를 실시간으로 확인이 가능하며, 장애 발생시 즉각 대응 알림 및 주차장비를 관제 및 제어하는 양방향 서비스를 개발하였습니다.
> 실시간이 필요한 서비스에는 WebSocket을 이용하여 응용 어플리케이션을 개발하는데 큰 도움이 된다고 생각합니다.

# Socket.io
## 정의
* node.js 기반으로 만들어진 기술 스팩
* Socket.io는 JavaScript를 이용하여 실시간 웹을 구현할 수 있도록 한 기술
* WebSocket, FlashSocket, AJAX, IFrame, JSONP Polling등 다양한 통신을 하나의 API로 추상화
  - 즉 브라우저 종류에 상관없이 실시간 웹 서비스를 구현 가능
  - 개발자가 각 기술을 깊이 이해하지 못하거나 구현 방법을 잘 알지 못해도 사용

---

> WebSocket 미지원 웹 브라우져에서 실시간 서비스를 위해 이 기술을 사용했습니다.
> - 구버전 익스플로러 환경에서 자동차 보험 서비스 환경
>
> 타사의 자동차 보험 서비스 서버와 인터페이스 하는 Node.js 기반으로 Express socket.io 중계서버를 만들고, 구 버전 익스플로러 환경일 경우 socket.io 클라이언트 객체를 통해 서버와 연결 세션을 가지는 환경을 개발 했습니다.
> Socket.io기술을 이용해 WebSocket이 지원되지 않는 환경에서도 이벤트 기반으로 실시간 서비스를 개발 가능합니다.


# STOMP
## 정의
* Simple (or Streaming) Text Oriented Message Protocol 의 약자인 STOMP는 텍스트 기반의 메세징 프로토콜
* STOMP 사용 환경은 TCP 나 WebSocket 과 같은 신뢰성있는 양방향 streaming network protocol 상에 사용
* HTTP에 모델링된 frame 기반 프로토콜
* STOMP는 구독이라는 개념을 통해 내가 통신하고자 하는 topic을 판단하여, 브로커라는 개념으로 실시간, 지속적으로 관심을 가지며 요청을 처리

> 실시간으로 주차 장비를 관제하는 WebSocket 서버로, 주차 장비 및 다양한 클라이언트들과 통신할 수 있는 서버를 구성하는 것이 목표였습니다.
클라이언트 구성은 .Net 기반 주차장비와, JavaFx 키오스크, 모바일(Android, iOS)과 웹 브라우저 입니다.
이 프로젝트에서 이슈는 2가지를 해결해야 했습니다.
>  1. WebSocket을 지원하지 않는 브라우저
>  2. 웹 브라우저 이외의 클라이언트
>
> 이 2가지 문제를 해결하기 위해 Spring Framework 기반 STOMP + sockJS 구성 서버를 개발했습니다.
> 1. WebSocket을 지원하지 않는 브라우져에서는 sockJS를 이용해서 서버 실시간으로 통신
> 2. 웹 브라우저 이외의 클라이언트는 STOMP 규격으로 서버와 실시간 통신
>
> 이렇게 하나의 서버로 STOMP와 sockJS + STOMP 두개를 오픈하고 각각의 경로로 들어온 message에 대해서 동일한 소스로 처리하여, 모두 다른 클라이언트 환경에서 동일한 서비스를 제공하는 결과를 만들었습니다.
>
> 프로젝트를 진행하면서, 실시간 양방향 통신에 대한 이슈 관리와 유연한 서버 모듈을 개발하는 데 큰 도움이 됬습니다.


# sockJS
## 정의
* SockJS는 Socket.io와 유사한 라이브러리로 websocket을 지원하지 않는 브라우저를 위한 라이브러리
* springframework에서 WebSocket을 지원
  + 스프링 메뉴얼에는 WebSocket 브라우저 미지원 문제 해결을 위해 SockJS 사용을 추천하여 도입
  + 스프링 서버 개발시 설정을 통해 WebSocket 통신 또는 sockJS 호환으로 통신할지 결정 가능
  + 클라이언트는 sockJS Client를 통해 서버와 실시간 통신

> WebSocket 미지원 웹 브라우져에서 실시간 서비스를 위해 이 기술을 사용했습니다.
> Socket.io와 비슷한 라이브러리지만, Socket.io 라이브러리를 사용하기 위해서는 Node.js 기반  Socket.io 서버를 구현해야는 이슈가 있습니다.
>
> 하지만, 한개의 주차 관제 WebSocket 서버에서 모든 클라이언트를 관제하기 위해 SockJS를 사용했습니다.
> 현장 특성상 구버전 익스플로러를 많이 사용하는 환경으로, 브라우저 버전을 확인 후, WebSocket 미지원 브라우저일 경우, sockJS Clinet로 Spring 서버와 실시간 통신 기능을 개발했습니다.


# STOMP WebSocket 보안
실시간으로 주차 장비를 관제하는 STOMP 기반 WebSocket 서버의  WebSocket 보안 기능 개발

## 정의
* Spring Security를 통한 로그인 인증
  - 인증
  - 권한
* JWT(Json Web Token)을 이용한 WebSocket통신 보안 기능 강화
  - oauth2 기반 인증
> 1. Spring Security 설정을 통해 로그인 인증과 권한을 부여
>
> 로그인 이후에는 WebSocket기반 으로 통신을 하는데, 헤더에 토큰을 검사하는 HTTP 프로토콜과는 다르기 떄문에 이슈가 발생했습니다.
>
>> 최초 핸드쉐이킹 과정에서 HTTP -> WS Upgrade 과정에 HTTP 메세지에 인증 헤더를 추가하는 방안을 고려했지만, WebSocket 연결 후 별도 서비스의 권한 제어가 불가능 했습니다.
>
> 그리하여, WebSocket 연결 및 메세지 전송시에 JWT 토큰을 관리하여 통제하는 방안을 도입했습니다.
>
> STOMP 라이브러리를 이용한 WebSocket 통신 시 hearder에 Jwt를 설정하여 검증 된 Token 유무를 판단해, 검증된 클라이언트만 서비스 하도록 설정했습니다.
>>  StompHandler빈을 만들어 인터셉터에 설정함으로서, WebSocket을 통한 실시간 통신에서도 인증 서비스 제공
