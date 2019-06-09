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

 * required 속성 Default : true
 *


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
@ModelAttribute 해당 클래스 명의 카멜케이스 명으로 모델안에 키로 넣어준다.

@ModelAttribute("vo") 내가 원하는데로 모델안에 키로 넣어준다.

# 어노테이션 선언의 목적(@)

1. 하위 어노테이션을 사용하기 위해서
2. 모든 어노테이션은 인터페이스로 구성되어 있다.

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
