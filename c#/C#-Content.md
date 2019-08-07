# C# Content

# Categories
* [Basic](#basic)
    + [String](#string)
* [Method](#method)
    + [Virtual Function](#virtual-function)




---
# Basic
* [String](#string)

## String
* [String <-> string](#string과-string의-차이)
* [String Method](#string-method)
---
### String과 string의 차이
> Language/C# .NET

String은 원래 System.String인데 System 네임스페이스를 using System;으로 사용하고 있기 때문에 String으로 써도 상관없음

__string은 C#에서 사용하는 String의 별칭__

__결론은 차이없다.__

이밖에 int는 System.Int32의 별칭, bool은 System.Boolean의 별칭, double은 System.Double의 별칭이다.

## String Method

### 문자열의 선언

```csharp
string str        = "마음소프트";
String str        = "마음소프트";
System.String str = "마음소프트";
// 보통 첫번째인 string형으로 많이 선언하게 됩니다.
```

### 인덱스(Index)로 접근하기

```csharp
string str = "가나다라마바사";
Response.Write( str[0] );
// 결과는 첫번째 문자인 '가' 출력
```
### 문자열 추가

```csharp
string str1 = "반갑습니다. ";
str1 = str1.Insert(str1.Length, "홍길동님");
str1 = str1.Insert(0, "앗! ");
Response.Write( str1 );
// 결과는 '앗! 반갑습니다. 홍길동님' 출력
string str2 = String.Concat("마", "음", "소", "프", "트");
Response.Write( str2 );
// 결과는 '마음소프트' 출력

string str3 = "마" + "음" + "소" + "프" + "트";
Response.Write( str3 );
// 결과는 '마음소프트' 출력
```

### 대소문자 변환
C#은 대소문자를 구분하기 때문에 자주 사용되며, 대소문자가 구분없는 한글은 별다른 소용이 없습니다.
예를 들면, 'MaumSoft' 값과 'maumsoft' 라는 값은 서로 틀린 값이라고 보시면 되겠습니다. 사실은 같은 값이지만 --;

```csharp
string str = "MaumSoft";
Response.Write( str.ToUpper() );
Response.Write( str.ToLower() );
// 결과는 각각 'MAUMSOFT', 'maumsoft' 출력
```

### 공백 문자열 지우기

```csharp
string str = " 마음소프트 ";
str = str.TrimStart(); // 앞(왼쪽)쪽 문자열 삭제
str = str.TrimEnd(); // 뒤(오른쪽)쪽 문자열 삭제
str = str.Trim(); // 양쪽 문자열 삭제
// 특별한 상황이 아니면, 보통 Trim을 씁니다.
```

### 문자열을 찾아서 문자열 자르기
전체 문자열에서 어떤 문자열을 찾아서, 그 검색된 문자열을 다음 공백까지 잘라내는 작업을 많이 합니다.
전문 용어로 이를 파싱(Parsing)이라고 부릅니다.

```csharp
IndexOf( "검색할 문자열" );
LastIndexOf( "검색할 문자열" );
Substring( 자를 위치 첨자(시작위치) );
Substring( 자를 위치 첨자, 첨자에서 자를 만큼의 길이 );
```
> index : 문자열의 시작 index는 0부터 시작입니다.
* Substring(index) : index +1 부터 문자열 끝까지 출력
* Substring(index, length) : index + 1 부터 length 만큼 출력



#### 구분자 기준으로 문자열 자르기 (Split)
구분자를 기준으로 문자열을 분리시켜서 배열로 반환합니다.
```csharp
string str = "가,나,다,라,마";
string [] result = str.Split(',');
```

### 문자열 치환하기
문자열 중 특정 문자를 다른 문자로 바꾸고 싶을때 Replace 가 사용됩니다. 특히 ASP.NET 에서 내용을 보여줄때 꼭 쓰입니다.

```csharp
// 글 입력을 받을 때 textarea 내에서 엔터를 치면
// /r/n 으로 데이터가 입력됩니다. (일명 Carriage return 과 New line)
string str = "마음소프트\r\nC# 라이브러리";
str = str.Replace( "\r\n", "<br>" );
// 그냥 출력해서 보여주면 내용이 라인 구분없이 계속 붙어 나옵니다.
```
### 그외
System.String 클래스의 인스턴스 메서드
Clone
클래스 참조 반환
CompareTo	특정 객체와 비교
CopyTo	객체 복사
EndsWith	특정 문자열로 끝나는지를 확인
Equals	비교 연산
GetEnumerator	IEnumerator 인터페이스 반환
GetHashCode	해쉬 코드 반환
GetType	형식 정보 반환
GetTypeCode	TypeCode 반환
IndexOf	문자열 검색
IndexOfAny	유니코드 문자열에서 먼저 나오는 문자 반환
Insert	문자열 삽입
LastIndexOf	IndexOf를 뒤에서부터 수행
LastIndexOfAny	IndexOfAny를 뒤에서부터 수행
PadLeft	문자열에서 남아있는 왼쪽을 빈 공백으로 채움
PadRight	문자열에서 남아있는 오른쪽을 빈 공백으로 채움
Remove	지정 개수의 문자 제거
Replace	문자열 치환
Split	문자열 분리하여 배열로 반환
StartsWith	특정 문자로 시작하는지를 확인
Substring	문자열 추출
ToCharArray	문자 배열로 변환
ToLower	소문자로 변환
ToString	객체를 나타내는 문자열 반환
ToUpper	대문자로 변환
Trim	양쪽 공백 없앰
TrimEnd	문자열 끝 부분의 공백 없앰
TrimStart	문자열 시작 부분의


# Method


## Virtual Function

매서드 재정의(Virtual, Override)

### virtual

부모 클래스 함수 앞에 붙는 연산자 키워드
자식 클래스에 의해서 재정의 될 수 있다는 의미 가진다.

컴파일러는 이 지정자가 붙은 함수를 비가상함수와 다르게 컴파일함으로써, 재정의 될 준비를 한다.


### Override

자식 클래스 함수 앞에 붙는 연산자 키워드
부모로부터 상속받는 함수와는 다르게 구현하는 의미를 가진다.

재정의되는 함수는 부모의 함수와 이름, 시그니처도 일치해야 하며, Base 키워드로 부모의 원래함수를 호출 할 수 있다.


#### Example code

```csharp

class Parent
{}
  public virtual void echo()
  {
    console.WriteLine("Parent Echo");
  }
}

class Child : Parent
{
  public override void echo()
  {
    console.WriteLine("Child Echo");
  }
}

class Program
{
  static void Main()
  {
    // 객체 생성
    Parent  P = new Parent();
    Child   C = new Child();

    // Echo 함수 호출
    P.echo();
    C.echo();

    // Parent 클래스 객체에 자식 클래스 객체 C 할당
    Parent P_Dynamic_Test = C;

    // Echo 함수 호출
    P_Dynamic_Test.echo();
  }
}
```

#### Result
실행결과
> 1: Parent echo
> 2: Child Echo
> 3: Child Echo

P.echo와 C.echo는 당연한 결과를 출력했다.
마지막 3번 라인 P_Dynamic_Test.echo는 Child Echo를 출력했다.

> Parent P_Dynamic_Test = C;

위의 선언은 P_Dynamic_Test 객체의 타입
* 정적타입: Parent
* 동적타입: Child

일반적인 비가상 메서드는 정적 타입을 따라서 호출되지만,
가상 메서드는 호출 객체가 실제로 가리키고 있는 타입, 즉 동적 타입을 따르게 된다.

echo 함수가 가상함수 일 떄는 P_Dynamic_Test가 비록 Parent 타입이지만, Derived 객체를 가리키고 있기 때문에 Child 클래스의 echo 함수가 호출된다.

---
만약, 위의 예제를, 즉 가상함수를 -> 비가상함수로 바꾸어 출력한다면 결과는?

> public virtual void echo() -> public void echo()

> public override void echo() -> public new void echo()

실행결과
> 1: Parent echo
> 2: Child Echo
> 3: Parent echo

**참고**
new 연산자를 붙이는 이유:
상속받은 멤버를 완전히 숨겨버리고 자식 클래스가 같은 이름으로 새로운 맴버를 만든다는 뜻으로써, 의도적으로 같은 이름을 사용한다는 것을 알리는 연산자라고 볼 수 있다.

물론 멤버를 숨기는 것이지, 상속을 안받는다는 뜻은 아니다.
base.메서드명()을 호출하면, 부모의 숨겨진 맴버를 상속 받을 수 있게 된다.
