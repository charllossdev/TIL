# Time Conversion
https://www.hackerrank.com/challenges/time-conversion/problem?h_r=next-challenge&h_v=zen

Given a time in $12$-hour AM/PM format, convert it to military (24-hour) time.

Note: Midnight is 12:00:00AM on a 12-hour clock, and 00:00:00 on a 24-hour clock. Noon is 12:00:00PM on a 12-hour clock, and 12:00:00 on a 24-hour clock.

## Function Description

Complete the timeConversion function in the editor below. It should return a new string representing the input time in 24 hour format.

timeConversion has the following parameter(s):

s: a string representing time in 12 hour format

## Input Format

A single string $8$ containing a time in $12$-hour clock format($i.e$: $hh:mm:ssAM$ or $hh:mm:ssPM$), where $01 ≤ hh ≤ 12$ and $00 ≤ mm, ss ≤ 59$

## Constraints
All input times are vaild

## Output Format
Convert and print the given time in $24-$hour format, where $00 ≤ hh ≤ 23$.

# Input
```
07:05:45PM
```

# Output
```
19:05:45
```

# Dev
```Java
import java.io.*;
import java.math.*;
import java.text.*;
import java.util.*;
import java.util.regex.*;

public class Solution {

    /*
     * Complete the timeConversion function below.
     */
    static String timeConversion(String s) {

        // time split hh mm ss
        String[] timeArr = s.split(":");
        int hour = Integer.parseInt(timeArr[0]) + 12;

        // check 'PM' or 'AM'
        if (timeArr[2].contains("PM")) {    

            if (hour == 24) timeArr[0] = "12";
            else timeArr[0] = Integer.toString(hour);
        } else {

            if (hour == 24) timeArr[0] = "00";
        }

        // delete text 'PM' or 'AM'
        timeArr[2] = timeArr[2].substring(0, 2);

        // return conversion time
        return timeArr[0] + ":" + timeArr[1] + ":" + timeArr[2];
    }

    private static final Scanner scan = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bw = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String s = scan.nextLine();

        String result = timeConversion(s);

        bw.write(result);
        bw.newLine();

        bw.close();
    }
}
```


# Conclusion
코드가 조금 지저분해보여서 다시 한번 정리해봐야할 필요성이 있음
