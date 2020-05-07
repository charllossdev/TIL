# Javascript Dates

Given a date string, $dataString$, in the format MM/DD/YYYY, find and return the day name for that date. Each day name must be one of the following strings: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, or Saturday. For example, the day name for the date 12/07/2016 is Wednesday.

### Input Format

Locked stub code in the editor reads the following input from stdin:
The first line contains an integer, $d$, denoting the number of dates to check.
Each line $i$ of the $d$ subsequent lines contains a date in MM/DD/YYYY format; each date denotes some $dataString$ that is passed to the function.

### Constraints

It is guaranteed that the input only consists of valid dates.

### Output Format

The function must return a string denoting the day of the week corresponding to the date denoted by $dataString$.

# Sample Input 0
```
2
10/11/2009
11/10/2010
```
# Sample Output 0
```
Sunday
Wednesday
```

# Dev
```js
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', inputStdin => {
    inputString += inputStdin;
});

process.stdin.on('end', _ => {
    inputString = inputString.trim().split('\n').map(string => {
        return string.trim();
    });

    main();    
});

function readLine() {
    return inputString[currentLine++];
}

// The days of the week are: "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"
function getDayName(dateString) {
    let dayName = new Date(dateString).toString().split(" ")[0];
    // Write your code here
    switch(dayName) {
        case "Sun":
            dayName = "Sunday";
            break;
         case "Mon":
            dayName = "Monday";
            break;
        case "Tue":
            dayName = "Tuesday";
            break;
        case "Wed":
            dayName = "Wednesday";
            break;
        case "Thu":
            dayName = "Thursday";
            break;
        case "Fri":
            dayName = "Friday";
            break;
        default:
            dayName = "Saturday";
            break;           
    }

    return dayName;
}


function main() {
    const d = +(readLine());

    for (let i = 0; i < d; i++) {
        const date = readLine();

        console.log(getDayName(date));
    }
}
```


# Dates in Javascript

A Javascript date instance represents a single moment in time based on the number of milliseconds elapsed since $1$ $January,$ $1970 UTC$

### Create Date Instance

There are four constructors we can use to create a $Date$ $Object$, defined below.

1. Using $new \ Date()$
The default constructor creates a Javascript Date object for the current date and time(according to your system settings.)

2. Using $new \ Date(value)$
This constructor has a parameter, $value$, which is an integer representing the number of milliseconds elapsed since $1 \ January \ 1970 \ 00:00:00 \ UTC$ (this is a Unix Epoch, though you should keep in mind that most Unix timestamp functions count in seconds).

3. Using $new \  Date(dateString)$
This constructor has a parameter, $dateString$, which is a String describing a date. The $dateString$ must be in a format recognized by the Date.parse() function, such as MM/DD/YYYY or Month Day, Year. For example, 01/01/1980 and Jan 1, 1980 are both strings that can be successfully parsed using the parse function.

4. Using new Date(year, month, day, hour, minutes, seconds, milliseconds)
This constructor has the following parameters:
* year: An integer denoting the calendar year. Values from 0 through 99 map to the years $1900$ through $1999$.
* month: A one or two digit integer denoting the zero-indexed month. This means that  0 denotes January and 11 denotes December.
* day: Optional. An integer denoting the specific day number within the calendar month.
* hour: Optional. An integer denoting the hour of the day.
* minutes: Optional. An integer denoting the minute segment of a time.
* seconds: Optional. An integer denoting the second segment of a time.
* milliseconds: Optional. An integer denoting the millisecond segment of a time.

### Date $get$ Methods
1. Date.getTime()
Get the time in milliseconds elapsed since $January \ 1, 1970$.

2. Date.getFullYear()
Get the four-digit year ($yyyy$).

3. Date.getMonth()
Get the Date object's month as a zero-indexed number (0-11).

4. Date.getDate()
Get the Date object's day as a number (1-31).

5. Date.getDay()
Get the Date object's weekday as a number (0-6).

6. Date.getHours()
Get the Date object's hour (0-23).

7. Date.getMinutes()
Get the Date object's minutes (0-59)

8. Date.getSeconds()
Get the Date object's seconds (0-59).

9. Date.getMilliseconds()
Get the Date object's milliseconds (0-999).
