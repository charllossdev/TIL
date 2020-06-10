# Select Box Option

```js
// select box ID로 접근하여 선택된 값 읽기
$("#셀렉트박스ID option:selected").val();

// select box Name로 접근하여 선택된 값 읽기
$("select[name=셀렉트박스name]").val();

// 같은 방식으로 span과 같은 다른 태그도 접근 가능하다~
$("span[name=셀렉트박스name]").text();

// 선택된 값의 index를 불러오기
var index = $("#셀렉트박스ID option").index($("#셀렉트박스ID option:selected"));

// 셀렉트 박스에 option값 추가하기
$("#셀렉트박스ID").append("<option value='1'>1번</option>");

// 셀렉트 박스 option의 맨앞에 추가 할 경우
$("#셀렉트박스ID").prepend("<option value='0'>0번</option>");

// 셀렉트 박스의 html 전체를 변경할 경우
$("#셀렉트박스ID").html("<option value='1'>1차</option><option value='2'>2차</option>");

// 셀렉트 박스의 index별로 replace를 할 경우
// 해당 객체를 가져오게 되면, option이 다수가 되므로 배열 객체가 되어 eq에 index를 넣어 개별 개체를 선택할 수 있다.
$("#셀렉트박스ID option:eq(1)").replaceWith("<option value='1'>1차</option>");

// 직접 index 값을 주어 selected 속성 주기
$("#셀렉트ID option:eq(1)").attr("selected", "selected");

// text 값으로 selected 속성 주기
$("#셀렉트ID")val("1번").attr("selected", "selected");

or

$("#id").text("1번").attr("selected", "selected");

// value 값으로 selected 속성 주기
$("#셀렉트ID").val("1");

or

$("#id").val("1").prop("selected", true);

// 해당 index item 삭제하기
$("#셀렉트ID option:eq(0)").remove();

// 첫번째, 마지막 item 삭제하기
$("#셀렉트ID option:first").remove();
$("#셀렉트ID option:last").remove();

// 선택된 옵션의 text, value 구하기
$("#셀렉트ID option:selected").text();
$("#셀렉트ID option:selected").val();

// 선택된 옵션의 index 구하기
$("#셀렉트ID option").index($("#셀렉트ID option:selected"));

// 셀렉트박스의 아이템 갯수 구하기
$("#셀렉트ID option").size();

// 선택된 옵션 전까지의 item 갯수 구하기
$("#셀렉트ID option:selected").prevAll().size();

// 선택된 옵션 후의 item 갯수 구하기
$("#셀렉트ID option:selected").nextAll().size();

// 해당 index item 이후에 option item 추가 하기
$("#셀렉트ID option:eq(0)").after("<option value='3'>3번</option>");

// 해당 index item 전에 option item 추가하기
$("#셀렉트ID option:eq(3)").before("<option value='2'>2번</option>");

// 해당 셀렉트 박스에 change event binding 하기
$("#selectID").change(function() {
alert($(this).val());
alert($(this).children("option:selected").text());
});

```


출처: https://oingbong.tistory.com/175 [Oing]
