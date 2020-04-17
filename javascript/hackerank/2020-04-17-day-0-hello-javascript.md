# Hello

## Overview: 10 Days of JavaScript
This series focuses on learning and practicing JavaScript. Each challenge comes with a tutorial article, and you can view these articles by clicking either the Topics tab along the top or the article icon in the right-hand menu.

## Objective

In this challenge, we review some basic concepts that will get you started with this series. Check out the tutorial to learn more about JavaScript's lexical structure.

## Task

A greeting function is provided for ou in the editor below. It has one parameter, $parameter Variable$.
Perform the following tasks to complete this challenge:

1. Use $console.log()$ to print 'Hello, World!' on a new line in the console, which is also known as stdout or standard output. The code for this portion of the task is already provided in the editor.
2. Use $console.log()$ to print the contents of $parameter Variable$ ($i.e:$ the argument passed to main). You've got this!

# Input Format

|Data Type | Parameter | Description |
|:--|:--|:--|
|string | $parameter Variable$ | A single line of text containing one or more space-separated words. |


# Outpur Format
print the following two lines of output:

1. On the first line, print 'Hello, World!' (this is provided for you in the editor)
2. On the second line, print the contents of $parameter Variable$.

# Input

```js
Welcome to 10 Days of Javascript!
```

# Output

```js
Hello, World!
Welcome to 10 Days of Javascript!
```

# Explanation
We print two lines of output:

1. We printed the literal string $Hello, World!$ using the code provided in the Editor
2. the value of $parameter Variable$ passed to our main function in this Sample case was <i>'Welcome to 10 Days of Javascript!'</i>. We then passed our variable to console.log, which printed the contents of $parameter Variable$.

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

/**
*   A line of code that prints "Hello, World!" on a new line is provided in the editor.
*   Write a second line of code that prints the contents of 'parameterVariable' on a new line.
*
*	Parameter:
*   parameterVariable - A string of text.
**/
function greeting(parameterVariable) {
    // This line prints 'Hello, World!' to the console:
    console.log('Hello, World!');

    // Write a line of code that prints parameterVariable to stdout using console.log:
    console.log(parameterVariable);

}

```
