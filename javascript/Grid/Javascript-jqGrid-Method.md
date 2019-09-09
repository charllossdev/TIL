# Jqgrid Event Method

> List

* [그리드 초기화 및 생성](#jqgrid-init)
* [그리드 메서드 정의](#jqgrid-method)
    + Get
        * [특정 셀 데이터 리턴](#getcell)
        * [그리드 설정 옵션 리턴](#getgridparam)
        * [그리드 모든 행 ID 리턴](#getdataids)
        * [그리드 모든 행 데이터 리턴](#getrowdata)
    - Set
        * [그리드 행 추가](#addrowdata)
        * [그리드 행 삭제](#delrowdata)
        * [그리드 셀 속성 설정](#setcolprop)
    - Event
        * [그리드 클릭 이벤트](#oncellselect)
        * [그리드 수동 클릭](#manual-click-event)
        * [그리드 비동기 처리 이벤트](#ajax-event-mehtod)


## Jqgrid Init

그리드 초기옵션 설정  및 생성

```javascript

$("#jqGrid").jqGrid({

    url    	 	: "<c:url value='/dpBnnrList.do'/>",
    datatype   	: "local", // 2가지, 1. Json(default), local
    colModel   	: [
        {label 	: "번호",       		name : "bnnrMngNo",  width : 60,     align : "center",   hidden : true},   // 관리자가 테이블의 키를 볼 일이 없다. 히든
        {label 	: "제목",       		name : "subj",       width : 260,    align : "left"},
        {label 	: "배너유형",     		name : "bnnrTp",     width : 130,    align : "center"},
        {label 	: "전시기간",     		name : "giGan",      width : 260,    align : "center"},
        {label 	: "진행상태",     		name : "status",     width : 90,     align : "center"},
        {label 	: "전시여부",     		name : "dpYn",       width : 90,     align : "center"},
        {label 	: "배경이미지여부", 	        name : "bgYn",       width : 120,    align : "center"},
        {label 	: "등록자",      		name : "regr",       width : 90,     align : "center"},
        {label 	: "등록일",    			name : "regDt",      width : 90,     align : "center"}
    ],
    height   	: "480",
    autowidth  	: true,
    rownumbers 	: true,
    caption	: "배너관리",
    pager	: "#jqGridPager",
    rowNum	: 10,			// 한번에 표시되는 row 수 설정
    rowList	: [10, 20, 30],		// Select Box 생성
    viewrecords	: true, 		// 표시할 행이 없다는 글자 생성

    // == onClick Event Handler
    onCellSelect	: function(rowid, icol, cellVal, e) { // [args] rowid: 선택한row Id, icol: 선택한 행 번호, cellVal: 선택한 행의 값, e: event

        // icol === "2" ? $("#jqGrid").getCell(rowid, "bnnrMngNo") : 0; // 자바스크립트에서는 true/false 처럼 투르시와 펄시 관계를 가지는 값들이 있다
        var bnnrMngNo = $("#jqGrid").getCell(rowid, "bnnrMngNo");

        // 메뉴에 없는 화면은 반드시 Get방식이 좋다 - 뒤로가기 버튼을 고려해서
        // 메뉴를 클릭해서 들어가는 첫 화면은 반드시 포스트 방식
        location.href = "<c:url value='/dpBnnrDtl.do?bnnrMngNo='/>" + bnnrMngNo; // ===location.href = "<c:url value='/bnnrDtl.do?bnnrMngNo=" + bnnrMngNo + "'/>";
    }
 });
});
```

> jqgrid project

| Attribute	|  Description	Default |
|:---|:---|
| url | jqgrid는 그리드 관련 데이터를 갱신할 때 항상 ajax 이벤트가 일어난다. 관련해 ajax url 경로를 설정하는 속성 |
| datatype | jqgrid의 datatype 속성은 2가지로 json(default), local 설정가능하다.  <br>-json: Jqgrid의 이벤트가 발생할 때마다 ajax롤 호출에 데이터를 갱신하는 속성(최초화면 로딩, 그리드 클릭 이벤트 등등),<br>-local: jqgrid 데이터를 갱신하는 ajax 이벤트를 직접 호출해 그리드를 갱신하는 설정 |
| colModel | 그리드의 각 컬럼을 설정하는 모델로, 컬럼의 관련된 속성을 설정 |
| rownumbers | 각 행(row)에 고유한 순번을 부여 |
| pager | 그리드의 페이징 처리표시를 해줄 타겟(div) 아이디 지정 |
| rowNum | 그리드의 한번에 표시될 행의 수 |
| rowList | rowNum 속성의 설정을 변경할 수 있는 값을 설정해 주는 배열 |
| onCellSelect | 그리드의 모든 행의 각 셀을 클릭 시 발생하는 이벤트 핸들러 <br>- args1: 선택한 그리드의 row id <br>- args2: 선택한 그리드의 셀의 순번, colModel의 정의한 순서 <br>- args3: 선택한 그리드의 셀의 value 리턴 <br>- args4: event 리턴 |



# Jqgrid Method

> Get Method

## getCell
특정 셀에 있는 데이터 리턴 메소드

```javascript
/*
 * ### 그리드의 특정 셀의 데이터 가져오기
 * ============================================================
 * # param1(rowId): 원하는 특정 Row Id
 * # param2(colName): 원하는 특정 Cell Name
 */

 var getCellData = $("#jqGrid").getCell(rowId, colName);
```

## getGridParam
그리드의 설정 옵션을 반환해주는 메서드로 옵션 정보란, 초기 그리드 설정 속성들을 의미한다.

```javascript
/*
 * ### 그리드의 셀 설정 정보(colModel)를 배열로 리턴 메소드
 * ============================================================
 * Param X
*/
 var colModelArr = $("#jqGrid").getGridPara("colModel");
 */
```

## getDataIDs
그리드의 모든 row ID를 배열로 리턴하는 메서드

 ```javascript
 /*
  * ### 그리드의 모든 Row ID를 배열로 리턴하는 메서드
  * ============================================================
  * # param X
  */

var rowIdArr = $("#jqgrid").jqGrid("getDataIDs)");
```

## getRowData
그리드에 저장되어있는 Row모든 데이터 또는 Row ID를 전달인자로 주면 해당 Row만 데이터를 가져올 수 있다.

```javascript
/*
 * ###그리드의 모든 행이나, 원하는 행을 리턴하는 메서드
 * ============================================================
 * # param1(rowId): 만약 Row ID를 매개변수로 주면 해당 Row ID의 행의 데이터 리턴
 */

// Row의 모든 데이터를 배열로 가져오는 메서드
var rowDataArr = $("#jqGrid").getGridData();

// 또는 원하는 Row ID를 지정할 경우
var rowData = $("#jqGrid").getGridData(rowId);
```

---

> Set Methid

## addRowData
그리드 행 한줄을 추가하는 메서드

```javascript
/*
 * ### 그리드의 행 한줄을 추가하는 메서드
 * ============================================================
 * # param1(rowId): 추가되는 행의 Row ID 설정
 * # param2(rowData): 추가되는 행의 데이터로 기존의 colModel과 매치되어야 한다.
 * #param3(position): 추가되는 데이터의 위치를 설정(first, last, before, after) 4가지 속성이 있다.- Default: last
 * #param4(srcRowId): postion 속성값이 before, after일때, 타겟이 되는 ID를 설정해준다.
 */

 $("#jqGrid").addRowData(newRowId, newRowData, "last");
 ```

## delRowData
그리드 행 한줄을 삭제하는 메서드

```javascript
/*
 * ### 그리드의 행 한줄을 삭제하는 메서드
 * ============================================================
 * # param1(rowId): 삭제를 원하는 특정 Row Id
 */

$("#jqGrid").delRowData(rowId);
```

## setColProp
그리드 colModel 속성을 설정하는 메서드로, colModel의 name을 지정해 주어야한다.

```javascript
/*
 * ### 그리드의 colModel 속성을 설정하는 메서드
 * ============================================================
 * # param1(colName): 설정을 원하는 colModel의 name
 * # param2(option): 원하는 설정 값.
 */

$("#jqGrid").setColProp(colName, {edittable: true});
```

---

# Jqgrid Event Handler

## onCellSelect

```javascript
// == onClick Event Handler
/*
 * ### 그리드 Cell Click Event Handler
 * ============================================================
 * # param1(rowNum): 선택한 Row Id 리턴
 * # param2(colNum): 선택한 Cell Id 리턴
 * # param3(cellVal): 선택한 Cell Value 리턴
 * # param4(event): 일어난 이벤트 리턴)
 */
onCellSelect	: function(rowNum, colNum, cellVal, e) {
}
```

## Manual Click Event
사용자가 지정한 그리드의 좌표를 편집해주는 메서드

```javascript
/*
 * ### 지정한 그리드의 좌표를  클릭하는 메서드
 * ============================================================
 * # param1(rowIndex): Row Index , 행의 인덱스(RowID가 아니다.)
 * # param2(colIndex): Col index, 열의 인덱스
 * # param3(edit): bool값으로 true는 cell 편집, false는 cell이 편집되지 않는다.
 */

// 해당 좌표의 cell을 클릭 or 편집
$("#jqGrid").editCell(rowIndex, colIndex, true);
```

## Ajax Event Mehtod

```text
Jqgrid Ajax Event:
    Jqgrid설정에 따라 Aajx 이벤트가 일어날때 처리하는 메서드로 Aajx 결과값을 그리드에 반영하고, 그리드만 새로고침하여 실시간으로 데이터가 갱신되도록 한다.

Args: X

Return: X
```

```javascript
$("#jqGrid").setGridParam({

     datatype    : "json",

     loadComplete  : function(data) {
       console.log("data : ", data);
     }
   }).trigger("reloadGrid");
```
