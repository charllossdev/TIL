# Week3

---

수업 내용 정리
* jQuery
* DOM
* QueryString

MetroKing
* PROJECT NAME: **week3_assignment**
  - 소스 리펙토링
  - 하이라이트 처리

Review
* PROJECT NAME: **week3_review**
  - 3~4 교시 복습
  - 공부내용 주석

---

<img src="./img/jQuery.GIF" width="100">
### 1.jQuery란?

2006년 존 레식(John Resig)이 최초로 출시한 jQuery는 클라이언트 측 솔루션 제작을 손쉽게 만들어주는 크로스 플랫폼 자바크스크립트 라이브러리로 출발했다.

jQuery 웹사이트의 설명에 따르면:
>jQuery는 빠르고, 작고, 기능이 풍부한 자바스크립트 라이브러리입니다. jQuery는 여러 브라우저에서 동작하는 사용하기 쉬운 API를 통해 HTML 문서 탐색과 조작, 이벤트 처리, 애니메이션, Ajax 등을 훨씬 더 간단하게 만들어줍니다. 다양성과 확장성을 겸비한 jQuery는 수백만 명이 자바스크립트 코드를 작성하는 방식을 바꿨습니다.

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

#### 1.1 jQuery 장점

* **멀티 브라우져 지원** 이다. 어느 브라우져에서나 동일하게 작동을 한다는 것은 자바스크립트 개발자로서는 너무나 매력적인 일이다. 특히 IE의 독자노선 행보로 인해 IE와 다른 브라우져들은 자바스크립트에서 지원하는 기능이 다르거나, 같은 기능이 있더라도 사용 방법이 다른 경우 jquery에서는 이것을 전부다 해결해준다는 것이 제일 큰 장점이라고 말할 수 있다.

* 멀티 브라우져에서의 ajax이용, 이벤트 설정, DOM 탐색이야말로 jquery의 핵심적인 기능이다.

*  바로 간단하게 이용할 수 있는 핵심 기능들을 포함하고 있다. 다른 것보다도 아마 가장 많이 이용할 기능은 바로 toggleClass나 removeClass등, 일을 할 수 밖에 없게 되는 것을 toggleClass 하나로 해결해 준다. addClass는 그냥 += 을 이용하면 간단하게 해결되지만, 제한된 상황이 아닌 용도에서 정규표현식을 잘 모르면 indexOf, replace, substring 등등 매우 복잡하고 무거운 함수를 만들어야 할 것이다.


* jquery-mobile을 이용해본 사람이라면 모든 모바일 단말에서의 똑같은 UI와 동작으로 인해 그 매력에 빠졌을지도 모른다. 단순히 attribute를 설정해주는 것만으로 UI들이 바로바로 적용되는 놀라운 기능들을 소개해주고 있다.

* 모든 모바일에서 동일한 디자인이 적용된다는 것은 또한 아주 매력적인 장점이다.


* 그 외에도 클래스로 선택했을 경우 $("className").click() 와 같이 이용할 경우 forEach를 하듯이 모든 element에 속성 부여나 이벤트 부여를 쉽게 해줄 수 있다는 것이 매우 큰 장점 중 하나이다.

---

#### 1.2 jQuery 기초 및 메서드

선언
   - jQuery() === $()

호출
  - ID호출 : $("#ID_NAME")
  - 클래스호출 : $(".CLASS_NAME")

메서드
<center>Method</center> |  <center> Description </center> |
|:--------|:--------|
|[attr()](https://www.w3schools.com/jquery/html_attr.asp) | **Get**: When this method is used to return the attribute value, it returns the value of the FIRST matched element. <br /> **Return the value of an attribute**:  jQuery(selector).attr(attribute) <br /><br /> **Set**: When this method is used to set attribute values, it sets one or more attribute/value pairs for the set of matched elements. <br /> **Set the attribute and value**: jQuery(selector).attr(attribute,value)
|[click()](https://www.w3schools.com/jquery/event_click.asp)   | Triggers, or binds a function to the click event of selected elements |
| [val()](https://www.w3schools.com/jquery/html_val.asp) | This method sets the value of the value attribute for ALL matched elements. <br /> **Return the value attribute:** jQuery(selector).val() <br /> **Set the value attribute:** jQuery(selector).val(value)  |
| [addClass()](https://www.w3schools.com/jquery/html_addclass.asp) | This method does not remove existing class attributes, it only adds one or more class names to the class attribute. |
| [removeClass()](https://www.w3schools.com/jquery/html_removeclass.asp)  | The removeClass() method removes one or more class names from the selected elements. |
| [ready()](https://www.w3schools.com/jquery/event_ready.asp) <br> Document Ready | The ready event occurs when the DOM (document object model) has been loaded. <br> **Two syntaxes can be used:** <br /> jQuery(document).ready(function) <br /> jQuery(function)|

---

#### 1.3 DOM
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

---

#### 1.4 쿼리스트링
쿼리스트링은 사용자가 웹프로그램으로 입력 데이터를 전달하는 가장 단순하고 또한 널리 사용되는 방법이다. 이 방법은 URL 주소 뒤에 입력 데이터를 함께 제공하는 방법으로 다음과 같은 형식을 취한다.

```Java
http://hostname[:port]/folder/file?변수1=값1&변수2=값2&변수3=값3
```
위 형식에서 “?” 뒤의 표현된 부분이 쿼리스트링 이다. URL 주소와 쿼리스트링은 “?”로 구분되며 변수와 값의 쌍(변수=값)으로 구성된다. 만약 여러 쌍의 변수와 값을 전달할 경우 각각의 쌍을 “&”로 구분해주면 된다.

---

#### 1.4.1 쿼리스트링 받아오는 방법

**Java**
* HTTPServletRequest 클래스
  - HTTPServletRequest 클래스는 쿼리스트링 데이터뿐만 아니라 클라이언트 IP 등의 정보를 가져오거나, 쿠키, 헤더로 전송한 값을 가져오는데 주로 사용한다.
   ![Image](./img/Image_16g5mmx6q.png)

**Jsp**
* param
  - EL (Expression Language)로 param 은 파라미터값으로 이전 화면에 정보를 가지고 있는 객체를 뜻하고 data는 그 데이터중 data이라는 키의 데이터의 값을 가져온다.
![query_string](./img/query_string.PNG)
> 주의
> 1. param으로 파라미터값을 받아오려면 동적 텍스트를 출력을 위해 항상 c:out 을 사용해야한다(보안문제).
> 2. 사용하기 위해서는 JSTL 디렉티브를 추가해야 한다.
> ![c_out](./img/c_out.PNG)
> 3. 데이터 전송을 GET방식으로 할 경우에 한글 사용을 하려면 인코딩을 해주어야 한다.(Tomcat Server Localhost Config/server.xml)![server_encoding](./img/server_encoding.PNG)
