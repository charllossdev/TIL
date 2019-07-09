# [C#의 Value Type과 Reference Type의 비교]

* Value Type : 메모리에 값이 직접 저장되는 타입이다.
* Reference Type : 메모리에 데이터가 위치한 주소(참조)를 저장하는 타입이다.



<center>Data Type</center> |  <center> Value Type </center> | <center> Reference Type </center> |
|:--------|:--------|:--------|
| 메모리위치는? | 스택(Stack)에 활당 | 관리화 힙(Managed Heap)에 활당 |
| 메모리에 뭐가 저장될까? | 데이터 | 데이터가 위치한 메모리 주소 |
| 상속이 가능한가? | No | Yes |
| 매개변수의 전달은? | Call by Value | Call by Reference |
| 언제 메모리에서 사라지는가? | 정의한 범위 밖에서 | 가비지 컬렉터에 걸릴때 |
| 어떤 데이터형이 있을까? | 기본데이터 타입, 구조체, 열거형 | 클래스, 배열, 델리게이트, 인터페이스 |
