# Javascript Money Convention

정수형 또는 문자열 타입의 금액에 단위를 표시하는 `,`를 추가하는 정규식

```js

function getMoneyConvetion(money) {

  return money.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}
```
