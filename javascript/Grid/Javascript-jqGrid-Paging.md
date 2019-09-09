# Jqgrid Pager Setting

Controller Setting
```java
// jqGrid Ajax Fn
@RequestMapping(value 		= "/getBnnrMngList.do",
                produces	= "application/json; charset=utf8")
@ResponseBody
public String initGetBnnrList(@RequestParam Map<String, Object> reqMap) {

    Map<String, Object> resMap = new HashMap<String, Object>();

    try {

        List<EgovMap> bnList = bnnrService.selectBnnrMngServiceList(reqMap);

        resMap.put("rows",		bnList);
        resMap.put("page",		reqMap.get("page"));
        resMap.put("total", 	bnList.get(0).get("totalPage"));
        resMap.put("records", 	bnList.get(0).get("totalCnt"));

    } catch(Exception e) {

    }

    return JsonUtil.HashMapToJson((HashMap<String, Object>) resMap);
}
```

> 주요설정
> jqGrid가 자동으로 페이징 처리를 해주기 때문에 원하는 설정값만 넘겨주면된다.

* page
* total
* records

Page Setting

```javascript

$("#jqGrid").jqGrid({

    url		 : "<c:url value='/getBnnrMngList.do'/>",
    datatype	 : "json", // 2가지 Options: 1. Json(default), local
    colModel 	 : [
        {label : "번호", 			 name : "bnnrMgnNo",  width : 60,     align : "center",		hidden : true},		// 관리자가 테이블의 키를 볼 일이 없다. 히든
        {label : "제목", 			 name : "subj",       width : 260,    align : "left"},
        {label : "배너유형", 		 name : "bnnrTp",     width : 130,    align : "center"},
        {label : "전시기간", 		 name : "giGan",      width : 260,    align : "center"},
        {label : "진행상태", 		 name : "status",     width : 90,     align : "center"},
        {label : "전시여부", 		 name : "dpYn",       width : 90,     align : "center"},
        {label : "배경이미지여부", name : "bgYn",       width : 250,    align : "center"},
        {label : "등록자", 		 name : "regr",       width : 90,     align : "center"},
        {label : "등록일",		 name : "regDt",      width : 90,     align : "center"}
    ],
    autowidth	 : true,
    autoheight   : true,
    rownumbers   : true,
    caption	 : "배너관리",
    pager	 : "#jqGridPager",
    rowNum	 : 10,				// Pager의 최대 표출 Rows 수
    rowList	 : [10, 20, 30],	// Pager의 최대 표출 Rows 수 변경 옵션
    viewrecords: true				// 표시할 행이 없으면, 행이 없다는 알림 표출
 });

 ```

 주요 옵션
```javascript
pager	 : "#jqGridPager",
rowNum	 : 10,				// Pager의 최대 표출 Rows 수
rowList	 : [10, 20, 30],	// Pager의 최대 표출 Rows 수 변경 옵션
viewrecords: true				// 표시할 행이 없으면, 행이 없다는 알림 표출
```

> pager 속성의 타겟은 jqGrid 밑에 div테그로 잡으면 된다.

```html
<table id="jqGrid"></table>
<div id="jqGridPager"></div>
```
