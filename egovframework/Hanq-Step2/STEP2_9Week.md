# 9Week
수업내용 정리

# Java에서의 형변환


# forEach
HTML DOM 뿐만이 아니라, script 영역에서도 사용이 가능하다.

문제는 var itemTest = ${welcomeTest}; 이렇게 List를 변수로 받으려 했지만, 에러가 난다.
> 원인을 찾아보자

```JavaScript
var test = "<c:out value='${scriptTag}'/>";

var item = "<c:out value='${welcomeTest}'/>";

var itemTest = ${welcomeTest};

console.log(item);

<c:forEach items="${welcomeTest}" var="modelData">
  console.log("<c:out value='${modelData.userNm}'/>");
  //console.log(${modelData});
  alert("<c:out value='${modelData}'/>'");
</c:forEach>

```

# @RequestParam

```java
 @RequestParam String age,
 @RequestParam(value="pageName", required=false)
 ```
 * 필수적으로 필요한지, 안필요한지 판단 할 수 있다.
    + Required : TRUE  - 반드시 필요한 변수(키)로, 키값이 넘어오지 않으면 에러
    + Required : FALSE - 반드시 필요한 변수가 아닌것으로, 만약 키가 없다면, null이 들어온다.
    + required 속성 Default : true
 * 연속되는 변수를 받을때, @RequestParam을 중복으로 사용하는지 안하여도 받을 수 있다.
    + @RequestParam을 사용하지 않아도, 뷰에서 전달한 키를 바로 변수로 받을 수 있다.
    - 그러나, 좋은 이식성을 위해 명시적으로 모두 표시해주는것이 바람직
 * value 속성은 화면에서 올린 키 명과, 변수의 이름이 다를경우, value 속성으로 지정 할 수 있다.
 * 쿼리스트링으로 넘기지 않은 키를 받아올때는 Null(만약 @RequestParam을 붙이면 에러 - requied 속성때문에)
 * Map을 통해서 한번에 모든 쿼리스트링 데이터를 받기
 * **VO는 사용 불가능 하다**




# this 연산자
내가 속해있는 힙의 객체의 주소 - 해시코드로 구성되 있따.

# 캡슐화
private 필드를 외부에서 사용할 수 있도록 특권 메서드를 만들어서 비공개 맴버를 사용할 수 있도록 하는 기능

구성 : 특권 메서드와 비공개 맴버

# VO : Visual Object

Mapper XML 에서 VO경로를 설정해줘야 한다. - sel-mapper-config.xml

> VO의 사용처
> 초기값이 있어야 하는 경우는 Map보다 VO를 사용하는 방법이 훨신 더 좋다.

그 외의 경우는 Map을 사용하는 것이 더 좋다.
**Map이 속도가 훨신 빠르기 떄문**

# @RequestParam
(required=false)
선택적으로 받는지 필수적으로 받는지 판단할 수 있는 속성
Default : TRUE

### @RequestParam HashMap map
Map을 통해서 한번에 모든 쿼리스트링 데이터를 받기

# @ModelAttribute
 * @ModelAttribute 해당 클래스 명의 카멜케이스 명으로 모델안에 키로 넣어준다.
 * VO에서 생성한 키와, 화면에서 올린 쿼리스트링의 키가 같다면 VO 필드 안에 Value가 입력된다.
 * @ModelAttribute("vo") 내가 원하는데로 모델안에 키로 넣어준다.

# 어노테이션 선언의 목적(@)

0. 어노테이션을 사용하는 이이유
1. 하위 어노테이션을 사용하기 위해서
2. 모든 어노테이션은 인터페이스로 구성되어 있다.

- Dispatcher-Servlet
  - Component-Scan : 컴포넌트가 붙어있는 객체만, 구분하여 , Bin으로 설치
  - 즉 RquestMpiing :
Spring은 @Component 어노테이션이 붙어있는 객체만 @Bean으로 등록시키는 인젝션이 일어난다.

Spring은 @Component 붙어있는 객체만 @Bean으로 등록시키는 Injection이 일어난다.

dispatcher-Servlet.xml - component-scan 에 등록되있는 경로만 자동으로 등록되도록 한다.
---
@Controllere 어노테이션을 선언하지 않으면, @RequestMapping을 사용할 수 없다.

---

Apache Tomcat: Web Contaioner

동적 웹 어플리케이션 : 정적 어플리케이션들(CSS, IMAGE, JS, JAVASCRIPT)에 동적 서비스가 가능하도록 톰캣같은((Web Container가) 서비스

복습해서 정리하기

하나의 웹 컨테이너 당 하나의 컨텍스트를 생성(정적 웹 자원)

# JavaScript 배열
for(var i = 0; i < arrayLiteral.length; i++){
  alert(arrayLiteral[i]);
}

for(var i in  arrayLiteral){
  alert(arrayLiteral[i]);
}


# 정리

컨테이너인 로컬 웹서버 톰캣을 구동하면, 정적 어플리케이션(CSS, IMAGE, JS,)들은 웹 클라이언트가 요청하면, 웹 서버가 받아서 관리자가 인식하여 DB 죄회를 통해 리턴해주는 방식

현재
정적 어플리케이션에 동적 서비스가 존재(관리자가 했던 작업을 웹 컨테이너인 톰캣이 대신 DB조회)
정적인 웹 루트를 표시해주는 것이 컨텍스트 명 - 컨텍스트 명 등록

dispatcher-Servlet
requestMappingHandlerAdapter -
requestMappingHandlerMapping -

이 2개가 논리적 주소를 받아서, @Bean으로 등록되있는 어노테이션 중에 임믜로 컨트롤러라는 오네세이션을 해한다.

### Dispatcher Servlet.xml

Dispatcher-Servlet 내부
  - Component-Scan : 컴포넌트가 붙어있는 객체만, 구분하여 , Bin으로 설치
  - 즉 RquestMpiing :
Spring은 @Component 어노테이션이 붙어있는 객체만 @Bean으로 등록시키는 인젝션이 일어난다.
Spring은 @Component 붙어있는 객체만 @Bean으로 등록시키는 Injection이 일어난다.
dispatcher-Servlet.xml - component-scan 에 등록되있는 경로만 자동으로 등록되도록 한다.
---
@Controllere 어노테이션을 선언하지 않으면, @RequestMapping을 사용할 수 없다.

* RequestMappingHandlerAdapter
* RequestMappingHandlerMapping

1. 위 RequestMappingHandler Adapter, Mapping2이 논리적 주소(Ex.'/main.do')를 받아서 @bean으로 등록되 있는 정보들 중 @Controller 어노테이션이로 이동한다.
2. @Controller하위에 존재하는 @RequestMapping 벨류 정보와  논리적 주소가 매칭되는 메서드를 찾는다.
3. 그 서비스 메서드가 작동되어 서비스, 서비스임플, 맵퍼를 통해 MVC를 탄다.
4. DB 조회 후 결과물을 리턴받아 데이터를 처리하고 화면으로 올릴 데이터를 모델에 넣는다.
5. 정보를 넣은 모델이 화면으로 바로 가는 것이 아니라, **다시 Dispatcher-Servlet으로 간다.**
> 즉 Dispatcher-Servlet은 2가지를 받는다.
>> 1. return 하는 화면의 논리적 주소
>> 2. 모델 정보

6. Dispatcher-Servlet에 있는 viewResolver(Jstlview)가 2개의 정보를 받는다.
7. 정보를 받은 JstlView는 HTML(DOM)을 그리기 시작한다.
8. DOM을 그리다가, HTML이 아닌 Ex)forEach(Jstl문)이 나온다면, HTML 정보가 아니기 떄문에 정보가 없고, Jstlview가 (No.6)에서 받은 정보 중 모델에 있는 데이터를 찾아서 화면을 그리게 된다.
9. 화면을 다 그린 JstlView는 다시 Dispatcher-Servlet에게 화면에 관련된 정보를 준다.
10. Dispatcher-Servlet은 화면 결과물을 브라우저 서블릿 컨터이너에 결과를 전달한다.
11. HTTP 통신을 하려면, Dispatcher-Servlet에서 받은 결과물을 서블릿 컨테이너가 받아서,  HTTP 통신에 맞는 규격으로 맞춰 사람이 볼수 있도록 파싱하여 브러우저에서 화면이 보이게 된다.

---
# 과제
1. 연습숙제
MVC 파라메터 4가지(String, Map, EgovMap, VO)

화면에서 받는 방법 3가지(HttpServletRequest, RequestParam, ModelAttribute)

응용하는 연습

2. 자바에서 List를 가져와서 8줄 중에 1줄을 빼서, 1줄의 키 벨류 키 벨류 키벨류 한줄을 배열 2개를 선언하여서, 한쪽 배열에는 키만넣고, 나머지 하나는 값만 넣는다.
    1. 마지막으로 2개의 배열을 가지고 map에 키,벨류를 넣는다.

3. Object -> String 형 변환
    2. 강제 형 변환의 경우 try catch를 사용하여 형 변환에 대한 예외를 따로 잡아야 한다는 점
    3. 어떠한 경우를 사용해도 null은 변환될 수 있기 때문에 if/else를 사용하여 잡아줘야 한다는 점


---
