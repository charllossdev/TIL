# Javascript Delete Text Blank

## Trim
Trim은 앞 뒤 공백만 제거해준다.

```js
var text = $.trim(BLANK_TEXT);
```

## a regular expression
정규식을 사용하면, 원하는 스타일 대로 공백을 제거 가능하다.

```js
 var re = /(\s*)/g  // 문자열 모든 공백 제거
 var re = /^\s*/    // 문자열 앞 공백 제거
 var re = /\s*$/    // 문자열 뒤 공백 제거

 // 공백제거 적용
 BLANK_TEXT.replace(re);
```
