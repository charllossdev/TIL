
# Immediately Invoke Function Expression

* Immediately Invoke function:
    자바스크립트에서 가장 큰 문제점 중의 하나는 글로벌 스코프에 정의된 것은 코드 내의 어디서든지 접근이 가능하다. (속도저하)

    일반적인 함수 표현(Function expression)은 함수를 정의하고, 변수에 함수를 저장하여 실행하는 과정을 거친다.
    하지만 즉시실행함수(Immediately Invoke Function Expression)은 함수를 정의하고 바로 실행하여 위와 같은 과정을 거치지 않는 특징이 있다. 즉 함수를 정의하자마자 바로 호출하는 것을 즉시 실행 함수라고 한다.

    즉시 실행 함수는 한 번의 실행만 필요로 하는 초기화 코드로 많이 사용된다.'
    그렇다면 왜 초기화 코드 부분에 많이 사용할까?, 변수를 전역(global scope)으로 선언하는 것을 피하기 위해서 이다. 전역 변수를 추가히자 않아도 되기 때문에 코드 충돌 없이 안전하게 구현할 수 있기 때문에 플러그인이나 라이브러리 등을 만들때 주로 사용한다.

* Args:
    첫 로드 시 초기화 할 때 변수를 global하게 선언하고 싶지 않을 때
    변수에 함수를 이용해 즉시 값을 할당하고 싶을 때
    라이브러리 전역 변수 충돌 방지

* Return:
    즉 변수에 즉시실행함수 리턴값 저장

* Example:
    + Default Example
    ```javascript
        (function () {
            // statements
        })()
    ```

    + 기명 즉시 실행 함수
    ```javascript
        // 이 두가지 예는 괄호의 위치가 조금 다를 뿐 같은 기능을 한다.
        (function square(x) {
            console.log(x*x);
        })(2);

        (function square(x) {
            console.log(x*x);
        }(2));
    ```

    + 익명 즉시 실행 함수
    ```javascript
        (function (x) {
            console.log(x*x);
        })(2);

        (function (x) {
            console.log(x*x);
        }(2));
    ```

    + 변수에 즉시 실행 함수 저장
    ```javascript
        // 즉시 실행 함수도 함수이기 때문에, 변수에 즉시 실행 함수 저장이 가능하다.
        (mySquare = function (x) {
            console.log(x*x);
        })(2);
        mySquare(3);

        //result
        // 4    // 최초 즉시 실행 결과
        // 9    // mySquare(3); 결과
    ```

    + 리턴문이 있는 즉시 실행 함수
    ```javascript
    var mySquare = (function (x) {
        return x*x;
    })(2);
    console.log(mySquare)

    // result 4;
    // 즉 변수에 즉시실행함수 리턴값 저장
    ```
    + 캡슐화 즉시 실행 함수:
    즉시 실행 함수 내에서 선언한 변수를 외부에서도 접근이 가능하다.
    변수의 접근 범위가 함수 내부가 아닌 외부에서도 가능해진다.
    즉시 실행함수는 변수의 스코프를 포함하는데 사용되며, 외부에서 함수 내의 변수에 접근할 경우 이를 통제할 수 있다.
    즉시 실행 함수는 글로벌 네임스페이스에 변수를 추가하지 않아도 되기 때문에 코드 충돌 없이 구현할 수 있어 플러그인이나 라이브러리 등을 만들 때 많이 사용한다.
    ````javascript
    var app = (function() {
        var privateVar = 'private';
        return {
            prop : privateVar
        };
    }());
    console.log(app.prop); // "private" 출력
    ```
