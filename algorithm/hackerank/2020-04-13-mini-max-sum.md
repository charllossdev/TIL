# Mini-Max Sum

https://www.hackerrank.com/challenges/mini-max-sum/problem

Given five positive integers, find the minimum and maximum values that can be calculated by summing exactly four of the five integers. Then print the respective minimum and maximum values as a single line of two space-separated long integers.

For example, $ arr = [1, 3, 5, 7, 9] $ . Our minimum sum is $ 1 + 3 + 5 + 7 $  and our maximum sum is $ 3 + 5 + 7 + 9 $. We would print
```
16 24
```

## Function Description

Complete the miniMaxSum function in the editor below. It should print two space-separated integers on one line: the minimum sum and the maximum sum of  $ 4 $ of $ 5 $ elements.

miniMaxSum has the following parameter(s):

arr: an array of $ 5 $ integers
## Input Format

A single line of five space-separated integers.

## Constraints
$ 1 ≤ arr[i] ≤ 10^9 $

## Output Format

Print two space-separated long integers denoting the respective minimum and maximum values that can be calculated by summing exactly four of the five integers. (The output can be greater than a 32 bit integer.)

# Input
```
1 2 3 4 5
```

# Output

```
10 14
```

# Dev
```Java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the miniMaxSum function below.
    static void miniMaxSum(int[] arr) {

        // max, min value set
        int maxNum = 0, minNum = (int)Math.pow(10, 9);
        long sum = 0;

        // find max, min & sum
        for (int i : arr) {

            if (i > maxNum) maxNum = i;
            if (i < minNum) minNum = i;

            sum += i;
        }

        // calculated
        System.out.printf("%d %d", sum - maxNum, sum - minNum);
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int[] arr = new int[5];

        String[] arrItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < 5; i++) {
            int arrItem = Integer.parseInt(arrItems[i]);
            arr[i] = arrItem;
        }

        miniMaxSum(arr);

        scanner.close();
    }
}
```

# Conclusion
Hacker rank algorithm을 순서대로 풀고있어 초반 문제들은 굉장히 쉬운거 같습니다.
그러나 난이도만 굉장히 쉬울 뿐이지 고민을 하게 만드는 요소가 있어서 쉬운 문제라도 푸는 재미가 있습니다.
답만 내는 코딩보다는 과정을 계속 고민해 보는 좋은 경험이 되는거 같고, 마지막 계산에 대해서 데이터 타입의 범위에 대한 이해가 필요한 과제였습니다.
`
