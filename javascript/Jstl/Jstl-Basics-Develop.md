# JSTL

## forEach
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


```JavaScript
<c:forEach items="${menuList}" var="mainMenuList" varStatus="status">
```

## out

```JavaScript
<c:out value="${}"/>
```

## if

```JavaScript
<c:if test="${mainMenuList.catLv eq '1' }" >
```

#### if 비교 조건 연산자
1. eq = equal (==)

2. ne = not equal (!=)

3. empty = list,map등의 객체가 값이 있다,없다를 구분(ex)empty, !empty)

```JS
<c:if test="${ null eq columnName }"> // null
<c:if test="${ 0 eq columnName }">    // 숫자
<c:if test="${ '0' eq columnName }">  // 문자


<c:if test="${ null ne columnName }"> // null
<c:if test="${ 0 ne columnName }">    // 숫자
<c:if test="${ '0' ne columnName }">  // 문자

<c:if test="${ empty  columnMap}">    // 객체의 값이 비어있다.
<c:if test="${ !empty  columnMap}">   // 객체의 값이 있다.
```
