# 9주차 과제

# 데이트피커 날짜 셋팅 로직 변경

데이트피커 즉시실행 공통함수 부분


```JavaScript
/**
 * 데이트피커 커스텀
 */
var CmmnDatePicker = (function() {

	/**
	 * 데이트 피커 설정
	 */
	var _setDatePicker = function(newDateYn) {

	   	$(".cal-wrap").each(function(index) {
			var $inputVar = $(this).children("input");

```

공통함수 메서드 실행 시 체크 플레그인 텍스트가 N인 경우는 Model의 데이터가 있는 경우로,

모델의 날짜 데이터를 벨리데이션하여 데이커피커에 설정하는 로직 추가

최초 설정한 날짜로 각 시작 날짜와, 종료 날짜의 Min, Max 입력제한 설정 메서드 호출

```JavaScript
			// 오늘날짜 세팅
			if (newDateYn !=="N") {
				$inputVar.datepicker("setDate", "today");
			} else { // Model에서 날자 데이터를 가져오는 경우

				// 가져온 날짜 Validation
				Picker.setInputOnlyNumber($inputVar);

				// 유효한 날짜 datepicker 입력설정
				$inputVar.datepicker("setDate", Picker.setDateFormat($inputVar.val()));

				// Min, Max 설정
				SetDatePickerLimit($inputVar);
}

			// 맥스랭스 체크
			$inputVar.attr("maxlength", "8");	// numeric - maxPreDecimalPlaces

			// 숫자만 입력
			$inputVar.on("keyup", function() {	// 글자를 입력할 때
				//console.log(typeof $(this));
		    	Picker.setInputOnlyNumber($(this));
		    });

```

날자 입력을 변경 이벤트 시, 기존에 중복 이벤트 처리로,

설정한 날짜로 각 시작 날짜와, 종료 날짜의 Min, Max 입력제한 설정 메서드 호출로직으로 개선

```JavaScript
			$("[data-date]").on("change", function() {
				var $input		= $(this);
					getV 		= $input.data("date") === "start" ? "end" :"start",	// 반대
					dateVal	 	= $input.val();   

				/* 기존코드
				 *
				$("[data-date=" + getV + "]").on("change",function() {
					$("[data-date=" + setV + "]").datepicker(setDate, this.value);
				});
				*/

				// *개선* Min, Max 설정
				SetDatePickerLimit($input);

				var $target = getV === "start" ? $(this).parent().prev().children("input") : $(this).parent().next().children("input");

				// datepicker 날짜 형식 체크
				if (!Picker.validationDate(Valid.isNumeric(this.value), index)) {

					this.value = "";

					this.focus();

					return;	// 디버깅 종료
				}

				if (getV === "start") {

					if (new Date(Picker.setDateFormat($target.val())) > new Date(Picker.setDateFormat(dateVal))) {
						$target.val(this.value)
					}

				} else {

					if (new Date(Picker.setDateFormat($target.val())) < new Date(Picker.setDateFormat(dateVal))) {
						$target.val(this.value);
					}
				}
			});
	    });
	}

	return {
		setDatePicker	: _setDatePicker
	}
}());

function SetDatePickerLimit($inputTag) {

	var setV 			= $inputTag.data("date") === "start" ? "end" : "start",
		setLimitDate	= setV === "start" ? "setEndDate" : "setStartDate";

	$("[data-date=" + setV + "]").datepicker(setLimitDate, $inputTag.val());
}

```
