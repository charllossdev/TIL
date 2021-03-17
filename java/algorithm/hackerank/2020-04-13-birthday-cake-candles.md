# Birthday Cake Candles
https://www.hackerrank.com/challenges/birthday-cake-candles/problem

You are in charge of the cake for your niece's birthday and have decided the cake will have one candle for each year of her total age. When she blows out the candles, she’ll only be able to blow out the tallest ones. Your task is to find out how many candles she can successfully blow out.

For example, if your niece is turning 4 years old, and the cake will have 4 candles of height 4, 4, 1, 2, she will be able to blow out 2 candles successfully, since the tallest candles are of height 4 and there are 2 such candles.

## Function Description
Complete the function birthday Cake Canles in the editor below. It must return an integer representing the number of candles she can blow out.
birthday cake candles has the following parameter(s):
* ar: an array of integers representing candle heights

## Input Format
the first line contains a single integer, $n$, denoting the number of candles on the cake.
the second line contains $n$ space-separated integers, where each integer $i$ describes the height of candle $i$.

## Constraints
* $ 1 ≤ n ≤ 10^5$
* $ 1 ≤ ar[i] ≤ 10^7$

## Output Format
Return the number of canles that can be blown out on a new line.

# Input
```
4
3 2 1 3
```

# Output
```
2
```

# Explanation
We have on candle of height $1$, one candle of height $2$, and two candles of height $3$.
Your niece only blows out the tallest candles, meaning the cnadles where $height = 3$. Because there are $2$ such candles, we print $2$ on a new line.

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

    // Complete the birthdayCakeCandles function below.
    static int birthdayCakeCandles(int[] ar) {

        int maxValue = 0, count = 0;

        for (int i : ar) {
            if (i > maxValue) maxValue = i;
        }

        for (int i : ar) {
            if ( i == maxValue) count++;
        }

        return count;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int arCount = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] ar = new int[arCount];

        String[] arItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < arCount; i++) {
            int arItem = Integer.parseInt(arItems[i]);
            ar[i] = arItem;
        }

        int result = birthdayCakeCandles(ar);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}

```

# Conclusion

문제는 너무 간단했지만, 문제를 해석하고, 이해하는데 시간이 많이 걸렸습니다. 
