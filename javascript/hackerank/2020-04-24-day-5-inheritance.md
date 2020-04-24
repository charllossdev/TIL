# Inheritance
In this challenge, we practive implementing inheritance and use Javascript prototypes to add a new method to an existing prototype.
Check out the attached Classes tutorial to refresh what we've learned about these topics.

## Task
We provide the implementanion for a Ractangle class in the editor. Perform the following tasks:
  1. Add an are method to Rectangle prototype.
  2. Create a Square class that satisfiles the follwing
      + It is a subclass of Rectangle.
      + It contains a constructor and no other methods.
      + It can use the Ractangle class area method to print the area of a Square object.

Locked code in the editor tests the class and method implementations and prints the area values to STDOUT.

# Dev

```js

class Rectangle {
    constructor(w, h) {
        this.w = w;
        this.h = h;
    }
}

/*
 *  Write code that adds an 'area' method to the Rectangle class' prototype
 */
Rectangle.prototype.area = function() {
    return this.w * this.h;
}
/*
 * Create a Square class that inherits from Rectangle and implement its class constructor
 */
class Square extends Rectangle {
    constructor(w) {
        super(w, w);
    }
}


if (JSON.stringify(Object.getOwnPropertyNames(Square.prototype)) === JSON.stringify([ 'constructor' ])) {
    const rec = new Rectangle(3, 4);
    const sqr = new Square(3);

    console.log(rec.area());
    console.log(sqr.area());
} else {
    console.log(-1);
    console.log(-1);
}
```


# Conclusion

ES6 Javascript 문법이 자바랑 비슷해 지면서 클래스 관련 코드들이 가독성이 좋아진거 같아 배우고, 사용하기 훨신 편하게 느껴졌습니다.
