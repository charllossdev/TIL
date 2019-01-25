# C# Content

# Categories

0. [Virtual Function](#virtual-function)



---

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
