# Template Literals

### Task

The code in the editor has a tagged template literal that passes the area and perimeter of a rectangle to a tag function named sides. Recall that the first argument of a tag function is an array of string literals from the template, and the subsequent values are the template's respective expression values.

Complete the function in the editor so that it does the following:

1. Finds the inital values of $s1$ and $s2$ by plugging the area and perimeter values into the formula:

* $ s = \frac{P \pm \sqrt{P^2 - 16 \cdot A}}{4}$
where $A$ is the rectangles's area and $P$ is its perimeter.

2. Creates an array consisting of $s1$ and $s2$ and sorts it in ascending order.
3. Returns the sorted array.

### Input Format

The first line contains an integer denoting $s1$.
The second line contains an integer denoting $s2$.

### Constraints

* $ 1 \le s1, s2 \le 100 $

### Output Format
Return an array consisting of $s1$ and $s2$ sorted in ascending order.

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

/*
 * Determine the original side lengths and return an array:
 * - The first element is the length of the shorter side
 * - The second element is the length of the longer side
 *
 * Parameter(s):
 * literals: The tagged template literal's array of strings.
 * expressions: The tagged template literal's array of expression values (i.e., [area, perimeter]).
 */
function sides(literals, ...expressions) {
    const A = expressions[0];
    const P = expressions[1];

    const s1 = (P + Math.sqrt(Math.pow(P, 2) - 16 * A))/4;
    const s2 = (P - Math.sqrt(Math.pow(P, 2) - 16 * A))/4;

    return [s1, s2].sort();
}


function main() {
    let s1 = +(readLine());
    let s2 = +(readLine());

    [s1, s2] = [s1, s2].sort();

    const [x, y] = sides`The area is: ${s1 * s2}.\nThe perimeter is: ${2 * (s1 + s2)}.`;

    console.log((s1 === x) ? s1 : -1);
    console.log((s2 === y) ? s2 : -1);
}
```





# Javascript: Template Literals

### Template literals
Template literals(formerly known as template strings) are string literals that allow for embedded expressions.
We typically use them to express strings spanning multiple lines or for string interpolation, which essentially allows us to create a template with one or more placeholders for inserting variable text at a later time.

While traditional strings are wrapped in single or double quotes, template literals are wrapped in backtick (`'`) characters. A template literal can contain placeholders, which are preceded by a dollar sign (`$`) and wrapped in curly braces ({}). For example, in the template literal `${expression}`, the $expreesion$ text between the placeholders is passed to a function. The default function simply concatenates the template literal's parts into a single string.

Any time we see an expression preceding a template literal, we call the expression a tag and the template string a tagged template literal. In these instances, we call the tag expression (typically a function) with the processed template literal, which we can then manipulate before outputting the final string.


### Expression Interpolation

Print a Line Using Normal Strings
```js
const a = 2;
const b = 3;

console.log(
  'The sum of a and b is' + (a + b) + '.\n'
  + 'The product of a and b is' + (a * b) + '.'
);
```

Print a Line Using Template Literals

```js
const a = 2;
const b = 3;

console.log('The sum of a and b is ${a + b}.
The product of a and b is ${a * b}.');
```

Result
> The sum of a and b is 5.
The product of a and b is 6.


### Tagged template Literals
Tagged template literals allow us to use a function to modify the output of a template literal.
in this construct:

1. The first argument contains an array of string literals.
2. The subsequently processed arguments are the  values of the substitution expressions.

After processing all the arguments, the function returns the manipulated string.

```js
var a = 5;
var b = 10;

function foo(strings, ...values) {
    console.log("." + strings[0] + ".");
    console.log("." + strings[1] + ".");
    console.log("." + strings[2] + ".");
    console.log("." + strings[3] + ".");
    console.log(values[0]);
    console.log(values[1]);
    console.log(values[2]);
}

```

```js
foo 'sum  ${a + b}
Product   ${a * b}
Division  ${b / a}';
```
Result

> .Sum .
.
Product .
.
Division .
..
15
50
2

```js
foo 'sum  ${a + b} Product ${a * b} Division  ${b / a}';
```

Result
> .Sum .
.Product .
.Division .
..
6
5
0.2

Now we can see that, the total number of string literals is one more than the number of total cooked expressions. The first string literal is the string before the first cooked expression, the last string literal is the string after the last cooked expression and other literals are in between the cooked expressions.

We can also return from tagged templates:
```js
var a = 5;
var b = 10;

function foo(strings, ...values) {
    let a = values[0];
    let b = values[1];

    return `Sum ${a + b}
Product ${a * b}
Division ${b / a}`;
}

console.log(foo`Num1 ${a + 10}
Num2 ${b * 2}
Num3 ${b / a}`);
```
Result
> Sum 35
Product 300
Division 1.3333333333333333
