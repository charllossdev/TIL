
# EL 테그

# Form 테그

Window 객체의 location.href == Form 테그의 action 속성

## Javascript 용어 정리

속성 조작 메서드
* removeClass
* addClass
* attr
  - SET 메서드: attr(속성, 넣을 속성의 값) =>attr("action", "논리적 주소")
  - GET 메서드: attr(속성) => 원하는 속성의 값을 가져오는 방법
* val
  - SET 메서드: val(data) => val(전달 인자로 들어온 값이 value로 할당) :
  - GET 메서드: val() : 속성의 값을 가져오는 방법


``` JavaScript
// 객체리터럴 방식 - 클래스
// 렉시컬 컨텍스트라고 부른다.
var leftChk = {   // {} : 렉시컬 스코프 or 클래스

   // : 프로퍼티 정의
   data : "a",   // 필드

   // 클래스 메서드(클래스 이름.메서드 이름으로 호출)
   // Form Submit 방식 페이지 전황
   pageSubmitFn : function(menuStr) { // function() : 익명함수

      // Form 테그의 action 속성에 이동할 주소 논리주소 저장
      $("#leftFrm").attr("action", menuStr + ".do");

      // Form 테그의 자식 요소들의 Input 테그의 value 속성에 값을 저장
      $("#pageName").val(menuStr);   

      // Form 테그의 Submit : 페이지 전환
      // Form 테그의 하위 자식 요소들의 정보들을 모두 가지고 이동한다.
      // Controller에서 HttpServletRequest 객체를 통해 Key&Value로 값을 가져올 수 있다.
      $("#leftFrm").submit();
   }
}

// 자바스크립트에서 클래스 생성은 static
console.log(leftChk.data); //a

leftChk.data = "askdlfjsalkdfjsadf";

console.log(leftChk.data); //askdlfjsalkdfjsadf

leftChk.pageSubmitFn(leftChk.data);

// 이벤트 로딩 메서드
$(function() {

   var pageNameFn = ""; // 전역변수

   //속성 조작 메서드: 선택한 요소의 속성을 조작하는 메서드
   $("#leftUl > li").removeClass("active"); // 클래스 중 해당 속성을 지우는 메서드
   //노드 테그를 제외한 나머지를 노드라고 한다.(테그도 노드)
                        //text()    // 선택한 요소의 텍스트 속성(노드)를 반환하는 메서드
                        //attr()    // 선택한 요소의 전달인자 값의 속성(노드) 제어하는 메서드
                        //val()       // 선택한 요소의 value 속성을 제어하는 메서드
   pageName = "${param.pageHeadName}";

   $("#" + pageName).addClass("active");

   // >: 인접관계 요소 선택자 중에 자식 요소 선택자
   // 단독 이벤트 등록 메서드 중에 마우스 이벤트 등록 메서드(이벤트 리스너)
```
