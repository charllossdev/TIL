# Kotlin
* `NullSafe`, `?`, `?.let{}`
* `var` vs `val`
  + var: mutable object
  + val: immutable object



* let null check
* https://tourspace.tistory.com/208


## Retrofit
Retrofit은 위에서 나온 "Square"라는 회사가 만든 OkHttp 라이브러리의 상위 구현체입니다.
Retrofit은 OkHttp를 네트워크 계층으로 활용하고 그 위에 구축 되었습니다.

일단 Retrofit은 3가지 구성요소가 있습니다.

DTO(POJO): 'Data Transfer Object', 'Plain Old Java Object' 형태의 모델(Model) / JSON 타입변환에 사용
Interface: 사용할 HTTP CRUD동작(메소드) 들을 정의해놓은 인터페이스
CRUD ( Create / Read / Update / Delete ) -> HTTP Method ( POST / GET / PUT / DELETE )
Retrofit.Builder Class: Interface를 사용할 인스턴스, baseUrl(URL) / Converter(변환기) 설정
