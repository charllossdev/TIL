# Javascript Rgular Expression

## 날짜  YYYY-MM-DD

```javascript
var dayRegExp = /^(19|20)\d{2}-(0[1-9]|1[012])-(0[1-9]|[12][0-9]|3[0-1])$/;
```

## 시간  HH24:mm (24시간)

```javascript
var timeRegExp = /^([1-9]|[01][0-9]|2[0-3]):([0-5][0-9])$/;
```


## 복합 YYYYMMDD HH24:mm (중간 공백)

```javascript
var RegExp = /^(19|20)\d{2}(0[1-9]|1[012])(0[1-9]|[12][0-9]|3[0-1])\s([1-9]|[01][0-9]|2[0-3]):([0-5][0-9])$/;
```
