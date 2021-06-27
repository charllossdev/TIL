# Math algorithm

## GCD Algorithm
두 수 A와 B의 최대공약수 G는 A와 B의 공통된 약수 중에서 가장 큰 정수

* 두 수의 작은 값을 기준으로 GCD 구하기
  + Math.min() 메서드를 이용해 두 수중 작은 값을 기준으로 최소 공배수
  ```java
  for (int i = 2; i < min(a, b); i++) {
    if (a % i == 0 && b % i == 0) {
      result1 = i;
    }
  }


  for (int i = min(a, b); i >= 2; i--) {
    if (a % i == 0 && b % i == 0) {
      result2 = i;
      break;
    }
  }
  ```
* 위 방법 보다 더 빠른 방법이 유클리드 호제법
  + a 를 b 로 나눈 나머지를 r이라고 했을 때
    - `GCD(a,b) == GCD(b, r)`
    - `r == 0` 이면, b가 최대 공약수
  + `GCD(24, 16)` == `GCD(16, 8)` == `GCD(8, 0)`
    - `GCD(8, 0)` -> r == 0 이므로, 8이 최대 공약수
  ```java
  int a = max(num1, num2);
  int b = min(num1, num2);

  while(b != 0) {
    int temp = b;
    b = a%b;
    a = temp;
  }
  ```

## LCM Algorithm
두 수의 최소공배수는 두 수의 공통된 배수 중에서 가장 작은 정수

* 두 수 a, b의 최대공약수를 g라고 했을 때
  + 최소 공배수 l = g * (a/g) * (b/g)
  ```java
  int gcd = getGcd(num1, num2);
  int lcm = gcd * (num1/gcd) * (num2/gcd);
  ```
