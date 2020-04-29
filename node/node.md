
![](assets/node-7a0b8179.png)

[Node.js Documentation](https://nodejs.org/dist/latest-v8.x/docs/api/synopsis.html)

확장성 있는 네트워크 애플리케이션 개발에 사용되는 소프트웨어 플랫폼으로, 자바스크립트를 활용해서 Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능을 가지고 있다.

내장 HTTP 서버 라이브러리를 포함하고 있어, 웹 서버에서 아파치 등으 ㅣ별도의 소프트웨어 없이 동작하는 것이 가능하며, 이를 통해 웹 서버의 동작에 있어 많은 통제를 가능하게 해 주는 특징이 있다.

V8(자바스크립트 엔진)으로 빌드 된 이벤트 기반 자바스크립트 런타임이다. 웹 서버와 같이 확장성 있는 네트워크 프로그램 제작을 위해 고안되었다.
파이썬으로 만든 트위스티드, 펄로 만든 펄 객체 환경, 루비로 만든 이벤트머신과 그 용도가 비슷하다. 대부분의 자바스크립트가 웹 브라우저에서 실행되는 것과는 달리, 서버 측에서 실행된다. 일부 CommonJS 명세[3]를 구현하고 있으며, 쌍방향 테스트를 위해 REPL 환경을 포함하고 있다.

# Node.js

* 브라우저 밖에서 자바스크립트 코드를 실행 할 수 있다.
* 크롬에서 사용하는 V8 엔진을 사용한다
* 이벤트 기반의 비동기 I/O 프레임워크
* CommonJS를 구현한 모듈 시스템
  + 기본 모듈
  + 사용자 모듈
  + 서드파티 라이브러리 모듈


![](assets/node-2f6d9349.png)

성능을 높히려면 여러개의 서비스를 병렬적으로 사용하는 방법으로 단일 스레드로 무거운 잡을 워커에게 전달하고, 워커는 멀티 스레드로 워커가 무거운 잡을 끝내면, 이벤트 루프에 리턴하여 클라이언드에게 전송한다.

한 사이클에 다 못하는 인풋 아웃풋 잡

인풋(사용자 입력, 마우스 클릭, 키보드 입력)
아웃풋잡(DB조회, 서버통신)

워커에게 일을 할당하여 비동기적으로 서비스를 처리한다.


## Module

* 기본 모듈
```js
const util = require('util')

const name = 'World'
const msg = uilt.format('Hello %s', name)

console.log(msg);
```

* 사용자 모듈
```js
//math.js
const math = {
  add(a,b) {
    return a + b
  }
}
module.exports = math //이 한줄로 math.js가 모듈이 된다.

// index.js
const math = require('./math') // 모듈을 사용하기 위해서 경로 입력, .js는 생략
console.log(math.add(1,2)) // print '3'
```
* 서드파티 라이브러리 모듈

# 비동기
노드는 기본적으로 비동기로 동작함
readFIle() vs readFileSync()

```js
// test.txt
테스트 파일입니다.

// index.js
const fs = require('fs')

// callback method
const callback = (err, file) => {
  console.log(file)
}

// 동기 처리 // 파일을 다 읽을 때 까지 wait한다.
const file = fs.readFileSync('test.txt'. {encoding: 'uft8'}), (err, data) => console.log(file)) // 테스트 파일입니다.

// 비동기 처리 // 파일을 다 읽으면 콜백 이벤트 루프 함수가 호출된다.
const file = fs.readFile('test.txt', {encodig: 'utf'}, callback), (err, data) => console.log(file)  // undefind
```

# Node.js Create Server

```js
const http      = require('http');

const hostname  = '127.0.0.1';
const port      = 3000;

const server    = http.createServer((req, res) => {
    //console.log('login');
    console.log(req.url);

    if (req.url === '/') {
        res.statusCode = 200;
        res.setHeader ('Content-type', 'text/plain');
        res.end('Hello Client');
    }
    else if (req.url === '/users') {
        const users = [
            {name: 'Alice'},
            {name: 'Back'},
        ]
        res.statusCode = 200;
        res.setHeader ('Content-type', 'application/json');
        res.end(JSON.stringify(users));
    }


});

server.listen(port, hostname, ()=> {
    console.log(`Server running at http://${hostname}:${port}/`);
});                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
```

### Request server

```cmd
curl localhost:3000
```

```return
Hellow World
```

## curl을 통해 Server의 정보 얻기

```bash
curl localhost:3000/users
```
return
* $>$: http request에 관련 정보 리턴
* $<$: http response에 관련 정보 리턴


http request에 관련된 정보
```bash
> GET /users HTTP/1.1
> Host: localhost:3000
> User-Agent: curl/7.55.1
> Accept: */*
```

http response에 관련된 정보
```bash
< HTTP/1.1 200 OK
< Content-type: application/json
< Date: Tue, 21 Apr 2020 01:55:06 GMT
< Connection: keep-alive
< Content-Length: 34
[{"name":"Alice"},{"name":"Back"}]
```
# REST API

### HTTP 요청
* 모든 자원은 명사로 식별한다.
* HTTP 경로로 자원을 요청한다.
  + $e.i$: $GET$ $/user/${id}

### HTTP 요청 메서드를
* GET
* POST
* PUT
* DELETE

# TDD 테스트 주도 개발 방법론

### Mocah
* 모카(Mocha): 테스트 코드를 돌려주는 테스트 러너
* 테스트 꾸러미: 테스트 환경응로 모카에서는 describe()으로 구현한다.
* 테스트 케이스: 실제 테스트를 말하며, 모카에서는 it()으로 구현한다.

### should
* 슈드: 검증(assertion), 벨리데이션 라이브러리.
* 가독성 높은 테스트 코드를 만들 수 있다.

### SuperTest
API를 테스트 할 수 있는 라이브러리
Node.js의 API를 테스트 자동화 할 수 있는 라이브러리

* 단위 테스트
* 통합 테스트

```
npm i mocha --save-dev
npm i shoild --save-dev
npm i supertest --save-dev
```

> package.JSON

```json
{
  "name": "node-api-server",
  "version": "1.0.0",
  "description": "node test server api",
  "main": "index.js",
  "dependencies": {
    "express": "^4.17.1",
    "morgan": "^1.10.0"
  },
  "devDependencies": {
    "mocha": "^7.1.1",
    "should": "^13.2.3",
    "supertest": "^4.0.2"
  },
  "scripts": {
    "start": "node ./index.js",
    "test": "mocha ./index.spec.js"
  },
  "author": "charllossDev",
  "license": "MIT"
}
```

> index.spec.js

```js
// node 기본 몯듈
const assert  = require('assert');
const should  = require('should');
const request = require('supertest');
const app     = require('./index'); // module export 한 객체를 가져오기

// mocha 내장 함수 // 테스트 하려는 API
describe('GET /users', () => {

    // mocha 내장 it 함수 // param2: 검증 작업 이벤트 함수
    it('Return Array', () => {

        // 2개의 인자가 같으면 true, 다르면 에러를 리턴한다.
        //assert.equal(1, 2);

        // should // 위에 assert와 동일한 메서드
        // (1).should.equal(1);
        request(app)
            .get('/users')
            ,end((err, res) => {
                console.log(res.body);  // 비동기로 서버가 실행되서 테스트

                //  응답 값이 배열인지 확인
                res.boyd.should.be.instanceof(Array);
                res.boyd.forEach(user => {

                    // 배열의 속성 중에 name이 있는지 확인
                    user.should.have.property('name');
                });
                done();
            })
    })
})
```

# API Server

* 성공
  + 유저 객체를 담은 배열로 응답한다.
  + 최대 limit 갯수만큼 응답한다.
* 실패
  - limit이 숫자형이 아니면 400을 응답한다.
  - offset이 숫자형이 아니면 400을 응답한다.

데이터를 전달하는 3가지 방법
* url 경로
* 쿼리스트링
* Body에 Json을 통해 전달
