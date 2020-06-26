# JSTL Get Today Date
서버에서 받은 데이터를 JSP 페이지에서 날짜나 시간을 노출하거나 계산해야할 때가 많은데, 이 때 JSTL에서 제공하는 Formatting Tag(fmt)를 사용하면 쉽게 처리가 가능하다.

## Imfort JSTL Formatting Tags Include

```js
<%@ taglib prefix = "fmt" uri = "http://java.sun.com/jsp/jstl/fmt" %>
```


## Get Today Date

```js
<jsp:useBean id="now" class="java.util.Date" />
<fmt:formatDate value="${now}" pattern="yyyy-MM-dd" var="today" />  
```

or

```js
<c:set var="today" value="<%=new Date()%>">
<fmt:formatDate value="${today}" pattern="yyyy-MM-dd" var="today"/>
```

### fmt 테크

화면 출력
```js
<fmt:formatDate value="${today}" pattern="yyyy-MM-dd"/>
```

내부 변수 저장
```js
// 값 저장
<fmt:formatDate value="${today}" pattern="yyyy-MM-dd" var="getToday"/>

// 값 가져오기
<c:out value="${getToday}"/>
```

위와 같이 `fmt태그 var속성을 주면 EL태그 ${getToday}` 값이 저장된다.
> 저장된 값을 가져올땐,
