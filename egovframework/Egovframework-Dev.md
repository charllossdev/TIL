# Egovframework Develop Content

# MVC 관련 제어

## View -> Controller 다수의 키/벨류 데이터 올리기

만약 뷰에서 키와 그에 대한 값을 100개를 컨트롤러로 전송한다면, 컨트롤러에서는 이 키/값을 처리하기 위해서 Servlet에서 HttpServletRequest 객체를 이용해서 100개의 키를 받아 와야하는 어려움이 있다.

> 스프링 Servlet에서 화면에서 올린 키의 모든 모음을 한번에 받을 수 있는 기능이 있다.
> **getParameterNames();** 메서드

> 열거형 인터페이스 사용법 주의

```java
@RequestMapping("/main.do")
public String initMain(@RequestParam String arr, ModelMap model, HttpServletRequest req) throws Exception {

  String[] arrayTest = null;

  // 스프링 Servlet에서 화면에서 올린 키의 모음을 받을 수 있는 기능
  // Enumeration 열거형 타입 인터페이스
  Enumeration<String> names = req.getParameterNames();

  // 열거형 인터페이스를 사용할 떄는 for문을 절대 사용하지 않고, while문을 사용하는 암묵적인 룰
  // hasMoreElements : 첫번째 데이터를 리턴하고 다음 커서로 이동 -> 값을 하나씩 리턴하면서 다음커서로 이동하여 맨끝까지
  while (names.hasMoreElements()) {

    // 커서가 가리키는 값을 가져오고, 다음 커서를 가리키게 한다.
      String name = names.nextElement();

      System.out.println("각각의 Key : " + name);

      String value = req.getParameter(name);

      System.out.println("각각의 value : " + value);
  }

  if (arr != null) {
    arrayTest = arr.split(","); // split을 사용할 떄는 반드시 널 체크를 해야한다(인생공식)

    model.addAttribute("arr", arrayTest);
  }

  return "main/main.tiles";
}
```
