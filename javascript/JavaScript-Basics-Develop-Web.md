
# JavaScript
Categoris

* [Javascript Data Type](#javascript-data-type)
* [Javascript Basic Method](#basic-method)
* [Ajax](#ajax)
* [Dom](#dom)]

# JavaScript Data Type

자바스크립트의 DATA Type은 총 7개가 있으며 아래와 같다.

1. Boolean
2. Null
3. Undefined
4. Number
5. String
6. Symbol (ES6 에서 추가)
7. Object
> 위 리스트에서 6번까지는 primitive type 이며  Object 는 primitive가 아니다.  여기서 각 type별로 선언하는 여러가지 방법이 있지만 Object는 아래와 같이 주로 선언한다.


## 자바스크립트 변수

자바스크립트의 변수범위와 호이스팅이 작동하는 원리를 이해하는것은 필수적입니다. 이 두가지 컨셉은 직관적이면서도 이해하기가 쉽지 않습니다. 거기에는 미묘한 차이가 있으며, 자바스크립트 프로젝트에서 성공하기 위해서는 반드시 이해해야 합니다.

변수 범위 (Variable Scope)
변수 범위는 변수가 존재하는 컨텍스트입니다. 이것은 어디에서 변수에 접근할 수 있는지, 그 컨텍스트에서 변수에 접근할 수 있는지를 명시적으로 나타납니다.

변수는 지역 범위(local scope)와 전역 범위(global scope) 둘 중 하나를 가집니다.

지역 변수 (함수 수준 범위)
대부분의 프로그래밍 언어와 달리, 자바스크립트는 블럭-수준(block-level)의 범위를 가지고 있지 않습니다. 대신, 자바스크립트는 함수-수준(function-level)의 범위를 가집니다. 함수내에 정의된 변수는 지역 범위를 가지며, 해당 함수와 내부 함수에서만 접근이 가능합니다. 내부 함수에서 외부 함수의 변수 접근에 관한 더 자세한 내용은 클로저(Closure)를 설명한 글을 참조하시기 바랍니다.


# Basic Method

DOM - Javascript Method

### javascript

```JavaScript
function submitFn(menu) {
  if (menu === "a") {
    return "a...";
  } else {
    return "b...";
  }
}
```

### DOM

```HTML
<a onclick="submitFn('a')" href="#" />
```
---



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


## DOM

문서 객체 모델(DOM; Document Object Model)은 객체 지향 모델로써 구조화된 문서를 표현하는 형식이다. DOM은 플랫폼/언어 중립적으로 구조화된 문서를 표현하며, 표준은 [W3C의 공식 (https://www.w3.org/DOM/)](https://www.w3.org/DOM/)이다.

DOM 은 프로그래밍 언어는 아니지만 DOM 이 없다면 자바스크립트 언어는 웹 페이지 또는 XML 페이지 및 요소들과 관련된 모델이나 개념들에 대한 정보를 갖지 못하게 된다. 문서의 모든 element - 전체 문서, 헤드, 문서 안의 table, table header, table cell 안의 text - 는 **문서를 위한 document object model 의 한 부분이다.** 때문에, **이러한 요소들을 DOM 과 자바스크립트와 같은 스크립팅 언어를 통해 접근하고 조작할 수 있는 것이다.**  

페이지 콘텐츠(the page content)는 DOM 에 저장되고 자바스크립트를 통해 접근하거나 조작할 수 있다. 이것을 방정식으로 표현하면 아래와 같다:

API (web or XML page) = DOM + JS (scripting language)

DOM 은 프로그래밍 언어와 독립적으로 디자인되었다. 때문에 문서의 구조적인 표현은 단일 API 를 통해 이용가능하다.  이 문서에서는 자바스크립트를 주로 사용하였지만, DOM 의 구현은 어떠한 언어에서도 가능하다.

이 문서는 objects 와 types 을 최대한 간단하게 설명하려 한다. API 에는 우리가 반드시 알고 있어야 할 수많은 data types 이 있다는 사실을 염두해 두기 바란다.  이 문서에서는 nodes 는 elements 로, 노드의 arrays 는 nodeLists(또는 elements), attribute 노드들은 attributes 로 표현하였다.

아래의 표는 이러한 data types 에 대한 간략한 설명이다.


<center>Data Type</center> |  <center> Description </center> |
|:--------|:--------|
| **document**  | member 가 document type 의 object 를 리턴할 때(예를 들어 element의 ownerDocument property 는 그것이 속해 있는 document 를 return 한다. ), 이 object 는 root document object 자체이다. 는 document object 에 대한 설명은 [DOM document Reference](https://developer.mozilla.org/en-US/docs/Web/API/document) 챕터를 참조하라.
| **element** | element 는 DOM API 의 member 에 의해 return 된 element 또는 element type 의 node 를 의미한다. [document.createElement()](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) method 가 node 를 참조하는 object 를 리턴한다고 말하는 대신, 이 method 가 DOM 안에서 생생되는 element 를 리턴한다고 좀 더 단순하게 말할 수 있다. element 객체들은 DOM Element interface 와 함께 좀 더 기본적인 Node interface 를 구현한 것이기 때문에 이 reference 에는 두 가지가 모두 포함되었다고 생각하면 된다. |
| **node** | odeList 는 elements 의 배열이다. ([document.getElementsByTagName()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName) method 에 의해 리턴된 것과 같은) nodeList의 Items 은 index 를 통해 접근 가능하며, 다음과 같이 두 가지 방식이 있다.(list.item(1), list[1]) 위의 방식들은 동일한 것이다. item()method는 nodeList object 의 단일 method 이다. 두번째 방식은 list 에서 두번째 item 을 fetch 하는 전형적인 array syntax 이다.    |
| **attribute** | attribute 가 member 에 의해 리턴되는 것은(예를 들어 createAttribute() method 호출에 의한 리턴), attribute 에 대한 특별한 인터페이스를 노출하는 object reference 이다. attributes 는 DOM 에서 elements 와 같은 nodes 이다. elements 만큼 많이 사용되지는 않는다.  |
| **namedNodeMap** | namedNodeMap 는 array 와 유사하지만 items 은 name 또는 index 에 의해 접근 가능하다. 리스트는 특별한 정렬이 적용되지 않았기 enumeration 할 때 index 를 주로 사용한다. namedNodeMap 는 이를 위해 item() method 가 있으며, namedNodeMap 에 item 을 추가하거나 삭제할 수 있다. |
