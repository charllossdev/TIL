# 3Week


## blur Event


## 날자입력

input readonly 삭제 시
* 숫자만 입력
* 날자 자리수 맞추기

jquery.alphanum.js 을 사용하면 쉽게 가능

```javascript
// jquery.alphanum.js를 이용해서 날짜 인풋테그 숫자만 입력 가능
// 화면 이벤트에 blur가 있으면 이벤트 호환이 굉장히 좋지 않다.
$("[data-date]").numeric({

    // 해당 타켓의 입력 받을 수 있는 자리수 제한 // 최대 8자리
    maxPreDecimalPlaces : 8
});
```



## 공통 js

// 앞자리를 대문자 or 전체를 대문자
// 화면에서 메서드를 호출할때, 화면 내에 있는 객체를 호출하는지, 전역 객체 혹은 공통 객체를 호출하는지 구분하기 위해 해문

* 날짜 유효성 체크 정규식
