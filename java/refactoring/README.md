# Refactoring


# Mysterius Name
---
* 깔끔한 코드에서 가장 중요한 것 중 하나가 `좋은 이름`
* 함수, 변수, 클래스, 모듈의 이름 등 모두 어떤 역활을 하는지 어떻게 쓰이는지 직관적으로 짓기
---
* Mysterius Name refactoring
  1. 함수 선언 변경(Function Declaration)
  2. 변수 이름 변경(Rename Variable)
  3. 필드 이름 변경(Rename Field)


## 함수 선언 변경
* 좋은 이름을 가진 함수는 함수가 어떻게 구현되었는지, 코드를 보지 않아도 이름만 보고 이해 가능한 함수명
  + 함수에 대한 주석을 작성함으로서, 주석을 통해 함수 명 짓기
* 함수의 매개변수
  + 함수 내부의 문맥을 결정(`ex):` `전화번호 포매팅 함수`)
  + 의존성을 결정(`ex):` `Payment 만기일 계산 함수`)

## 변수 이름 변경
* 더 많이 사용되는 변수일수록 네이밍이 중요
  + 람다식에서 사용하는 변수 vs 함수의 매개변수
* 다이나믹 타입을 지원하는 언어에서는 타입을 이름에 넣는것도 방법
* 여러 함수에 걸쳐 쓰이는 필드 이름에는 더 많이 고민하여 네이밍이 필요

## 필드 이름 변경
* Record 자료 구조의 필드 이름은 프로그램 전반에 걸쳐 참조될 수 있기 때문에, 매우 중요
  + Record 자료 구조: 특정 데이터와 관련있는 필드를 묶어놓은 자료 구조
  + Python의 [Dictionay](https://docs.python.org/3/tutorial/datastructures.html#dictionaries) -> dicts
  + C#의 [Record](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/record-structs)
  + 자바 14 버전부터 `record` 키워드로 지원


# Duplicated Code
---
* 중복 코드의 단점
  + 비슷한지, 완전한 동일한 코드인지 주의 깊게 봐야하는 번거로움
  + **코드를 변경할 때, 동일한 모든 곳의 코드를 변경**
---
* Duplicated Code
  1. 함수 추출(Extract Function): 동일한 코드를 여러 메소드에서 사용하는 경우
  2. 코드 분리(Slide Statements): 코드가 비슷하게 생겼지만, 완전히 같지는 않은 경우
  3. 클래스 메소드 업(Pull Up Method): 여러 하위 클래스에 동일한 코드가 있을 경우
