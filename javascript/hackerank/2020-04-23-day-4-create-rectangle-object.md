
# Create a Rectangle Object

Complete the function in the editor. It has two parameters: $a$ and $b$. It must return an object modeling a rectangle that has the following properties:

* $length$: This value is equal to $a$.
* $width$: This value is equal to $b$.
* $perimeter$: This value is equal to $2*(a + b)$
* $area$: This value is equal to $a * b$

Note: The names of the object's properties must be spelled correctly to pass this challenge.

## Input Format

The first line contains an integer denoting $a$.
The second line contains an integer denoting $b$.

## Constraints

$ 1 < a, b < 100

## Output Format

Return a object that has the properties specified above. Locked code in the editor prints the returned object's $length$, $width$, , and  to STDOUT.

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
 * Complete the Rectangle function
 */
function Rectangle(a, b) {

    const rectangle = {
        length: a,
        width: b,
        perimeter: 2*(a + b),
        area: (a * b)
    }

    return rectangle;
}

function main() {
    const a = +(readLine());
    const b = +(readLine());

    const rec = new Rectangle(a, b);

    console.log(rec.length);
    console.log(rec.width);
    console.log(rec.perimeter);
    console.log(rec.area);
}
```


# Study

### 1. Use a Constructor Function;

```js
function Rectangle(a, b) {
    return {
        get length() { return a; },
        get width() { return b; },
        get perimeter() { return 2 * (a + b); },
        get area() { return a * b; }
    }
}
```

```js
function Rectangle(a, b) {
    // Set the object's properties
    this.length = a;
    this.width = b;
    this.perimeter = 2 * a + 2 * b;
    this.area = a * b;

    // This isn't necessary, but it prevents new properties from being added
    // It also prevents the properties we've already set from being modified
    Object.freeze(this);
}
```

```js
function Rectangle(a, b) {
    Object.defineProperty(this, 'length', {
        get: () => {
            return a;
        }
    });

    Object.defineProperty(this, 'width', {
        get: () => {
            return b;
        }
    });

    Object.defineProperty(this, 'perimeter', {
        get: () => {
            return 2 * (a + b);
        }
    });

    Object.defineProperty(this, 'area', {
        get: () => {
            return a * b;
        }
    });
}
```

2. Use an Object Initializer / Object Literal

```js
let myObject = {
    property1: 1,
    property2: 2
    // ... and so on
}
console.log(myObject)
// This prints:
// { property1: 1, property2: 2 }
```
```js
function Rectangle(a, b) {
    const rectangle = {
        length: a,
        width: b,
        perimeter: 2 * (a + b),
        area: a * b
    };

    return rectangle;
}
```
