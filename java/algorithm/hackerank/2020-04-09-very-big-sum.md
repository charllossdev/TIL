# Very Big Sum
https://www.hackerrank.com/challenges/a-very-big-sum/problem

![](assets/02.Very-Big-Sum-3e6b2f19.png)

# Input Format
![](assets/02.Very-Big-Sum-bd6b1455.png)

# Output
![](assets/02.Very-Big-Sum-15d5cbc9.png)

![](assets/02.Very-Big-Sum-fd383351.png)


# Code

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the aVeryBigSum function below.
    static long aVeryBigSum(long[] ar) {

        long resultValue = 0;

        for (int i = 0; i < ar.length; i++) {
            resultValue += ar[i];
        }

        return resultValue;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int arCount = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        long[] ar = new long[arCount];

        String[] arItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < arCount; i++) {
            long arItem = Long.parseLong(arItems[i]);
            ar[i] = arItem;
        }

        long result = aVeryBigSum(ar);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}

```
