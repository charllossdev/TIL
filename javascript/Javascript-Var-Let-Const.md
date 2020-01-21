# var-let-const
Javascript에 변수 선언 방식인 `var` `let` `const`에 각각 차이점을 알아보자

Javascript의 변수 선언과, 이들의 차이점을 이해하려면
**Hoisting** 과 **Scope** 의 개녕이 필요하다.
  * [Javascript Hoisting](./Javascript-Hoisting.md)
  * [Javascript Scope](./Javascript-Closer-Scope.md)


## var-let-const 차이점
Javascript의 변수 정의의 비교 키워드는 3가지

 1. 변수 값의 변환
 2. 변수의 유효범위
 3. 호이스팅


# 1. 변수 값의 변환

기존의 Javascript를 사용하면서 가잔ㅇ 문제가 있다고 느낀점은 변수 선언 방식이다.

`var`를 사용하는 변수 선언의 경우 할당되는 값이 유동적으로 변경될 수 있는 단점을 가지고 있다.

```Javascript
var name = "Marcus";
console.log(name);

var name = "Jogeonsang";
console.log(name);

------------------------
output: Marcus
output: Jogeonsang
```

> 다음과 같이 name이라는 변수를 2번 선언했는데도 에러가 나오지않고 각기 다른 값이 출력되는걸 볼 수 있다.

하지만 ES6 업데이트 이후로 추가된 변수 선언 방식인 let과 const는 var와 같은 선언 방식을 막고있다.

```Javascript
let name = "Marcus";
console.log(name);

let name = "Jogeonsang";
console.log(name);
output: Identifier 'name' has already been declared
```

> 위와 같이 let을 사용했을 경우에는 name이 이미 선언되었다는 에러 메시지가 나오는걸 볼 수 있다.
> 위에 코드에는 let만 케이스로 집어넣었지만 const도 마찬가지로 변수 재할당이 안된다는 특징을 가지고있다.

---

그럴다면 `let`과 `const`는 어떤 차이가 있을까?

`let`과 `const` 차이점은 `immutable` 여부이다.

 `let`은 변수에 재할당이 가능하지만,

 `const`는 변수는 재선언, 재할당이 모두 불가능하다.


 `let`

```Javascript
// let
let testCase = 'let' // output: let
let testCase = 'let2' // output: Uncaught SyntaxError: Identifier 'testCase' has already been declared
testCase = 'let3' // output: let3
```

`const`

```Javascript
const testCase = 'const' // output: const
const testCase = 'const2' // output: Uncaught SyntaxError: Identifier 'testCase' has already been declared
testCase = 'const3' // output: Uncaught TypeError:Assignment to constant variable.
```

> 위에 코드에서 ReferenceError가 발생한 이유는 tdz(temporal dead zone)때문이다.

### temporal dead zone
let은 값을 할당하기전에 변수가 선언 되어있어야 하는데 그렇지 않기 때문에 에러가 난다.

이건 const도 마찬가지인데 좀 더 엄격하다.

```javascript
// let은 선언하고 나중에 값을 할당이 가능하지만
let dd
dd = 'test'

// const 선언과 동시에 값을 할당 해야한다.
const aa // Missing initializer in const declaration
```

> 이렇게 javascript에 `tdz`가 필요한 이유는 동적언어이다 보니깐 runtime type check 가 필요해서이다.

# 2. 변수의 유효범위
Javascript에서 변수들의 스코프(유효범위) 에 대해서, `var`는 함수 스코프(Function Scope)를 가지고, `let`, `const`는 블럭 스코프(Block Scope)를 가지게 된다.

`var`

```javascript
var foo = "This is String.";
if(typeof foo === 'string'){
    var result = true;
} else {
  var result = false;
}

console.log(result);    // result : true
```

`let`, `const`
```Javascript
var foo = "This is String.";
if(typeof foo === 'string'){
    const result = true;
} else {
  const result = false;
}

console.log(result);    // result : result is not defined
```
