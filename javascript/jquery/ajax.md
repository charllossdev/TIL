# Jquery Ajax
Ajax(Asynchronous Javascript and XML): 웹페이지가 서버와 비동기 통신을 하는 기술의 집합체

Ajax Convention
```js
$(function() {
  $.ajax({
    ...
  })
});

```

## 자주 사용되는 Ajax 옵션
![](assets/ajax-f365e119.png)

## Ajax Data Serialize
Ajax 비동기 통신에서 Post로 데이터를 보낼 때, 데이터를 Json으로 정렬화 하는 방법

```js
$.ajax({
  url: "url",
  async: true,
  type: "POST",
  data: $("form[name=formTagName]").serialize(),
    success: function(data) {
    }
  },
  error: function(errCode, errMsg, jqXHR){
    console.log("errCode: " + errCode + "\nerrMsg:" + errMsg);
  },
  complete: function (data) {
  }
});
```

> data: $("form[name=formTagName]").serialize(),

jQuery form 태그를 serialize()하면 쉽게 JSON으로 전송이 가능하다.

## Ajax JSON
ajax에서 JSON.parse()와 JSON.stringify()에 대해서 정리한다.

* JSON.parse(): String 객체를 Json 객체로 변환
* JSON.stringify(): Json객체를 String 객체로 변환
