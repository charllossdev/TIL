# Classes

Create a Polygon class that has the following properties:

* A constructor that takes an array of integer values describing the lengths of the polygon's sides.
* A perimeter() method that returns the polygon's perimeter.

Locked code in the editor tests the Polygon constructor and the perimeter method.
Note: The perimeter method must be lowercase and spelled correctly.

## Input Format

There is no input for this challenge.

## Output Format

The perimeter method must return the polygon's perimeter using the side length array passed to the constructor.

# Dev

```js
/*
 * Implement a Polygon class with the following properties:
 * 1. A constructor that takes an array of integer side lengths.
 * 2. A 'perimeter' method that returns the sum of the Polygon's side lengths.
 */

class Polygon {
    constructor(arr) {
        this.arr = arr;
    }

    perimeter() {
        let sum = 0;

        for (const i in this.arr) {
            sum += this.arr[i];
        }

        return sum;
    }

}

const rectangle = new Polygon([10, 20, 10, 20]);
const square = new Polygon([10, 10, 10, 10]);
const pentagon = new Polygon([10, 20, 30, 40, 43]);

console.log(rectangle.perimeter());
console.log(square.perimeter());
console.log(pentagon.perimeter());
```


# Classes in Javascript


# Function Classes
we'll discuss some of the ways we can use functions to simulate the behavior of classes.


### Using Functions

1. Define a normal Javascript function.
2. Create an object by using the Keywords.
3. Define properties and methods for a created object using the this keyword.

```js
'use strict';

function Fruit (type) {
    this.type = type;
    this.color = 'unknown';
    this.getInformation = getFruitInformation;
}

function getFruitInformation() {
    return 'This ' + this.type + ' is ' + this.color + '.';
}

let lime = new Fruit('Mexican lime');
console.log(lime.getInformation());

lime.color = 'green';
console.log(lime.getInformation());
```


### The Prototype Property

he drawback of internally defining the getInformation function is that it recreates that function every time we create a new Fruit object. Fortunately, every function in JavaScript has something called a prototype property, which is empty by default. We can think of a function's prototype as an object blueprint or paradigm; when we add methods and properties to the prototype, they are accessible to all instances of that function. This is especially useful for inheritance (discussed below).

We can add a function to our constructor function's prototype like so:

```js
'use strict';

function Fruit (type) {
    this.type = type;
    this.color = 'unknown';
}

Fruit.prototype.getInformation = function() {
    return 'This ' + this.type + ' is ' + this.color + '.';
}

let lime = new Fruit('Mexican lime');
console.log(lime.getInformation());

lime.color = 'green';
console.log(lime.getInformation());
```

### Using Object Literals
We can use object literals to define an object's properties and functions by initializing a variable with a comma-separated list of property-value pairs enclosed in curly braces.

```js
'use strict';

let lime = {
    type: 'Mexican lime',
    color: 'green',
    getInformation: function() {
        return 'This ' + this.type + ' is ' + this.color + '.';
    }
}

console.log(lime.getInformation());

lime.color = 'yellow';
console.log(lime.getInformation());
```

### Singleton Class Using a Function

A singleton class is a design pattern that restricts a class to a single instance. When we assign the value of new function(){...} to a variable, the following happens:

1. We define an anonymous constructor function.
1. We invoke the anonymous constructor function with the new keyword.

```js
'use strict';

let lime = new function() {
    this.type = 'Mexican lime';
    this.color = 'green';
    this.getInformation = function() {
        return 'This ' + this.type + ' is ' + this.color + '.';
    };
}

console.log(lime.getInformation());

lime.color = 'yellow';
console.log(lime.getInformation());
```

# Classes

JavaScript classes, introduced in ECMAScript 6, are essentially syntactic sugar over JavaScript's existing prototype-based inheritance that don't actually introduce a new object-oriented inheritance model. This syntax is a means of more simply and clearly creating objects and deal with inheritance.

### Class Declartions

One way to define a class is using a class declaration. To declare a class, we use the class keyword and follow it with the class' name. Ideally, we always write class names in TitleCase.

```js
class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
}

let p = new Polygon(1, 2);
console.log('Polygon p:', p);
```

```js
try {
    let p = new Polygon(1, 2);
    console.log('Polygon p:', p);
}
catch (exception) {
    console.log(exception.name + ': ' + exception.message);
}
class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
}

p = new Polygon(1, 2);
console.log('Polygon p:', p);
```

### Class Expression

Class expressions are another way to define a class, and they can be either named or unnamed. The name given to a named class expression is local to the class body.

```js
let Polygon = class {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
};

console.log('Polygon:', Polygon);
let p = new Polygon(1, 2);
console.log('p:', p);
```

### Named Class Expression

```js
let Polygon = class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
};

console.log('Polygon:', Polygon);
let p = new Polygon(1, 2);
console.log('p:', p);
```

# The Constructor Method

* The constructor method is a special method we use to create and initialize objects of a class.
* A class can only have one special method with the name constructor, and attempting to write a class containing more than one constructor method will throw a SyntaxError.
* To implement inheritance, we can use the super keyword in a constructor to call a parent class constructor.

### Prototype Methods

```js
'use strict';

class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    getArea() {
        return this.height * this.width;
    }
}

const square = new Polygon(10, 10);

console.log(square.getArea());
```

# Static Methods

tatic methods are methods relevant to all instances of a class — not just any one instance. These methods receive information from their arguments and not a class instance, which allows us to invoke a class' static methods without creating an instance of the class. In fact, we actually can't call a static method on an instantiated class object (attempting to do so throws a TypeError).

We define a class' static methods using the static keyword. We typically use these methods to create utility functions for applications, as they can't be called on class objects.

```js
'use strict';

class Point {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
    static distance(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}

const p1 = new Point(5, 5);
const p2 = new Point(10, 10);

// The correct way to call a static method
console.log(Point.distance(p1, p2));

// Attempt to call a static method on an instance of the class
try {
    console.log(p1.distance(p1, p2));
}
catch (exception) {
    console.log(exception.name + ': ' + exception.message);
}
```

# Subclassing with the $extends$ Keywords

We use the extends keyword in class declarations or class expressions to create a child class (i.e., subclass).

```js

'use strict';

class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    speak() {
        console.log(this.name, 'barks.');
    }
}

let spot = new Dog('Spot');
spot.speak();

spot = new Animal('Spot');
spot.speak();
```

> Spot barks.
> Spot speaks.

# Superclass Calls Using the $super$ Keyword
We use the super keyword to call functions on an object's parent.

```js
'use strict';

class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    speak() {
        super.speak();
        console.log(this.name, 'barks.');
    }
}

let spot = new Dog('Spot');
spot.speak();
```

> Spot speaks.
> Spot barks.


# Extending an Object
The ability to extend multiple classes from the same superclass (or model multiple object types after the same prototype) is powerful because it provides us with certain implied guarantees about the basic functionality of the subclasses; as extensions of the parent class, subclasses are guaranteed to (at minimum) have the superclass' fields, methods, and functions.


```js
'use strict';

class Animal {
    constructor(name) {
        this.animalType = 'Animal'
        this.name = name;
    }
    type() {
        console.log(this.name, 'is type', this.animalType);
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    constructor(name, collarColor) {
        super(name);
        this.animalType = 'Dog';
        this.collarColor = collarColor;
    }
    speak() {
        console.log(this.name, 'barks.');
    }
    collar() {
        console.log(this.name, 'has a', this.collarColor, 'collar.');
    }
}

let spot = new Dog('Spot', 'red');
spot.type();
spot.speak();
spot.collar();

// Because the Animal constructor only expects one argument,
// only the first value passed to it is used
spot = new Animal('Spot', 'white');
spot.type();
spot.speak();
try {
    spot.collar();
}
catch (exception) {
    console.log(exception.name + ': ' + exception.message
    + ' (collar is a method of Dog, not Animal).');
}
```

>Spot is type Dog
Spot barks.
Spot has a red collar.
Spot is type Animal
Spot speaks.
TypeError: spot.collar is not a function (collar is a method of Dog, not Animal).
