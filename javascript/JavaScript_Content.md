# JavaScript

## AJAX (Asynchronous JavaScript and XML)

Ajax 설정 속성
```JavaScript
$.ajax:
    Ajax(Asynchronous JavaScript And XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미

    서버로부터 웹페이지가 반환되면 화면 전체를 갱신해야 하는데 페이지 일부만을 갱신하고도 동일한 효과를 볼 수 있도록 하는 것이 Ajax이다.
    페이지 전체를 로드하여 렌더링할 필요가 없고 갱신이 필요한 일부만 로드하여 갱신하면 되므로 빠른 퍼포먼스와 부드러운 화면 표시 효과를 기대할 수 있다.

Args:
    클라이언트와 서버 간에는 데이터 교환이 필요하다. JSON(JavaScript Object Notation)은 클라이언트와 서버 간 데이터 교환을 위한 규칙 즉 데이터 포맷을 말한다.    
    JSON은 일반 텍스트 포맷보다 효과적인 데이터 구조화가 가능하며 XML 포맷보다 가볍고 사용하기 간편하며 가독성도 좋다.

    **키는 반드시 큰따옴표(작은따옴표 사용불가)로 둘러싸야 한다.**
    자바스크립트의 객체 리터럴과 매우 흡사하다. 하지만 JSON은 순수한 텍스트로 구성된 규칙이 있는 데이터 구조이다.

Return:
    서버에서 브라우저(클라이언트)로 전송된 JSON 데이터는 문자열이다.
    이 문자열을 객체로서 사용하려면 객체화하여야 하는데 이를 역직렬화(Deserializing)이라 한다. 역직렬화를 위해서 내장 객체 JSON의 static 메소드인 JSON.parse를 사용한다.

Example:
    >>>$.ajax({

      url           : callUrl, // 설정 url
      type          : "POST",  // 전송 타입 설정 (GET, POST) 방식
      data          : {        // 전송 Data : JSON Object Type
                      "bnnrMngData"  : JSON.stringify(bnnrMngData),
    							    "chkAgreeData" : chkAgreeData
                      },
      traditional   : true,	   // 배열 데이터를 전송할 떄 사용한다.

      // Ajax 비동기 통신이 성공했을때, 호출되는 콜백함수(리턴받는 매개면수 data)
      success		: function (data) {

        // 서버로 부터 받은 데이터는 JSON Object String 타입이다.
        // 이 데이터를 JSON으로 사용하려면 역직렬화해주는 JSON.parse 함수를 사용하면 JSON Object 타입으로 데이터를 가공하여 사용한다.  
        var jObj = JSON.parse(data);
      }
    });

```
Data 속성은 Json : Object Type 데이터가 전송된다.
즉 Data 형식을 Json Object Type으로 전송해줘야한다.

반대로 Ajax가 성공했을때 호출되는 콜백함수에서도 역시 받는 데이터는 Json Object Type이다. JavaScript에서 사용하려면 형 변환을 해야한다. JSON.parse(data); 와 같이

링크참조
> https://poiemaweb.com/js-ajax

#### 1. Ajax(Asynchronous JavaScript and XML)
Ajax(Asynchronous JavaScript and XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미

서버로부터 웹페이지가 반환되면 화면 전체를 갱신해야 하는데 페이지 일부만을 갱신하고도 동일한 효과를 볼 수 있도록 하는 것이 Ajax이다. 페이지 전체를 로드하여 렌더링할 필요가 없고 갱신이 필요한 일부만 로드하여 갱신하면 되므로 빠른 퍼포먼스와 부드러운 화면 표시 효과를 기대할 수 있다.



#### 2. JSON (JavaScript Object Notation)
클라이언트와 서버 간에는 데이터 교환이 필요하다. JSON(JavaScript Object Notation)은 클라이언트와 서버 간 데이터 교환을 위한 규칙 즉 데이터 포맷을 말한다.

JSON은 일반 텍스트 포맷보다 효과적인 데이터 구조화가 가능하며 XML 포맷보다 가볍고 사용하기 간편하며 가독성도 좋다.

자바스크립트의 객체 리터럴과 매우 흡사하다. 하지만 JSON은 순수한 텍스트로 구성된 규칙이 있는 데이터 구조이다.

```JSON
{
  "name": "Lee",
  "gender": "male",
  "age": 20,
  "alive": true
}
```

**키는 반드시 큰따옴표(작은따옴표 사용불가)로 둘러싸야 한다.**

#### 2.1 JSON.stringify

JSON.stringify 메소드는 객체를 JSON 형식의 문자열로 변환한다.

```JavaScript
var o = {
  name: 'Lee',
  gender: 'male',
  age: 20
};

// 객체 => JSON 형식의 문자열
var strObject = JSON.stringify(o);
console.log(typeof strObject, strObject);
// string {"name":"Lee","gender":"male","age":20}

// 객체 => JSON 형식의 문자열 + prettify
var strPrettyObject = JSON.stringify(o, null, 2);
console.log(typeof strPrettyObject, strPrettyObject);
/*
string {
  "name": "Lee",
  "gender": "male",
  "age": 20
}
*/

// replacer
// 값의 타입이 Number이면 필터링되어 반환되지 않는다.
function filter(key, value) {
  return typeof value === 'number' ? undefined : value;
}

// 객체 => JSON 형식의 문자열 + replacer + prettify
var strFilteredObject = JSON.stringify(o, filter, 2);
console.log(typeof strFilteredObject, strFilteredObject);
/*
string {
  "name": "Lee",
  "gender": "male"
}
*/

var arr = [1, 5, 'false'];

// 배열 객체 => 문자열
var strArray = JSON.stringify(arr);
console.log(typeof strArray, strArray); // string [1,5,"false"]

// replacer
// 모든 값을 대문자로 변환된 문자열을 반환한다
function replaceToUpper(key, value) {
  return value.toString().toUpperCase();
}

// 배열 객체 => 문자열 + replacer
var strFilteredArray = JSON.stringify(arr, replaceToUpper);
console.log(typeof strFilteredArray, strFilteredArray); // string "1,5,FALSE"
```

#### 2.2 JSON.parse
JSON.parse 메소드는 JSON 데이터를 가진 문자열을 객체로 변환한다.

> 서버로부터 브라우저로 전송된 JSON 데이터는 문자열이다. 이 문자열을 객체로서 사용하려면 객체화하여야 하는데 이를 역직렬화(Deserializing)이라 한다. 역직렬화를 위해서 내장 객체 JSON의 static 메소드인 JSON.parse를 사용한다.

```JavaScript
// JSON 형식의 문자열 => 객체
var obj = JSON.parse(strObject);
console.log(typeof obj, obj); // object { name: 'Lee', gender: 'male' }

// 문자열 => 배열 객체
var objArray = JSON.parse(strArray);
console.log(typeof objArray, objArray); // object [1, 5, "false"]
```

배열이 JSON 형식의 문자열로 변환되어 있는 경우 JSON.parse는 문자열을 배열 객체로 변환한다. 배열의 요소가 객체인 경우 배열의 요소까지 객체로 변환한다.

```JavaScript
var todos = [
  { id: 1, content: 'HTML', completed: true },
  { id: 2, content: 'CSS', completed: true },
  { id: 3, content: 'JavaScript', completed: false }
];

// 배열 => JSON 형식의 문자열
var str = JSON.stringify(todos);
console.log(typeof str, str);

// JSON 형식의 문자열 => 배열
var parsed = JSON.parse(str);
console.log(typeof parsed, parsed);
```


## 즉시 실행 함수

```JavaScript
// 즉시실행함수, ->함수가 호출되서 실행되는것이 아니고 즉시 함수가 실행
// 함수의 실행 결과값을 변수에 할당한다. ->
// 함수의 결과는 return으로 주로 표현
// return 문이 없으면 결과값이 없기 때문에 undifined가 들어간다.

// static을 사용 유무로 객체 리터럴 방식보다 좋은 이유
// 객체 리터럴방식은 public,
// 즉시 실행 함수 방식은 private
// 내부함수 or 중첩함수
// 내수함수명은 앞에 "_"를 붙인다.
// 내부함수의 접근방법 -> return
```


## HTML DOM Data 속성 값 가져오기

```JavaScript
$this.data("name");

//Target
$("data-name");
```


## Validation 예외 설정

### 공백(스페이스) 제거 정규식

```JavaScript
$this.val().replace(/(\s*)/g, ""):
    replace() 함수를 활용하여, 빈공백(" ") 뛰어쓰기를 전부 없애주는 정규식

Args:
    (/(\s*)/g, "") : 빈 공백을 제거해주는 정규식

Return:
    공백을 제거한 문자열 데이터 리턴

Example:
    >>> var removeBlankData = $this.val().replace(/(\s*)/g, "");
```
