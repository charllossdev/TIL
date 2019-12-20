
# vue
![](assets/0.vue-init-34259aaf.png)

Vue(/vjuː/ 로 발음, view 와 발음이 같습니다.)는 사용자 인터페이스를 만들기 위한 진보적인 프레임워크 입니다. 다른 단일형 프레임워크와 달리 Vue는 점진적으로 채택할 수 있도록 설계하였습니다. 핵심 라이브러리는 뷰 레이어만 초점을 맞추어 다른 라이브러리나 기존 프로젝트와의 통합이 매우 쉽습니다. 그리고 Vue는 현대적 도구 및 지원하는 라이브러리와 함께 사용한다면 정교한 단일 페이지 응용프로그램을 완벽하게 지원할 수 있습니다.


문자열 템플릿을 렌더링하는 것과 매우 유사하지만 사실 Vue는 더 많은 작업을 합니다. 데이터와 DOM이 연결되어 이제 모든 것이 반응형입니다.


Node.js®는 Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임입니다. Node.js는 이벤트 기반, Non 블로킹 I/O 모델을 사용해 가볍고 효율적입니다. Node.js의 패키지 생태계인 npm은 세계에서 가장 큰 오픈 소스 라이브러리 생태계이기도 합니다.


node.js는 JavaScript 기반으로 구성된 서버 사이드 서비스를 JavaScript로 구현할 수 있게 만든 런타임이다.

 npm은 node.js 기반의 모듈을 모아둔 집합 저장소이다.
 npm은 Node Package Manager 또는 Node Package Modules라고도 한다.


다음은 node.js로 할 수 있는 것들이다. 꼭 여기에 국한되지는 않지만 node.js가 가장 빛을 발하는 곳은 실시간 웹 애플리케이션이다. 이유는 About Node.js node.js 정보에 잘 나와 있다. 설명하자면 node.js는 lock이 없으므로 프로세스를 dead-locking 할 걱정이 없고 I/O를 직접 수행하지 않으므로 프로세스가 절대 차단되지 않기 때문이다. non Block이기에 확장 가능한 시스템은 노드에서 개발하는 것이 합리적이다

* 정적 파일 서버
* 웹 응용프로그램
* 메시징 미들웨어
* HTML5 멀티 플레이어 게임용 서버

npm은 훌륭한 개발자들이 Node.js 기반의 JavaScript로 개발된 오픈 소스를 모듈로 올려놓은 곳이다. 우리는 웹 개발에 필요한 jQuery, gulp, webpack 등의 모듈들을 npm명령어를 통해 쉽게 다운받고 쓸 수가 있다.

---
vue ajax 관련: https://m.blog.naver.com/PostView.nhn?blogId=spdlqjdudghl&logNo=221291924219&proxyReferer=https%3A%2F%2Fwww.google.com%2F



# Vue 설치 방법

1. CDN
https://unpkg.com/vue 주소를 script 태그에 직접 추가

2. Vue.js 파일다운
개발용, 배포용 버전을 다운 받아 script 태그에 추가
개발용 버전은 개발에 도움이 되는 모든 경고를 출력하기 때문에 개발 중에만 사용하고, 실제 서비스에서는 배포용 버전으로 사용해야 한다.

3. NPM 설치
규모가 큰 프로젝트 경우 컴포넌트별 독립적으로 관리할 수 있는 싱글 파일 컴포넌트 방식 추천



## Vue Cli

vue-cli
vue-cli를 사용하면 뷰 애플리케이션을 개발하기 위한 초기 프로젝트 구조를 쉽게 구성할 수 있습니다. 다만, 싱글 파일 컴포넌트 체계를 사용하려면 .vue 파일을 웹 브라우저가 인식할 수 있는 형태의 파일로 변환해 주는 웹팩(Webpack)이나 브라우저리파이(Browserify)와 같은 도구가 필요합니다.

**Vue Cli 2.0 버전과 3.0 버전 전부 셋팅해봐야 한다.**

Vue Cli 3.0 버전 관련 사이트
https://vuejs.kr/vue/vue-cli/2018/01/27/vue-cli-3/

## Vue Cli 설치 명령어 종류
* vue init webpack : 고급 웹팩 기능을 활용한 프로젝트 구성 방식. 테스팅，문법 검사 등을 지원
* vue init webpack-simple : 웹팩 최소 기능을 활용한 프로젝트 구성 방식. 빠른 화면 프로토타이핑용
* vue init browserify : 고급 브라우저리파이 기능을 활용한 프로젝트 구성 방식. 테스팅，문법 검사 등을 지원
* vue init browserify-simple : 브라우저리파이 최소 기능을 활용한 프로젝트 구성 방식. 빠른 화면 프로토타이핑용
* vue init simple : 최소 뷰 기능만 들어간 HTML 파일 1개 생성
* vue init pwa : 웹팩 기반의 프로그레시브 웹 앱(PWA, Progressive Web App) 기능을 지원하는 뷰 프로젝트


# npm 설치된 글로벌 패키지 확인

![](assets/Vue-Intro-b5a90e76.png)
