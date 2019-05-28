# JSTL

## forEach

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
