## 'This' Keyword
### Global 'This'
- `This` is attached to the global object if not in a declared object
  - In the case of the browser, this is the `window` object
- In `"Strict Mode"` (ES5), `this` is undefined unless inside a declared object (no access to global `this`)

### 'This' and declared objects (Implicit/Object)
- Implicit 'this' will always be the closest parent object
```
var person = {
  firstName: 'Miller',
  sayHello: function(){
    return 'Hi ' + this.firstName
  },
  determineContext: function(){
    return this === person
  }
}
```
`person.sayHi()` -> "Hi Miller"
`person.determineContext()` -> true

**Nested Objects**
```
var person = {
  firstName: "Miller",
  sayHi: function() {
    return "Hi " + this.firstName
  },
  determineContext: function() {
    return this === person
  }
  dog: {
    sayHello: function() {
      return "Hello " + this.firstName
    },
    determineContext: function() {
      return this === person
    }
  }
}
```
`person.sayHi()` -> "Hi Miller"
`person.determineContext()` -> true
`person.dog.sayHello()` -> "Hello undefined"
`person.dog.determineContext()` -> false

### Explicit Binding
- Choose what we want the context of 'this' to be using `call`, `apply`, or `bind`
  - Can **only** be used on functions
- `call` and `apply` immediately invoke the function they are bound to
- `bind` will make a new function definition with the value of 'this' explicitly determined (not invoked immediately)
```
var person = {
  firstName: "Miller",
  sayHi: function() {
    return "Hi " + this.firstName
  },
  determineContext: function() {
    return this === person
  }
  dog: {
    sayHello: function() {
      return "Hello " + this.firstName
    },
    determineContext: function() {
      return this === person
    }
  }
}
```
**Using Call Examples**
`person.sayHi()` -> "Hi Miller"
`person.determineContext()` -> true
`person.dog.sayHello().call(person)` -> "Hello Miller"
`person.dog.determineContext.call(person)` -> true

```
var sara = {
  firstName: "Sara",
  sayHi: function(){
    return "Hi " + this.firstName
  }
}
var miller = {
  firstName: "Miller",
  sayHi: function(){ // Duplication is bad :(
    return "Hi " + this.firstName
  }
}
```
`sara.sayHi()` -> Hi Sara
`miller.sayHi()` -> Hi Miller
-> Fix the duplication <-
`person.sayHi()` -> "Hi Miller"
`person.determineContext()` -> true
`person.dog.sayHello().call(person)` -> "Hello Miller"
`person.dog.determineContext.call(person)` -> true

```
var sara = {
  firstName: "Sara",
  sayHi: function(){
    return "Hi " + this.firstName
  }
}
var miller = {
  firstName: "Miller",
}
```
`sara.sayHi()` -> Hi Sara
`sara.sayHi.call(miller)` -> Hi Miller
- "Borrow the sayHi function from `sara`"

**Using Apply**
- Almost identical to `call` - except with parameters!
```
var sara = {
  firstName: "Sara",
  sayHi: function(){
    return "Hi " + this.firstName
  },
  addNumbers: function(){
    return this.firstName + " just calculated " + (a+b+c)
  }
}
var miller = {
  firstName: "Miller",
}
```
`sara.sayHi.apply(miller)` -> Hi Miller
`sara.addNumbers.call(miller,1,2,3)` -> Miller just calculated 6
`sara.addNumbers.apply(miller, [1,2,3])` -> Miller just calculated 6

**Call vs Apply**
`Call(thisArg, a, b, c, ...)`
`Apply(thisArg, [a, b, c, ...])`

**Bind**
- *Remember:* Unlike `call` and `apply`, `bind` does not invoke the function it is attached to right away
- Use `bind`  on functions that will be called at a later point
```
var sara = {
  firstName: "Sara",
  sayHi: function(){
    return "Hi " + this.firstName
  },
  addNumbers: function(){
    return this.firstName + " just calculated " + (a+b+c)
  }
}
var miller = {
  firstName: "Miller",
}
```
```
var millerCalc = sara.addNumbers.bind(miller, 2, 3, 4)
millerCalc() // Miller just calculated 9
```
With bind, all arguments **do not** need to be determined 'up front':
```
var millerCalc = sara.addNumbers.bind(miller, 1, 2)
millerCalc(3) // Miller just calculated 6
```

**Bind in the Wild**
```
var miller = {
  firstName: "Miller",
  sayHi: function(){
    setTimeout(function(){
      console.log("Hi " + this.firstName)
      }, 5000)
  }
}
```
`miller.sayHi()` -> Hi undefined *(5 seconds later)*
- `setTimeout` exists in the `global` object (often the `window` object), meaning `firstName` is undefined
```
var miller = {
  firstName: "Miller",
  sayHi: function(){
    setTimeout(function(){
      console.log("Hi " + this.firstName)
      }.bind(this), 5000)
  }
}
```
`miller.sayHi()` -> Hi Miller *(5 seconds later)*

### The 'new' Keyword
- The context of the keyword `this` can be set by using the `new` keyword (among other things...)

### Recap
- `This` is a reserved keyword in Javascript, whose value is determined at execution
- It is either set using the **global context**, **object binding**, **explicit binding**, or the `new` keyword

## OOP in Javascript
### Constructor functions
- Convention - Capitalize first letter of constructor function name
```
function House(bedrooms, bathrooms, numSqFt){
  this.bedrooms = bedrooms;
  this.bathrooms = bathrooms;
  this.numSqFt = numSqFt;
}
```
`var newHouse = House(4, 2, 1000);``
`console.log(newHouse)` -> undefined
- Why?
  - `this` is not explicitly bound to an object, and remains as a reference to the global `this`

### The 'new' keyword
- Must be used with a function
```
function House(bedrooms, bathrooms, numSqFt){
  this.bedrooms = bedrooms;
  this.bathrooms = bathrooms;
  this.numSqFt = numSqFt;
}
```
`var newHouse = new House(4, 2, 1000);`
`firstHouse.bedrooms` -> 4

- What does `new` do?
  - First creates an empty object
  - Sets the keyword `this` to that empty object
  - Adds the line `return this` to the end of the function that follows it
  - Adds a property onto the empty object called `__proto__` (aka 'dunderproto') which links the prototype object on the constructor function to the empty object

```
function Dog(name, age){
  this.name = name;
  this.age = age;
  this.bark = function(){
    console.log(`${this.name} just barked!`)
  };
}
```
`var fido = new Dog('Fido', 2);`
`fido.bark();` -> Fido just barked!

### Multiple Constructors
```
function Car(make, model, year){
  this.make = make;
  this.model = model;
  this.year = year;
  // Can set preset property values as well
  this.numWheels = 4;
}
```
```
function Motorcycle(make, model, year){
  Car.call(this, make, model, year);
  this.numWheels = 2;
}
// #### OR ####
function Motorcycle(make, model, year){
  Car.apply(this, [make, model, year]);
  this.numWheels = 2;
}
// #### OR ####
function Motorcycle(make, model, year){
  Car.apply(this, arguments);
  this.numWheels = 2;
}
```
- The `arguments` property can be used to place all arguments passed into a function into an array

### Recap
- Use constructor functions and `new` to mimic classes and instances
- Mimic inheritance between constructor functions using `call` or `apply`

## Prototypes
- Every constructor function has a property called `prototype`, which is an object
- Every prototype object has a property called `constructor` which points back to the constructor function
```
function Person(name, age){
  this.name = name;
  this.age = age;
}
var miller = new Person('Miller', 22);
```
`miller.__proto__ === Person.prototype` -> true

## Prototype Chain
- Methods and properties are first searched for in the object itself
  - If the method or property is not found, its `__proto__` property is searched
  - If that `__proto__` property does not have the property or object, its `__proto__` is then searched
  - This is called scaling the **prototype chain**
- The `prototype` property is shared among all instances of a constructor function.  This means that properties and methods that are the same among all instances should be placed in the `prototype` object of their shared constructor function (most efficient, as this prevent duplicated code)

**Example**
```
function Vehicle(make, model, year){
  this.make = make;
  this.model = model;
  this.year = year;
  this.isRunning = false;
}

Vehicle.prototype.turnOn = function(){
    this.isRunning = true;
  };

Vehicle.prototype.turnOff = function(){
    this.isRunning = false;
  };

Vehicle.prototype.honk = function(){
    if(this.isRunning){
      return "beep";
    }
  };
```
`var carOne = new Vehicle('ford', 'explorer', '1996');`
`console.log(carOne.honk());` -> returns nothing
`carOne.turnOn();`
`console.log(carOne.honk());` - beep

## Closures
A **closure** is a function that makes use of variables defined in outer functions that have previously returned

```
function outer(a){
  return function inner(b){
    // The inner function is making use of the
    // variable 'a' which was defined in an outer
    // function called "outer" and by the time this
    // is called, that outer function has returned.
    // This function called "inner" is a closure
    return a + b;
  }
}
```
`outer(5)(5);` -> 10

**Closures** != **Nested Functions**

### Private Variables
```
function counter(){
  var count = 0;
  return function(){
    return ++count;
  }
}

counterOne = counter();
counterOne(); // 1
counterOne(); // 2

counterTwo = counter();
counterTwo(); // 1

counterOne() // 3 (this is not affected by counterTwo)

count / ReferenceError: count is not defined (because it's private)
```
