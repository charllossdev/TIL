# Interview

* [Development common sense](#development-common-sense)


# Development common sense

## Object Oriented Programming

객체 지향 프로그래밍 이전의 프로그래밍 패러다임을 살펴보면, 컴퓨터가 중심으로 있었다. 컴푸터가 사고하는대로 프로그래밍을 하는 것이다.
하지만 객체지향 프로그래밍이란 인간 중심적 프로그래밍 패러다임이라고 할 수 있다. 즉 현실 세계를 프로그래밍ㅇ으로 옮겨와 프로그래밍하는 것을 말한다.
현실 세계의 사물들을 객체라고 보고, 그 객체로부터 개발하고자 하는 애플리케이션에 필요한 특징들을 뽑아와  프로그래밍 하는 것이다. 이것을 **추상화**라 한다.

`OOP`로 코드를 작성하면 이미 작성한 코드에 대한 재사용성이 아주 높다. 자주 사용되는 로직을 라이브러리로 만들어두면 계속해서 사용할 수 있으며, 그 신뢰성을 확보할 수 있다.
또한 라이브러리를 각종 예외상황에 맞게 잘 만들어두면, 개발자가 사소한 실수를 하더라도 그 에러를 컴파일 단계에서 잡아낼 수 있으므로 버그 발생이 줄어든다.
또한 내부적으로 어떻게 동작하는지 몰라도, 개발자는 라이브러리가 제공하는 기능들을 사용할 수 있기 때문에 생산성이 높아지게 된다.
객체 단위로 코드가 나눠져 작성되기 때문에 디버깅이 쉽고 유지보수에 용이하다. 또한 데이터 모델링을 할 때 객체와 매핑하는 것이 수월하기  때문에 요구사항을 보다 명확하게 파악하여 프로그래밍 할 수 있다.

객체 간의 정보 교환이 모두 메세지 교환을 통해 일어나므로, 실행 시스템에 많은 `overhead` 가 발생하게 된다. 하지만 이것은 하드웨어의 발전으로 많은 부분 보완되었다.
객체 지향 프로그래밍의 치명적인 단점은 함수형 프로그래밍 패러다임의 등장 배경을 통해서 알 수 있다. **바로 객체가 상태를 갖는다는 것이다.**
변수가 존재하고, 이 변수를 통해 객체가 예측할 수 없는 상태를 갖게 되어 애플리케이션 내부에서 버그를 발생시킨다는 것이다. 이러한 이유로 함수형 패러다임이 다시 주목받고 있다.

### 객체 지향적 설계 원칙

1. SRP(Single Responsibility Principle): 단일 책임 원칙- 클래스는 단 하나의 책임을 가져야하며, 클래스를 변경하는 이유는 단 하나의 이유여야 한다.
2. OCP(Open-Closed Principle): 개방-폐쇄 원착- 확장에는 열려 있어야 하고, 변경에는 닫혀 있어야 한다.
3. LSP(Liskov Substitution Principle): 리스코프 치환 원칙- 상위 타입의 객체를 하위 타입의 객체로 치환해도, 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.
4. ISP(Interface Segregation Principle): 인터페이스 분리 원칙- 인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리해야 한다.
5. DIP(Dependency Inversion Principle): 의존 역전 원칙- 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다.

---

# Network

## HTTP

* `GET`
  + get 방식은 요청하는 데이터가 `HTTP Request Message`의 `Header` 부분에 url이 담겨서 전송
  + 그렇기 떄문에, `url`상의 `?`뒤에 데이터가 붙어 `request`를 보내게 된다.
  + 이러한 방식은 `url`이라는 공간에 담겨가기 때문에, 전송할 수 있는 데이터의 크기가 제한적
  + 또한 보안이 필요한 데이터에 대해서는 데이터가 `url`에 그대로 노출되기 때문에 이러한 경우 `GET`방식은 적절하지 않음
  + 즉 `GET`방식은 주로 서버에서 어떤 데이터를 가져오는 상황에 주로 사용되며, **서버의 값이나 상태 등을 변경하지 않는다.**
  + 또한 `GET` 방식의 요청은 브라우저에서 `Caching`gkf tn dlTek.

* `POST`
  + post 방식은 요청하는 데이터가 `HTTP Request Message`의 `Body` 부분에 데이터가 담겨서 전송
  + 그렇기 떄문에, 바이너리 데이터를 요청하는 경우 `POST` 방식으로 보내야 한다.
  + 데이터 크기에 대해 자유롭고, `GET` 방식보다 보안성이 좋다(하지만 보안적인 측면에서 중요 데이터는 암호화)
  + 즉 `POST`방식은 주로 서버에 값이나 상태를 변경하기 위해서 또는 추가하기 위해서 사용


# RESTful API

* `REST`란, REpresentational State Transfer 의 약자
* 여기러 `~ful` 이라는 형용사형 어미를 붙여 ~한 API 라는 표현으로 사용
* 즉 REST의 기본 원칙을 성실히 지킨 서비스 디자인은 `RESTful` 하다고 표현
* `REST`가 디자인 패턴으로, 아키텍쳐다.
  + 좀더 정확하게 표현하면, `REST`는 `Resource Oriented Architecture`로, API 설계 중심에 자원(Resource)이 있고, `HTTP Method`를 통해 자원을 처리하도록 설계

## RESTful API 설계

1. 리소스와 행위를 명시적으로 직관적으로 분리
  + 리소스는 `URI`로 표현되는데, 리소스가 가리키는 것은 `명사`로 표현
  + 행위는  `HTTP Method`로 표현하고, `GET(조회)`, `POST(생성)`, `PUT(entity 전체 수정)`,`PATCH(entity 일부 수정)`, `DELETE`를 분명한 목적으로 사용
2. `Message`는 `Header`와 `Body`를 명확하게 분리해서 사용
  + Entity에 대한 내용은 `Body`에 담는다.
  + 애플리케이션 서버가 행동할 판단의 근거가 되는 컨트롤 정보인 API버전 정보, 응답받고자 하는 MIME 타입 등은 `Header`에 담는다.
  + header 와 body 는 http header 와 http body 로 나눌 수도 있고, http body 에 들어가는 json 구조로 분리할 수도 있다.
3. API 버전을 관리
  + 환경은 항상 변하기 때문에 API의 signature가 변경될 수도 있음을 유의
  + 특정 API를 변경할 때는 반드시 하위호환성을 보장
4. 서버와 클라이언트가 같은 방식을 사용해서 요청
  + 브라우저 또는 모바일 환경 등 다양한 클라이언트 환경을 고려해, 서버와 클라이언트 간의 데이터 교환 타입을 json, form-data 등 같이 한가지 방식으로 통일
  + `URI`가 플랫폼 중립적으로 구성

## 장점
* Open API를 제공하기 쉽다.
* 멀티플랫폼 지원 및 연동이 쉽고 용이
* 원하는 타입으로 데이터를 교환
* 기존 웹 인프라를 그대로 사용 가능

---

# Data Structure



---

# 후기

## 네이버 z
> 2021.04.23

* HTTP Status: 304
* Java 쓰레드 덤프와 힙덤프
  - https://d2.naver.com/helloworld/10963
  - https://bestugi.tistory.com/38
  - http://honeymon.io/tech/2019/05/30/java-memory-leak-analysis.html
  - https://jupiny.com/2019/07/15/java-heap-dump-analysis/
* 우테캠 상세 후기
  - 개발에 대한 정리 필요
  - 앞으로의 발전

## 블랙홀릭
> 2021.04.26

* Srping Interceptor & filter
* Java String, StringBuffer, StringBuilder 차이 및 장단점
  - https://ifuwanna.tistory.com/221
  - 연산횟수가 많아지거나 멀티쓰레드, Race condition 등의 상황이 자주 발생 한다면 각 클래스의 특징을 이해하고 상황에 맞는 적절한 클래스를 사용
  - String:  문자열 연산이 적고 멀티쓰레드 환경일 경우
  - StringBuffer:  문자열 연산이 많고 멀티쓰레드 환경일 경우
  - StringBuilder:  문자열 연산이 많고 단일쓰레드이거나 동기화를 고려하지 않아도 되는 경우

## Next-Step 멘토링
> 2021.04.27

* Java Anotation vs Spring Anotation
* Spring Singleton
* OOP 개발 방법론 5가지
---
숙제
* 기술에 대한 본질적인 원리
* 기술의 사용 이유 또는 장단점 파악
* 상세하게 설명할 수 있는 스킬
  - 아무것도 모르는 상대에게 알려줄 수 있을 정도의 지식 필요
  - 모든 기술은 본질적으로 공식 홈페이지를 참조하기(한글x)
* 진지한 목표와 방향성 그리기
  - 향후 1년 뒤, 3년 뒤, 5년 뒤 방향성에 대해서 고민
* 진지한 목표 가지기
* 정리하는 슨관 필요
* 환경 파악 및 devops
