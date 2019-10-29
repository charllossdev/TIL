# 9Week


프로젝트의 규모가 클수록 공통코드를 가져오는 수단을 가장 쉽게하는 방법은

서버를 올릴 때, 모든 공통코드를 자바 휘발성 메모리에 최초로 올려서 공통코드를 쉽게 가져올수 있도록


단점: 서버 실행시 최초로 공통코드를 가져오기 때문에, 공통코드를 수정하거나, 생성하면, 서버를 내렸다 올려야 한다.


# 숙제

데이트피커 날짜 셋팅 설정



---

#Backup

REGR
$(".cal-wrap").each(function(index) {
var $inputVar = $(this).children("input");

// 오늘날짜 세팅
"<c:if test='${bnMngInfo == null}'>"
  $inputVar.datepicker("setDate", "today");
"</c:if>"

// 맥스랭스 체크
$inputVar.attr("maxlength", "8");	// numeric - maxPreDecimalPlaces

// 숫자만 입력
$inputVar.on("keyup", function() {	// 글자를 입력할 때
  //console.log(typeof $(this));
    Picker.setInputOnlyNumber($(this));
  });

$("[data-date]").on("change", function() {
  var getV = $(this).data("date") === "start" ? "end" :"start",
    setV = $(this).data("date") === "start" ? "start" :"end",
    setDate = getV === "start" ? "setStartDate" : "setEndDate",
    dateVal = $(this).val();   

  $("[data-date=" + getV + "]").on("change",function() {
    $("[data-date=" + setV + "]").datepicker(setDate, this.value);
  });

  var $target = getV === "start" ? $(this).parent().prev().children("input") : $(this).parent().next().children("input");

  // datepicker 날짜 형식 체크
  //console.log(index);
  //if (!Picker.validationDate(this.value, index)) {
  //if (!Picker.validationDate(this.value.replace(/[^0-9]/gi, ""), index)) {
  if (!Picker.validationDate(Valid.isNumeric(this.value), index)) {
    // 처음 시작할 때 input태그에 오늘 날짜(2019-08-18)로 입력이 되어 있기 때문에 "-"나 이외의문자는 공백으로 바꾼다
    // -> numeric 숫자만 입력하기 위함~~~!!

    this.value = "";

    this.focus();

    return;	// 디버깅 종료
  }

  if (getV === "start") {

    // 두번째 달력(처음 Click 시) - 첫번째 달력의 값보다 작을 때
    //if (setDateFormat($target.val()) > setDateFormat(dateVal)) {
    //if (new Date(setDateFormat($target.val())) > new Date(setDateFormat(dateVal))) {
    if (new Date(Picker.setDateFormat($target.val())) > new Date(Picker.setDateFormat(dateVal))) {
      $target.val(this.value)
    }

  } else {
    // 첫번째 달력(처음 Click 시) - 두번째 달력의 값보다 클 때
    //if (setDateFormat($target.val()) < setDateFormat(dateVal)) {
    //if (new Date(setDateFormat($target.val())) < new Date(setDateFormat(dateVal))) {
    if (new Date(Picker.setDateFormat($target.val())) < new Date(Picker.setDateFormat(dateVal))) {
      $target.val(this.value);
    }
  }
});
});
