Features covered in this overview:
- [arrow functions](arrows/arrow_func.md)
- [let and const](#let-and-const)
- [destructuring](#destructuring)
- [default + rest + spread](#default--rest--spread)
- [enhanced object literals](#enhanced-object-literals)
- [iterators + for..of](#iterators--forof)
- [generators](#generators)
- [classes](#classes)
- [modules](#modules)
- [new built-in objects](#new-built-in-objects)
- [template strings](#template-strings)

### `let` and `const`

> `let` declares a block scope local variable

```JavaScript
let f = (value) => {
	let factor = 2;
	let delta = 1;

	if(value > 2) {
		let delta = 4 // different variable!
		factor += delta;
	} else {
		let factor = 5;	// different variable!
		delta += factor;
	}

	return result * factor + delta;
};
```

`let` will hoist the variable to the top of the block.
However, referencing the variable in the block before the variable declaration results in a `ReferenceError`.
This is *called temporal dead zone* (TDZ);
```JavaScript
function do_something() {
  console.log(foo); // ReferenceError
  let foo = 2;
}
```

> `let` can be used to declare variables in the scope of the loops

```JavaScript
var i = 0;
for (let i = i; i < 10; i++) {
  console.log(i);
}
```

> `const` is single-assignment.

```JavaScript
const x = 1;
x = 2;
console.log(x); // prints 1
```

> `let` does not make the value it holds immutable, just that the variable identifier cannot be reassigned.

```JavaScript
const y = {
  count: 1,
};

y.count++;
console.log(y.count);	// prints 2
```
An initializer for a constant is required.


### Destructuring

### Default + Rest + Spread

### Enhanced Object Literals

### Iterators + For..Of

#### Array
```JavaScript
let iterable = [1, 2, 3];

for (let value of iterable) {
  console.log(value);
}
// 1
// 2
// 3
```

#### String
```JavaScript
let iterable = "boo";

for (let value of iterable) {
  console.log(value);
}
// "b"
// "o"
// "o"
```


#### Difference between for...of and for...in
```JavaScript
let iterable = [3, 5, 7];
iterable.foo = "hello";

for (let i in iterable) {
  console.log(i); // logs 0, 1, 2, "foo"
}

for (let i of iterable) {
  console.log(i); // logs 3, 5, 7
}
```
Also about Symbols here



### Generators

### Classes
> Syntactical sugar over JavaScript's existing prototype-based inheritance.

> Does not introduce a new object-oriented inheritance model.

```JavaScript
class Person {
  constructor (name) {
    this._name = name;
  }

  // property definiton shorthand
  get name() {
    return this._name;
  }
  set name(value) {
    this._name = value;
  }

  // note that this is a prototype method
  doWork() {
    return this.name + ' is working';
  }
}
```

> Sub classing with `extends`

```JavaScript
class Employee extends Person {
  constructor (name, title) {
    super(name);	// calling base class constructor

    this._title = title;
  }

  get title() {
    return this._title;
  }

  doWork() {
    return super.doWork() + ' hard';	// calling base class method
  }
}

let greatPerson = new Person("Bob Ross");
let humblePerson = new Employee("Oleg", "developer");

for(let person of [greatPerson, humblePerson]) {
  console.log(person.doWork());
}
```

> Can also have static methods

```JavaScript
class Point {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }

    static distance(a, b) {
        let dx = a.x - b.x;
        let dy = a.y - b.y;

        return Math.sqrt(dx*dx + dy*dy);
    }
}
let p1 = new Point(5, 5);
let p2 = new Point(10, 10);

// p1.distance is not defined.

console.log(Point.distance(p1, p2));
```

###### [TODO] Subclassable Built-ins


### Modules
Aslo about module loaders here

### New built-in objects
Map, Set, WeakMap, WeakSet, Promise, Proxy

### Template strings

