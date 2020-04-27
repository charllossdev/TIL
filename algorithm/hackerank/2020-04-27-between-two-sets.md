# Between Two Sets
You will be given two arrays of integers and asked to determine all integers that satisfy the following two conditions:

1. The elements of the first array are all factors of the integer being considered
2. The integer being considered is a factor of all elements of the second array


### Function Description

Complete the getTotalX function in the editor below. It should return the number of integers that are betwen the sets.

getTotalX has the following parameter(s):

* a: an array of integers
* b: an array of integers


### Input Format
The first line contains two space-separated integers, $n$ and $m$, the number of elements in array  and the number of elements in array $b$.
The second line contains $n$ distinct space-separated integers describing $a[i]$ where $0 \le i < n$.
The third line contains $m$ distinct space-separated integers describing $b[j]$ where $0 \le j < m$.

### Output Format

Print the number of integers that are considered to be between $a$ and $b$.

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'getTotalX' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. INTEGER_ARRAY a
     *  2. INTEGER_ARRAY b
     */

    public static int getTotalX(List<Integer> a, List<Integer> b) {
    // Write your code here
        int lcmVal = getLcm(a), gcdVal = getGcd(b);
        int count = 0;
        for (int i = lcmVal, j = 2; i <= gcdVal; i= lcmVal*j, j++) {
            if((gcdVal%i) == 0) count++;
        }
        return count;
    }

    public static int getLcm(List<Integer> input) {

        int resultLcm = input.get(0);

        for (int i = 1; i < input.size(); i++) {
            resultLcm = lcm(resultLcm, input.get(i));
        }    
        return resultLcm;
    }

    public static int getGcd(List<Integer> input) {

        int resultGcd = input.get(0);

        for (int i = 1; i < input.size(); i++) {
            resultGcd = gcd(resultGcd, input.get(i));
        }

        return resultGcd;
    }

    // 최소 공배수
    public static int lcm(int a, int b) {
        return a * b / gcd(a,b);
    }

    // 최대 공약수
    public static int gcd(int a, int b) {
        while (b > 0)
        {
            int tmp = a;
            a = b;
            b = tmp%b;
        }
        return a;
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String[] firstMultipleInput = bufferedReader.readLine().replaceAll("\\s+$", "").split(" ");

        int n = Integer.parseInt(firstMultipleInput[0]);

        int m = Integer.parseInt(firstMultipleInput[1]);

        List<Integer> arr = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
            .map(Integer::parseInt)
            .collect(toList());

        List<Integer> brr = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
            .map(Integer::parseInt)
            .collect(toList());

        int total = Result.getTotalX(arr, brr);

        bufferedWriter.write(String.valueOf(total));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

# Study
* [Euclidean Algorithm With Code](/algorithm/euclidean-algorithms.md)


### Get GCD & LCM

```

// GCD: 최대 공약수
public static int gcd(int a, int b) {
    while (b > 0)
    {
        int tmp = a;
        a = b;
        b = tmp%b;
    }
    return a;
}

// LCM: 최소 공배수
public static int lcm(int a, int b) {
    return a * b / gcd(a,b);
}
```

### Get GCD & LCM With List

```java
public static int getLcm(List<Integer> input) {

    int resultLcm = input.get(0);

    for (int i = 1; i < input.size(); i++) {
        resultLcm = lcm(resultLcm, input.get(i));
    }    
    return resultLcm;
}

public static int getGcd(List<Integer> input) {

    int resultGcd = input.get(0);

    for (int i = 1; i < input.size(); i++) {
        resultGcd = gcd(resultGcd, input.get(i));
    }

    return resultGcd;
}
```
