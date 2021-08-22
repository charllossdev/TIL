# Code Coverage

코드 커버리지(Code Coverage)
> In computer science, test coverage is a measure used to describe the degree to which the source code of a program is executed when a particular test suite runs. A program with high test coverage, measured as a percentage, has had more of its source code executed during testing, which suggests it has a lower chance of containing undetected software bugs compared to a program with low test coverage. - wikipedia

* 코드 커버리지는 소프트웨어의 테스트 케이스가 얼마나 충족되었는지를 나타내는 지표 중 한가지
* 테스트를 진행하였을 때 ‘코드 자체가 얼마나 실행되었느냐’는 것이고, 이는 수치를 통해 확인 가능


## Code Coverage 측정 기준
코드 커버리지는 소스 코드를 기반으로 수행하는 화이트 박스 테스트를 통해 측정

> 화이트 박스 테스트 <-> 블랙 박스 테스트


---


## 블랙 박스 테스트
* 소프트웨어의 내부 구조나 작동 원리를 모르는 상태에서 동작을 검사하는 방식
* 올바른 입력과 올바르지 않은 입력을 입력하여 **올바른 출력이 나오는지 테스트** 하는 기법
* **사용자 관점** 테스트 방법


## 화이트 박스 테스트
* 응용 프로그램의 **내부 구조와 동작을 검사**하는 테스트 방식
* 소프트웨어 **내부 소스 코드를 테스트**하는 기법
* **개발자 관점** 단위 테스트 기법
