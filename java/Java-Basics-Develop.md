# Java

# 문자열 관련 메소드 정리

## charAt()
인수번째의 문자를 읽어 냅니다.

> "abcde".charAt(2)에는 'c'가 읽어 집니다. 0부터 시작하기 때문에 3번째인 'c'가 읽어 집니다.

문자열에 숫자로 인덱스를 지정하면 문자가 나옵니다.

```java
String a = "abcb";
System.out.println(a.charAt(1)); // return 'b'
```

## indexOf()
해당 문자가 들어있는 위치를 알려 줍니다.(문자가 없으면 -1 반환)

> "abcde".indexOf("e")에는 4가 읽어 집니다. 0부터 시작하기 때문입니다.(lastIndexOf는 뒤에서부터 셈)

## substring(args1, args2)
charAt은 문자하나를 읽어내지만 substring은 문자열을 읽어 냅니다.

* 첫번째 인수는 시작지점 문자(반환값에 포함),
* 두번째 인수는 끝지점에 다음문자(반환값에 포함하지 않는다.)

> "abcde".substring(1, 3)은 "bc"를 추출해냅니다.  0부터 시작하기 때문입니다.

## length()
인수의 길이를 나타냅니다..

```JAVA
 String str="abcd";

 int i=str.length();

 System.out.println(i); // return 4
 ```

## isLowerCase(args1)
 isLowerCase() 함수는 입력 받은 인자가 영문 소문자 인지 여부를 판단하여 true 또는  false 값을 리턴 합니다.

```java
public static boolean isLowerCase ( char ch )

public static boolean isLowerCase ( int codePoint )

System.out.println(Character.isLowerCase('t'));
System.out.println(Character.isLowerCase('\u0074'));

```

> 영문 소문자 't' 그리고 영문 소문자 t 의 Unicode 인 \u0074 모두 소문자를 의미 하므로 true가 리턴 됩니다.


```java
System.out.println(Character.isLowerCase('T'));
System.out.println(Character.isLowerCase('\u0054'));
```
> 영문 대문자 'T' 그리고 Unicode 값인 \u0054 모두 대문자 T 를 의미 하므로 false 가 리턴 됩니다.


입력 값이 int 형입니다.

위 Syntax 를 보시면 두번째 함수가 int 형 인자를 받고 있습니다.

Unicode 의 소문자 t를 의미 하는 값으로 true 가 리턴 됩니다.


```java
System.out.println(Character.isLowerCase('7'));
System.out.println(Character.isLowerCase('굿'));
```


char 형의 '7' 값은 영문자가 아닙니다.

또한 '굿' 이라는 한글 캐릭터 역시 영문자가 아니며 당연히 소문자도 아니므로 false 값이 리턴 됩니다.
