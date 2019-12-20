# 셀렉트박스 공통

공통 셀렉트박스 만드는 로직

입력받는 파라메터가 오브젝트 배열, 배열 오브젝이 둘다 상관없게 처리

---

**자바스크립트에서 Object와 Array는 typeof를 통해 데이터타입을 구하면 둘다 'Object' 이다.**

Array와 Object를 구분하기 위한 여러가지 방법을 찾게 되었다.

1. Array 클래스 내장함수

```javascript
var _createSelectBox = function(cellVal, opt, rowObj, optionArr) {

  var str = "<select onchange='CmmnJqgrid.changeUpdYNA(" + opt.rowId + ")'>";

  if (Array.isArray(optionArr)) {

    optionArr.forEach(function(e, i) {
      str += "<option value='"+ optionArr[i].nm +"'"+ (optionArr[i].nm === cellVal ? "selected" : "") +">" + optionArr[i].val + "</option>";
    });
  } else if (typeof optionArr === "object"){

    for (i = 0; i < optionArr.nm.length ; i++) {

      str += "<option value='"+ optionArr.nm[i] +"'"+ (optionArr.nm[i] === cellVal ? "selected" : "") +">" + optionArr.val[i] + "</option>";
    }
  }


  return str += "</select>";
}

```

2. 객체의 constructor

```javascript
var _createSelectBox = function(cellVal, opt, rowObj, optionArr) {

  var str = "<select onchange='CmmnJqgrid.changeUpdYNA(" + opt.rowId + ")'>";

  if (optionArr.constructor === Array) {

    optionArr.forEach(function(e, i) {
      str += "<option value='"+ optionArr[i].nm +"'"+ (optionArr[i].nm === cellVal ? "selected" : "") +">" + optionArr[i].val + "</option>";
    });
  } else if (optionArr.constructor === Object) {

    for (i = 0; i < optionArr.nm.length ; i++) {

      str += "<option value='"+ optionArr.nm[i] +"'"+ (optionArr.nm[i] === cellVal ? "selected" : "") +">" + optionArr.val[i] + "</option>";
    }
  }


  return str += "</select>";
}
```


3. instanceof <-> typeof
