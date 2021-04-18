
# Input

## Scanner
Java는 입력은 Scanner, 출력은 System.out을 사용

* Space Enter를 모두 경계로 인식.

> 입력이 많을 경우 Scanner의 속도가 저하될 수 있다.

```java
  Scanner sc = new Scanner(System.in);
```

## BufferedReader
입력이 많은 경우에는 Scanner의 속도가 느려, BufferedReader를 사용

* Enter만 경계로 인식, 받은 데이터가 String으로 고정.

1. 작업속도에 차이가 많이난다. ( 알고리즘의 효율성 검사에 유리1. readLine() 리턴값은 String으로 고정(다른타입으로 입력을 받을려면 형변환 필요)
2. 예외처리를 꼭 해주어야한다.(보편적으로 throws IOException을 통하여 예외처리)
  (try & catch를 활용하여 예외처리 또한 가능)
```java
  BufferedReader bf = new BufferedReader(new InputStreamReader(System.in)); //선언
  String s = bf.readLine(); //String
  int i = Integer.parseInt(bf.readLine()); //Int
```

> readLine() 주의점
> 1. readLine() 리턴값은 String으로 고정(다른타입으로 입력을 받을려면 형변환 필요)
> 2. 예외처리를 꼭 해주어야한다.(보편적으로 throws IOException을 통하여 예외처리)
(try & catch를 활용하여 예외처리 또한 가능)


# Write

## System.out
Java의 출력 System.out 사용
```java
  System.out.println(message);  
```

> 출력이 많은 경우에는 StringBuilder를 사용

## BufferedWriter
출력이 많은 경우에는 StringBuilder를 사용해서 한 문자열로 만들어서 출력을 한 번만 사용하거나
BufferedWriter를 사용한다.

```java
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));//선언
String s = "abcdefg";//출력할 문자열
bw.write(s+"\n");//출력
bw.flush();//남아있는 데이터를 모두 출력시킴
bw.close();//스트림을 닫음
```

> BufferedWriter의 경우 반드시 flush() / close() 를 호출해 닫아주어야 한다.
> 자동 개행이 없기 때문에 \n 을 통해 개행을 해야 한다.
