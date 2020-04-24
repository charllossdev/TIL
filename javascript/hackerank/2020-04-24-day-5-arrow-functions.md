# Arrow Functions

### Task

Complete the function in the editor. It has one parameter: an array, $nums$. It must iterate through the array performing one of the following actions on each element:

* If the element is even, multiply the element by 2.
* If the element is odd, multiply the element by 3.
The function must then return the modified array.


### Input Format
The first line contains an integer, $n$, denothing the size of $nums$
The second line contains $n$ space-separated integers describing the respective elements of $nums$.

### Constraints
* $1 \le n \le 10$
* $1 \le nums \le 100$, where $nums$, is the $i^{th}$ element of $nums$.

### Output Format
Return the modified array where every even element is doubled and every odd elements is tripled.

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
 * Modify and return the array so that all even elements are doubled and all odd elements are tripled.
 *
 * Parameter(s):
 * nums: An array of numbers.
 */
function modifyArray(nums) {
    for (const i in nums) {
        (nums[i] % 2 === 0) ? nums[i] *= 2 : nums[i] *= 3;
    }

    return nums;
}


function main() {
    const n = +(readLine());
    const a = readLine().split(' ').map(Number);

    console.log(modifyArray(a).toString().split(',').join(' '));
}
```

# Arrow Functions in Javascript

### Arrow Functions
There expressions lexically bind the $this$ value while using less syntax than a typical function expression.
Arrow functions are always anonymous.

* Here are some basic examples of arrow function syntax:
  ```js
  (parameter) => {statements}
  parameter => {statements}
  parameter => expression
  parameter => {return expression}

  (param1, param2, ..., paramN) => {statements}
  (param1, param2, ..., paramN) => expression
  (param1, param2, ..., paramN) => {return expression}
  ```

* Let's look at some simple ways to apply this syntax:
  ```js
  'use strict';

  const makeArray = (...values) => { return values };
  console.log('Array:', makeArray(1, 2, 3, 4));
  console.log('Array:', makeArray(1, 2, 3, 4, 5, 6));

  const getSum = (a, b) => { return a + b };
  console.log('1 + 2 =', getSum(1, 2));

  const greeting = 'Hello, World.';
  const capitalize = (myString) => { return myString.toUpperCase() };
  console.log(greeting, '=>', capitalize(greeting));
  ```

### Using Arrow Functions
Let's look at some ways we can use arrow functions to make our code shorter.

* Sum the Elements of an Array
while we can certainly iterate over an array and sum each value, we can also use the reduce function.
  ```js
  'use strict';

  const arr = [1, 2, 3, 4, 5];

  // Basic function
  const sum = arr.reduce(function (a, b) {
      return a + b;
  }, 0);

  // Now, let's reduce the length of our code using an arrow function:
  const sum = arr.reduce((a, b) => { return a + b }, 0);

  // Let's further reduce it by getting rid of the return:
  const sum = arr.reduce((a, b) => a + b, 0);

  console.log('Array:', arr);
  console.log('Sum:', sum);
  ```
    + Result
      > Array: [ 1, 2, 3, 4, 5 ]
        Sum: 15


* Find the Length of Strings in an Array
Let's take an array of strings and use if to create a new array containing the respective lengths of its elements.
  ```js
  'use strict';

  const arr = ['first', 'second', 'third', 'fourth', 'fifth'];

  // Basic function
  const len = arr.map(function(s) { return s.length });

  // Now, let's reduce the length of our code using an arrow function:
  const len = arr.map(s => s.length);

  console.log('Array:', arr);
  console.log('Lengths:', len);
  ```
    + Result
      > Array: [ 'first', 'second', 'third', 'fourth', 'fifth' ]
        Lengths: [ 5, 6, 5, 6, 5 ]

* Find Array Elements Greater Than a Value
Let's find all the elements in an array that are greater than 3 and add them to a new array.
```js
'use strict';

const arr = [1, 2, 3, 4, 5];

// Basic function
const greaterThan3 = arr.filter(function(a) {
  return a > 3;
});

// Now, let's reduce the length of our code using an arrow function:
const greaterThan3 = arr.filter(a => a > 3);

console.log('Array', arr);
console.log('Elements greater Than 3: ', greaterThan3);
```
