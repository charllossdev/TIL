# Refactoring


## Mysterius Name
* 깔끔한 코드에서 가장 중요한 것 중 하나가 `좋은 이름`
* 함수, 변수, 클래스, 모듈의 이름 등 모두 어떤 역활을 하는지 어떻게 쓰이는지 직관적으로 짓기
* 사용할 수 있는 리펙토링 기술
  1. 함수 선언 변경(Function Declaration)
  2. 변수 이름 변경(Rename Variable)
  3. 필드 이름 변경(Rename Field)


### 함수 선언 변경
* 좋은 이름을 가진 함수는 함수가 어떻게 구현되었는지, 코드를 보지 않아도 이름만 보고 이해 가능한 함수명
  + 함수에 대한 주석을 작성함으로서, 주석을 통해 함수 명 짓기
* 함수의 매개변수
  + 함수 내부의 문맥을 결정(`ex):` `전화번호 포매팅 함수`)
  + 의존성을 결정(`ex):` `Payment` 만기일 계산 함수)