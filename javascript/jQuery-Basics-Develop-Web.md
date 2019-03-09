
# jQuery Basics Develop Web
categoris

* [Jquery](#jquery)
* [Selector](#selector)
* [Basic Method](#basic-method)
* [Array](#Array)


## Jquery

<img src="./img/jQuery.GIF" width="100">

2006년 존 레식(John Resig)이 최초로 출시한 jQuery는 클라이언트 측 솔루션 제작을 손쉽게 만들어주는 크로스 플랫폼 자바크스크립트 라이브러리로 출발했다.

jQuery 웹사이트의 설명에 따르면:
> jQuery는 빠르고, 작고, 기능이 풍부한 자바스크립트 라이브러리입니다. jQuery는 여러 브라우저에서 동작하는 사용하기 쉬운 API를 통해 HTML 문서 탐색과 조작, 이벤트 처리, 애니메이션, Ajax 등을 훨씬 더 간단하게 만들어줍니다. 다양성과 확장성을 겸비한 jQuery는 수백만 명이 자바스크립트 코드를 작성하는 방식을 바꿨습니다.

즉 jQuery는 코드를 단순하고 간결하게 유지하여 많은 반복 루프와 DOM 스크립팅 라이브러리 호출을 작성할 필요가 없게 해준다.

##### jQuery Version

jQuery는 jQuery Foundation을 통해 버전 개발 및 유지 보수가 진행되고 있다.

```
현재 각 jQuery 버전별 최신 버전은 다음과 같다.

버전 1 : jQuery 1.12.4
버전 2 : jQuery 2.2.4
버전 3 : jQuery 3.3.1
jQuery 버전 1은 익스플로러 6, 7, 8 버전에서의 동작까지 모두 지원하는 버전이다.
jQuery 버전 2는 버전 1에서 지원하는 익스플로러 6, 7, 8 버전에 대한 지원을 중단한 버전이다.

2014년 10월에 배포된 jQuery 버전 3은 jQuery의 차세대 표준이다.
jQuery 버전 3은 기존 버전과의 호환성을 유지한 채 더욱 간결하게 작성되고,더욱 빠르게 동작하도록 변경되었다.
2016년 9월에는 jQuery 버전 3의 최신 버전인 3.1.1 버전이 발표되었다.
```
jQuery 최신 버전에 대한 더 자세한 사항은 다음 [링크](http://blog.jquery.com)를 참고하면 된다.

---

### jQuery 장점

* **멀티 브라우져 지원** 이다. 어느 브라우져에서나 동일하게 작동을 한다는 것은 자바스크립트 개발자로서는 너무나 매력적인 일이다. 특히 IE의 독자노선 행보로 인해 IE와 다른 브라우져들은 자바스크립트에서 지원하는 기능이 다르거나, 같은 기능이 있더라도 사용 방법이 다른 경우 jquery에서는 이것을 전부다 해결해준다는 것이 제일 큰 장점이라고 말할 수 있다.

* 멀티 브라우져에서의 ajax이용, 이벤트 설정, DOM 탐색이야말로 jquery의 핵심적인 기능이다.

*  바로 간단하게 이용할 수 있는 핵심 기능들을 포함하고 있다. 다른 것보다도 아마 가장 많이 이용할 기능은 바로 toggleClass나 removeClass등, 일을 할 수 밖에 없게 되는 것을 toggleClass 하나로 해결해 준다. addClass는 그냥 += 을 이용하면 간단하게 해결되지만, 제한된 상황이 아닌 용도에서 정규표현식을 잘 모르면 indexOf, replace, substring 등등 매우 복잡하고 무거운 함수를 만들어야 할 것이다.


* jquery-mobile을 이용해본 사람이라면 모든 모바일 단말에서의 똑같은 UI와 동작으로 인해 그 매력에 빠졌을지도 모른다. 단순히 attribute를 설정해주는 것만으로 UI들이 바로바로 적용되는 놀라운 기능들을 소개해주고 있다.

* 모든 모바일에서 동일한 디자인이 적용된다는 것은 또한 아주 매력적인 장점이다.


* 그 외에도 클래스로 선택했을 경우 $(".className").click() 와 같이 이용할 경우 forEach를 하듯이 모든 element에 속성 부여나 이벤트 부여를 쉽게 해줄 수 있다는 것이 매우 큰 장점 중 하나이다.


## Selector

### Basic Selector

Basic Select Two Kinds

* DOM SELECTOR ID
  ```JavaScript
    $("#dom-select-id")
  ```
* DOM SELECTOR CLASS
  ```javascript
    $(".dom-select-class")
  ```

## Basic Method

메서드
<center>Method</center> |  <center> Description </center> |
|:--------|:--------|
|[attr()](https://www.w3schools.com/jquery/html_attr.asp) | **Get**: When this method is used to return the attribute value, it returns the value of the FIRST matched element. <br /> **Return the value of an attribute**:  jQuery(selector).attr(attribute) <br /><br /> **Set**: When this method is used to set attribute values, it sets one or more attribute/value pairs for the set of matched elements. <br /> **Set the attribute and value**: jQuery(selector).attr(attribute,value)
|[click()](https://www.w3schools.com/jquery/event_click.asp)   | Triggers, or binds a function to the click event of selected elements |
| [val()](https://www.w3schools.com/jquery/html_val.asp) | This method sets the value of the value attribute for ALL matched elements. <br /> **Return the value attribute:** jQuery(selector).val() <br /> **Set the value attribute:** jQuery(selector).val(value)  |
| [addClass()](https://www.w3schools.com/jquery/html_addclass.asp) | This method does not remove existing class attributes, it only adds one or more class names to the class attribute. |
| [removeClass()](https://www.w3schools.com/jquery/html_removeclass.asp)  | The removeClass() method removes one or more class names from the selected elements. |
| [ready()](https://www.w3schools.com/jquery/event_ready.asp) <br> Document Ready | The ready event occurs when the DOM (document object model) has been loaded. <br> **Two syntaxes can be used:** <br /> jQuery(document).ready(function) <br /> jQuery(function)|

## Method

### $.on()

http://api.jquery.com/on/

> .on(events[, selector][,data], handler)

Attach an event handler function for one or move events to the selected elements

```JavaScript
$( "#dataTable tbody tr" ).on( "click", function() {
  console.log( $( this ).text() );
});

// dataTable tbody > tr "SELECT Event Function"
$( "#dataTable tbody" ).on( "click", "tr", function() {
  console.log( $( this ).text() );
});
```

#### Multi Event Handler Function
```JavaScript
$("#container") on ( {
  "change"  : function(){...},
  "blur"    : function(){...},
  "click"   : function(){...}
}, ".foo");
```
## Array


### $.inArray()

Checks if a value exists in an 'Array'

```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log($.inArray("Banana", fruits)); // 0
console.log($.inArray("Orange", fruits)); // 1
console.log($.inArray("Apple", fruits)); // 2
console.log($.inArray("Mango", fruits)); // 3
console.log($.inArray("Melon", fruits)); // -1

var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log( $.inArray("Banana", fruits) >=0 ); // true
console.log( $.inArray("Orange", fruits) >=0 ); // true
console.log( $.inArray("Melon", fruits) >=0 ); // false
```
