# Sock Merchant
[Sock Merchant](https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup)

John works at a clothing store. He has a large pile of socks that he must pair by color for sale. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

For example, there are $n=7$ socks with colors . There is one pair of color $ar = [1, 2,1,2,1,3,2]$ and one of color . There are three odd socks left, one of each color. The number of pairs is $2$.

## Function Description

Complete the sockMerchant function in the editor below. It must return an integer representing the number of matching pairs of socks that are available.

sockMerchant has the following parameter(s):

* n: the number of socks in the pile
* ar: the colors of each sock

## Input Format

The first line contains an integer , the number of socks represented in $ar$.
The second line contains $n$ space-separated integers describing the colors $ar[i]$ of the socks in the pile.

## Constraints

* $1 ≤ n ≤ 100$
* $1 ≤ ar[i] ≤ 100$  $where$  $0 ≤ i ≤ n$

## Output Format

Return the total number of matching pairs of socks that John can sell.

## Sample Input
```
9
10 20 20 10 10 30 50 10 20
```

## Sample Output
```
3
```


### Result Code

```java

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the sockMerchant function below.
    public static int sockMerchant(int n, int[] ar) {

        int totalSocks = 0;
        Map<Integer, Integer> sockMap = new HashMap<Integer, Integer>();

        for (int num : ar) {
            if (sockMap.containsKey(num)) {
                sockMap.put(num, sockMap.get(num) + 1);
            } else {
                sockMap.put(num, 1);
            }
        }

        for (int key : sockMap.keySet()) {
            totalSocks += (sockMap.get(key)/2);
        }

        return totalSocks;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] ar = new int[n];

        String[] arItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < n; i++) {
            int arItem = Integer.parseInt(arItems[i]);
            ar[i] = arItem;
        }

        int result = sockMerchant(n, ar);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}

```

# Result

배열 관련 데이터를 정렬하고 정리하는 문제를 자주 만나게 되는데, 만날때마다 항상 잠깐 멈칫하게 된다.
그래서 이번 문제는, 배열 관련 문제를 더 효율적이고, 좋은 해결책을 찾는 방향을 최우선적으로 생각하면서 문제해결에 임했다.

양말의 종류를 맵의 키로 정의하고, 그 양말들의 갯수를 세어 최종적으로 짝이 맞는 양말을 카운팅하였다.

저장에 중점을 두었을 때는 Map이 좋겠지만, 속도측면으로 생각하면 비효율적이라고 생각한다.


## 속도

```Java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the sockMerchant function below.
    public static int sockMerchant(int n, int[] ar) {

        int totalSocks = 0;
        Set<Integer> colors = new HashSet<Integer>();

        for (int key : ar) {
            if (!colors.contains(key)) {
                colors.add(key);
            } else {
                totalSocks++;
                colors.remove(key);
            }
        }

        return totalSocks;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] ar = new int[n];

        String[] arItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < n; i++) {
            int arItem = Integer.parseInt(arItems[i]);
            ar[i] = arItem;
        }

        int result = sockMerchant(n, ar);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}
```
