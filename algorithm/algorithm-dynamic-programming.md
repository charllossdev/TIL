# Dynamic Programming


## Fibonacci Numbers
조건
`f(1) = f(2) = 1`
`f(n) = f(n-1) + f(n-2)`, `단 (n > 2)`
![](assets/dynamic-programming-1445d024.png)

* 단점: 많은 계산이 중복 (비효율적)
![](assets/dynamic-programming-8072eee0.png)

> 개선안

* Memoization
* Bottom-Up

## Memoization
* 피보나치 수열의 중간 계산 과정을 캐싱하여 중복계산을 줄이는 기법
![](assets/dynamic-programming-fc5bf3d8.png)

![](assets/dynamic-programming-242af11d.png)

## Bottom-Up
![](assets/dynamic-programming-9d8b4822.png)

![](assets/dynamic-programming-7d9409b7.png)
