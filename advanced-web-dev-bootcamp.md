### Curriculum Walkthrough
- CSS Animations
- CSS Flexbox
- *Special Project*
- Asynchronous Javascript
- AJAX
- Testing
- Advanced Array Methods
- Closures & `This`
- OOP with Javascript
- Creating your own APIs
- Single Page Apps with Node
- ES2015
- 'Guess the Password Refactor'
- ES2016 & ES2017
- D3 and the DOM
- D3 and Data
- SVG and D3
- Intermediate D3
- Advanced D3
- D3 Climate Dashboard
- Intro to React and JSX
- Create React App and Props
- React and State
- The Virtual DOM and React Events
- The Component Lifecycle
- React and Auth
- React Router
- React and Redux

### Learning Paths
- **The CSS Master**
  - CSS Animations
  - CSS Flexbox
- **Modern JS Guru**
  - Async JS
  - JS OOP
  - Closures and `This`
  - Advanced Array Methods
  - Testing with Jasmine
  - Mastering ES2015
  - Guess the Password Refactor
  - Mastering ES2015 Pt. 2
  - ES2016 & ES2017
- **D3 and SVG... Person**
- **Complete React Path**

### *Section 2:* CSS Animations: Transforms and Transitions
**Why animations matter**
- Add context
- Provide an 'air of professionalism' and credibility through polish

**Psuedoclasses**
- keyword added to a selector to define a special state of an element
- `:hover`
- `:focus`
- `:active`

**Transform**
- Move, warp, rotate, and scale elements
- `transform: `
  - `translateX()`
  - `translateY()`
  - `scale()`
  - `transform-origin()`
  - `rotate()`
- *NOTE:* To attach multiple transformations to an element, string them together:
  - `transform: rotate(45deg) translateX(50px);`
  - Otherwise, the *last* transformation will overwrite the first

**Vendor Prefixes**
- `-webkit-`
- `-moz-`
- `-ms-`
- `-o-`
- Use autoprefixers to generate browser compatible CSS
- autoprefixer.github.io

**Transitions**
- Specify transition for one state change
- 4 Transition properties:
  1. transition-duration
  2. transition-property
  3. transition-timing-function
  4. transition-delay

- Shorthand transitions:
  - `transition: <property> <duration> <timing-function> <delay>`

**CSS Animation Performance**
- 4 Highest (cheapest) performance animations
  - `Position`
  - `Scale`
  - `Rotate`
  - `Opacity`

### *Section 3:* CSS Animations: Keyframes
- Used to perform multiple state changes in an animation
```
<selector> {
  animation-name: <animation name>;
  animation-duration:
  animation-timing-function:
  animation-delay:
  animation-iteration-count:
}
@keyframes <animation name> {
  25% {
    ...
  }
  50% {
    ...
  }
  75% {
    ...
  }
  100% {
    ...
  }
}
```

**Common Keyframe Properties**
- `animation-name`
- `animation-duration`
- `animation-timing-function`
- `animation-delay`

**Less Common Properties**
- `animation-iteration-count`
- `animation-direction`
- `animation-fill-mode`
- `animation-play-state`

### *Section 4:* Advanced CSS: Layout With Flexbox
> "A more efficient way to lay out, align, and distribute space among items in a container (even if their size is unknown)"

**Container Properties**
- `flex-direction`
- `justify-content`
- `flex-wrap`
- `align-items`
- `align-content`

**Flex Item Properties**
- `order`
- `flex`
- `flex-grow`
- `flex-shrink`

`display: flex;`

**Flexbox Terminology**
- Flex container
- Flex item
- Main Axis
- Cross Axis

#### Container Properties
**flex-direction** - Defines the *main axis* and its *direction* (specify how items are placed in the flex container)

`flex-direction: row;`
- Default flex direction

`flex-direction: row-reverse;`
`flex-direction: column;`
`flex-direction: column-reverse;`

**flex-wrap**
- specify whether items are forced into a *single line* or can be wrapped into *multiple lines*

`flex-wrap: no-wrap`
- Default flex-wrap

`flex-wrap: wrap;`
`flex-wrap: wrap-reverse;`

**justify-content**
- Define how space is distributed between items in flex container *along the main axis*

`justify-content: flex-start`;
- default justify-content

`justify-content: flex-end`;
`justify-content: center`;
`justify-content: space-between`;
`justify-content: space-around`;

**align-items**
- Define how space is distributed between items in flex container *along the cross axis*

`align-items: stretch;`
- Default align-items

`align-items: flex-start;`
`align-items: flex-end;`
`align-items: center;`
`align-items: baseline;`

**align-content**
- Defines how space is distributed *between rows* in flex container *along the cross axis*

`align-content: stretch;`
- Default align-content

**CSS @media rule**
- used to define different style rules for different media types/devices
`@media screen and (max-width: 500px){}`

#### Flex Item Properties
**align-self**
- Override align-items on individual flex items
`flex-start`
`flex-end`
`stretch`
`center`

**order**
- specify the order used to lay out item in their flex container
- All items have a default order of 0;

**flex**
- define how a flex item will grow or shrink to fit the available space in a container
- *actually a shorthand property for 3 other properties:*
  - `flex-grow`
  - `flex-shrink`
  - `flex-basis`
`flex: <flex-grow> <flex-shrink> <flex-basis>`

**flex-basis**
- specifies the ideal size of a flex item *BEFORE* it's placed into a flex container

**flex-grow**
- Dictate how the unused space should be spread amongst flex items
- Determined by *ratios*
`flex-grow: 0;`
  - Default value

**flex-shrink**
- Dictate how items should shrink when there isn't enough space in container
- Different space distribution formula than `flex-grow`
`flex-shrink: 1;`
  - Default value

#### Browser support
`caniuse.com`
`autoprefixer.github.io`

### *Section 5:* Project: Building A Startup Site
**Advanced CSS Properties**
`background-image: url(someimage.com)`
`background-clip`
`background-size`
`background-position`
`box-sizing: border-box;`

### *Section 6:* Async Foundations
#### Callback Functions
- A function that is passed into another function as a parameter, than invoked by the parent function
```
function callback() {
  console.log('Coming from callback');
}

function higherOrder(fn) {
  console.log('About to call callback');
  fn();
  console.log('Callback has been invoked');
}

higherOrder(callback);
```

**Higher Order Function** - A function that accepts a callback as a parameter

**What are callbacks used for?**
- Very common JS pattern
- Advanced Array Methods
- Browser events
- AJAX Requests
- React Development

**Code Reuse with Callbacks**
```
function sendMessage(message, callback) {
  return callback(message);
}

sendMessage('message for console', console.log);

sendMessage('Message for alert', alert);
```

**Callbacks with Anonymous Functions**
```
function sendMessage(name, formatter) {
  return 'Hello, ' + formatter(name);
}

sendMessage('Matt', function(name){
  return name.toUpperCase();
});
```

**forEach Function Definition**
```
function forEach(array, callback) {
  // ...
}

// Callback signature
function callback(curElement, currentIndex, array) {}
```

**findIndex function**
- Returns the index of the first element in the array for which the callback returns a truthy value.  `-1` is returned if the callback never returns a truthy value

#### The Stack and the Heap
**What is the Stack**
- An ordered data structure
- Keeps track of function invocations
- part of the JavaScript runtime (you don't access it directly)

**How your code changes the Stack**
- When you invoke a function, the detains of the invocation are saved to the top of the stack
- Whenever a function returns, the information about the invocation is taken off the top of the stack (popped off the top)

**Stack Frame**
- Keeps track of:
  - The function that was invoked
  - The parameters that were passed to the Function
  - Current line number

**Stack Definition**
- An stack set of stack frames
- Most recently invoked function is on top of the stack
- The bottom of the stack is the first function invoked
- The stack is processed from top to bottom

**Heap**
- An area in memory where your data is stored

`var obj = {firstName: 'Miller', lastName: 'Anderson'};`
- The object is created in the heap.  obj is a reference to the object

`var referenceCopy = obj;`
- New data is not created, only a copy of the reference

```
var obj = {firstName: 'Miller', lastName: 'Anderson'};
var ref = obj;

ref.firstName = 'Matthew';
```
`console.log(obj.firstName)` -> prints `Matthew`

**setTimeout and setInterval**
**setTimeout** - a function that asynchronously invokes a callback after a delay in milliseconds
- Cleared with `clearTimeout(<timeoutId>)`

**setInterval** - a function that continually invokes a callback after every `x` milliseconds
- Cleared with `clearInterval(<intervalId)`

**Event Loop and the Queue**
**Queue** - An ordered list of functions waiting to be placed on the Stack
  - Functions in the queue are processed in a first in, first out (FIFO) basis
**The Event Loop** - Functionality in the JS runtime that checks the queue when the stack is empty  
  - If the stack is empty, the front of the queue is placed in the stack

**JavaScript is Single Threaded**
- Code execution is linear
- Code that is running cannot be interrupted by another event in the program

#### Promise Basics
- A promise is an object that represents a task that will be completed in the future
- *Analogy* - Taking a number at the DMV before getting helped.  The paper is your promise.  The help received at the counter is the invocation of the callback

```
var p1 = new Promise(function(resolve, reject){
  resolve([1,2,3,4]);
});

p1.then(function(arr){
  console.log('Promise p1 resolved with data:', arr)
});
```

**Promise: Handling Errors**
```
var p1 = new Promise(function(resolve, reject){
  var num = Math.random();
  if(num < 0.5){
    resolve(num)
  } else {reject(num)}
});

p1.then(function(result){
  console.log('Success:', result);
}).catch(function(error){
  console.log('Error:', error);
});
```

#### Promise Chaining
**Disadvantages of Nested Callbacks**
- Hard to read
- Logic is difficult to parse
- Not modular

```
var promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    var num = Math.floor(Math.random() * 10);
    resolve(num);
  }, 3000);
});

promise.then((num) => {
  console.log('promise resolved with random int', num);
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      var num = Math.random();
      resolve(num);
    }, 500)
  });
}).then((num) => {
  console.log(`Chained promise resolved with random decimal ${num}`);
});
```

**Promises in Practice**
- It is useful to understand how promises work (resolve, reject), but in practice you will often use promises that are returned to you

### *Section 7:* AJAX Part 1: XHR and Fetch
#### AJAX Introduction
**AJAX is not**
- A library
- A framework
- A technology

**AJAX is**
- An approach (that's it)

> With AJAX, websites can send and request data from the server in the background without disturbing the current page

**Making Requests with JavaScript**
- XMLHTTP Request
- The Fetch API
- 3rd Party Libraries
  - jQuery
  - Axios
  - etc...

- APIs respond with pure data, *not* structure (no HTML)

**XMLHTTP Requests**
- AKA XHRs

#### Intro to Fetch
**Problems with XHR**
- Ugly, bulky syntax
- 16 years old
- No streaming

**Fetch API**
- 'facelift' for XHR
```
fetch(url)
.then(function(res) {
  console.log(res);
})
.catch(function(error) {
  console.log(error);
});
```

**Fetch Options**
```
fetch(url, {
  method: 'POST',
  body: JSON.stringify({
    name: 'blue',
    login: 'bluecat',
    })
  })
.then(function(data) {
  // do someth ing
  })
.catch(function(error) {
  // handle error
});
```

**Problems with Fetch**
- Limited browser support
  - No support with IE

**AJAX with jQuery**
- `$.ajax`
- `$.get`
- `$.post`
- `$.getJSON`

```
$.ajax({
  method: 'GET',
  url: 'some.api.com'
  })
.done(function(res) {
  console.log(res)
  })
.fail(function() {
  // do something
  })
```

**Axios Intro**
- Lightweight HTTP request library
- Use in place of jQuery if only using request methods (much less code)

```
axios.get(url)
.then(function(res) {
  console.log(res.data)
})
.catch(function(e) {
  console.log(e);
});
```

**Handling Errors with Axios**
```
.catch((error) => {
    if (error.response) {
      ...
    } else if (error.request) {
      ...
    } else {
      ...
    }
});
```

### *Section 9:* Testing with Jasmine
**Unit Tests** - Test parts (units) of an application
  - Often, each unit is tested individually and independently to ensure an application is running as expected

**Jasmine**
- Works with many JavaScript environments
- Simple syntax to 'get up and running'

**Essential Keywords**
- `describe` - *let me describe ____ to you*
  - nest specific high-level concepts to describe
  - `it` - *let me tell you about ____*
    - `expect` - *here's what I expect*

**Conceptual Exercise**
```
describe("Earth")
  it("is round")
    expect(earth.isRound.toBe(true))
  it('is the third planet from the sun')
    expect(earth.numberFromSun).toBe(3)
```

**In Code**
```
var earth = {
  isRound: true,
  numberFromSun: 3
}
```

```
describe('Earth', function(){
  it('is round', functionm(){
    expect(earth.isRound).toBe(true);
  });
  it('is the third planet from the sun', function(){
    expect(earth.numberFromSun).toBe(3);
  })
})
```

**Matchers**
- `toBe()` / `not.toBe()`
- `toBeCloseTo()`
- `toBeDefined()`
- `toBeFalsey()` / `toBeTruthy()`
- `toBeGreaterThan()` / `toBeLessThan()`
- `toContain()`
- `toEqual()`
- `jasmine.any()`

*REMEMBER:* `===` verifies that data being compared share same reference in memory

**BeforeEach**
- run before each `it` callback

```
describe('Arrays', function(){
  var arr;
  beforeEach(function(){
    arr = [1,3,5]
  });
  it('adds elements to an array', function(){
    arr.push(7);
    expect(arr).toEqual([1,3,5,7]);
  });

  it('returns the new length of the array', function(){
    expect(arr.push(7)).toBe(4)
  });

  it('adds anything into the array', function(){
    expect(arr.push({})).toBe(4);
  });
})
```

**AfterEach**
- run after each `it` callback
  - useful for 'teardown'

**beforeAll / afterAll**
- run before/after all tests
- Does not reset between `it` callbacks

**Nesting Describe**
```
describe('Array', function(){
  var arr;
  beforeEach(function(){
    arr = [1,3,5];
  })
  describe('#unshift', function(){
    it('adds an element to the beginning of an array', function(){
      arr.unshift(17);
      expect(arr[0]).toBe(17);
    });
    it('returns the new length', function(){
      expect(arr.unsift(1000)).toBe(4);
    });
  });
  describe('#push', function(){
    it('adds elements to the end of an array', function(){
      arr.push(7);
      expect(arr[arr.length-1]).toBe(7);
    });
    it('returns the new length', function(){
      expect(arr.push(1000)).toBe(4);
    });
  });
});
```

**Pending tests**
- Tests can be marked as pending if you don't know when they'll be executed

```
describe('pending specs', function(){
  xit('can sart with an xit', function(){
    expect(true).toBe(true)
  });

  it('is a pendingtest if there is no callback function');

  it('is pending if the pending function is invoked inside the callback', function(){
    expect(2).toBe(2);
    pending();
  })
})
```

**Best Practices**
- Use seperate `it` blocks to test different functionality
  (best not to use multiple distinct `expect` clauses within one `it` block)

**Spies**
- aka a **Mock** - a fake object that poses as a real object without the necessary overhead of the real object
- Can stub (mimic) any function and track calls to it and all arguments
- Removed after each spec
- Special matchers exist for interacting with spies

**Creating a Spy**
```
function add(a,b,c){
  return a+b+c;
}
```
```
describe('add', function(){
  var addSpy, result;
  beforeEach(function(){
    addSpy = spyOn(window, 'add');
    result = addSpy();
  });
  it('can have params tested', function(){
    expect(addSpy).toHaveBeenCalled();
  });
});
```

**Clock**
- The Jasmine `Clock` is available for testing time dependent code
- Installed by invoking `jasmine.clock().install()`
- Be sure to uninstall the clock after you are done to restore original functions
```
describe('a simple setInterval', function(){
  var dummyFunction;

  beforeEach(function() {
    dummyFunction = jasmine.createSpy('dummyFunction');
    jasmine.clock().install();
  });
  afterEach(function(){
    jasmine.clock().uninstall();
  });

  it('checks to see the number of times the function is invoked', function(){
    setInterval(function(){
      dummyFunction();
    }, 1000);

    jasmine.clock().tick(999);
    expect(dummyFunction.calls.count()).toBe(0);
    jasmine.clock().tick(1);
    expect(dummyFunction.calls.count()).toBe(1);
    jasmine.clock().tick(1000);
    expect(dummyFunction.calls.count()).toBe(2);
  });
});
```

**Testing async code**
- `beforeAll` , `afterAll`, `beforeEach`, `afterEach`, and `it` take an optional single argument (commonly called `done`) that should be called when the async work is complete
- A test will not complete until its `done` is called

```
function getUserInfo(username){
  return $.getJSON(`https://api.github.com/users/${username}`);
}
```
```
describe('#getUserInfo', function(){
  it('returns the correct name for the user', function(done){
    getUserInfo('juicybits').then(function(data){
      expect(data.name).toBe('Matt Anderson');
      done();
    });
  });
});
```

**TDD - Test Driven Development**
1. Write the tests
2. See the tests fail
3. Write code to pass the test
4. Refactor code as necessary
5. Repeat

**BDD - Behavior Driven Development**
- Subs et of **TDD**
- Involves being verbose with our style and describing the behavior of the functionality
- Helpful when testing the design of the software

**Other Kinds of Tests**
- **Integration Tests** - Test multiple units and how they function / behave together
- **Acceptance Tests** - Test whether entire application satisfies a provided spec
- **Stress Test** - Test application effectiveness under stressful / unideal circumstances

### *Section 10:* Advanced Array Methods
`forEach`
- Iterates through an array
- Runs a callback function on each value in the array
- Returns `undefined`

`map`
- creates a new array
- iterates through an array
- runs a callback function for each value in the array
- adds the result of that callback function to the new array
- Returns the new array
- NOTE: the new array is always the same length as that which invoked `map`

`filter`
- creates a new Array
- iterates through an array
- runs a callback function on each value in the Array
- if the callback function returns true, that value will be added to the new array
- If the callback function returns false, that value will be ignored from the new array

`some`
- iterates through an array
- runs a callback on each value in the array
- if the callback returns true for at least one value, return true
- otherwise return false

`every`
- iterates through an array
-runs a callback on each value in the array
- if the callback returns false for any value, return false
- otherwise, return true

`reduce`
- accepts a callback function and an optional second parameter
- iterates through an array
- runs a callback on each value in the array
- the first parameter to the callback is either the first value in the array or the optional second parameter
- The first value to the callback is often called the `accumulator`
- The returned value from the callback becomes the new value of the accumulator

### *Section 11:* Closures and the Keyword 'This'
#### Closures
- A function that makes use of variables defined in outer functions that have previously returned
- Inner functions only store reference to outer functions variables that are needed within the inner function:
- Closures are useful to simulate private variables

```
function outer(){
  var a = 'foo';
  var b = 'bar';
  return function inner(){
    console.log(a);
  }
}
```

#### This
- Usually determined by the execution context (how a function is called)
- `This` is defined when a function is run
- Can be determined with four rules:
  1. Global
  - Object/Implicit
  - Explicit
  - New

**Implicit/Object**
- When the keyword `this` is inside of a declared object, `this` refers to the nearest parent object

**Explicit Binding**
- `call`
- `apply`
- `bind`
  - Unlike `call` and `apply`, `bind` does not immediately invoke the function it is bound to

### *Section 12:* Object Oriented Programming with JavaScript
#### The 'New' keyword
- Creates an empty object
- Sets the keyword `this` to be that empty object
- Adds the line `return this` to the end of the function which follows it
- Adds a property onto the empty object `__proto__` which links the prototype property on the constructor function to the empty object

#### Prototypes
```
function Person(name){
  this.name = name;
}

var matt = new Person('Matt');
matt.__proto__ === Person.prototype; // true
```

#### OOP Recap
- Every time the new keyword is used, a link between the object created and the prototype property of the constructor is established --this link can be accessed using `__proto__`
- The prototype object on the constructor contains a property called constructor which points back to the constructor
- To share properties and methods for objects created by the constructor function, placing them in the prototype is the most efficient
- To pass methods and properties from one prototype object to another, we c an use inheritance:
  - Set the prototype property to be a newly created object using `Object.create` and resetting the constructor property

### *Section 13:* Creating JSON API's with Node and Mongo
#### Responding with JSON
- `res.json({})`

- `status(201)`
  - Signify that new data was created in response to POST request

### *Section 15:* ES2015 Part I
#### Const
- Create values that cannot be redeclared (constant)
- `Const` objects and arrays can still be mutated, but not redeclared:
```
const arr = [1,2,3,4];
arr.push(5);
console.log(arr); // [1,2,3,4,5]
arr = 'hello'; // error
```

#### Arrow Functions
- Can place arrow functions on one line, but **must** omit the `return` keyword and `{}`:
```
var add = (a,b) => {
  return a+b;
}
```
becomes
`var add = (a,b) => a+b;`

- Arrow functions with only one parameter don't need `()`:
`var fn = val => val*2;`

- Not the same as regular functions:
  - Don't get their own `this` keyword
  - In an arrow function, the keyword `this` has its original meaning from the enclosing context (**the context of this directly after the arrow function**)

- Arrow functions don't get their own keyword `arguments`

- When **not** to use arrow functions
  - Should never be used as methods in objects since we will get the incorrect value of the keyword `this`

#### Default Parameters
```
function add(a=10, b=20){
  return a+b;
}

add(); // 30
add(20); // 40
```

#### For...of loops
- Can't access an index
- Can only be used with a `Symbol.iterator` method (no objects)
```
var arr = [1,2,3,4,5];

for(let val of arr){
  console.log(val);
}
```

#### Rest
- Always returns an array
- Is called the rest operator only when it is a parameter to a function
- Is accessed without the `...` in a function
```
function printRest(a,b,...c){
  console.log(a);
  console.log(b);
  console.log(c);
}
printRest(1,2,3,4,5);

// 1
// 2
// [3,4,5]
```

#### Spread
- Used on arrays to spread each value out (as a comma separated value)
- Useful when you have an array, but what you are working with expects comma separated values

```
var arr1 = [1,2,3];
var arr2 = [4,5,6];
var arr3 = [7,8,9];
```
ES5:
`var combined = arr1.concat(arr2).concat(arr3);`
ES6:
`var combined = [...arr1, ...arr2, ...arr3];`

**Spread instead of Apply**
```
var arr = [3,2,4,5,1];
```
`Math.max(arr);` // NaN
ES5:
`Math.max.apply(this,arr);` // 5
ES6:
`math.max(...arr)` // 5

#### Object Enhancements
**Object Shorthand Notation**
```
var fName = 'Miller';
var lName = 'Anderson';

var name = {
  fName,
  lName
}
```

**Object Methods**
ES5
```
var instructor = {
  sayHello: function(){
    return 'Hello!';
  }
}
```
ES6
```
var instructor = {
  sayHello(){
    return 'Hello!';
  }
}
```

**Computed Property Names**
ES5
```
var firstName = 'Elie';
var instructor = {};
instructor[firstName] = 'That\'s me!'
instructor.Elie; // 'That's Me!'
```
ES6
```
var firstName = 'Elie';
var instructor = {
  [firstName]: 'That's me!
}
instructor.Elie; // 'That's Me!''
```

#### Destructuring
Extracting values from data stored in objects and arrays
```
var player = {
  username: 'Miller420',
  score: 420
}
var {username, score} = player;
username; // 'Miller420'
score; // 420
```

**Different Variables**
```
var instructor = {
  firstName: 'Elie',
  lastName: 'Schoppik'
}
var {firstName:first, lastName:last} = instructor;
first; // 'Elie'
last; // 'Schoppik'
```

**Array Destructuring**
```
var arr = [1,2,3];
var [a,b,c] = arr;
a; // 1
b; // 2
c; // 3
```
```
function reverse([a,b]){
  return [b,a];
}
reverse([1,2]); // [2,1]
```

### *Section 17:* ES2015 Part II
#### The Class Keyword
- A new reserved keyword provided by ES6
- Creates a constant -- cannot be redeclared
- Is an abstraction of constructor functions and prototypes (JS does not have built in support for OOP)
- The `class` keyword **does not hoist**
- Uses the `new` keyword to create objects

ES5:
```
function Student(firstName, lastName){
  this.firstName = firstName;
  this.lastName = lastName;
}
var matt = new Student('Matt', 'Anderson');
```

ES6:
```
class Student {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
}

var matt = new Student('Matt', 'Anderson');
```

#### ES6 Instance Methods
ES5:
```
function Student(firstName, lastName){
  this.firstName = firstName;
  this.lastName = lastName;
}
Student.prototype. sayHello = function(){
  return 'Hello ' + this.firstName;
}
```

ES6:
```
class Student {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
  sayHello(){
    return `Hello ${this.firstName}`;
  }
}
```
- Placed inside the `class`
- No `function` keyword
- Under the hood, places methods on the prototype object

#### Class Methods
```
class Student {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
  static isStudent(obj){
    obj.constructor === Student;
  }
}
```

#### Inheritance
- Passing methods and properties from one class to another
ES5:
```
function Student(firstName, lastName){
  this.firstName = firstName;
  this.lastName = lastName;
}
Student.prototype. sayHello = function(){
  return 'Hello ' + this.firstName;
}
function Animal(name, type){
  this.name = name;
  this.type = type;
}

Animal.prototype = Object.create(Student.prototype);
Animal.prototype.constructor = Animal
```

ES6:
```
class Student {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
  sayHello(){
    return `Hello ${this.firstName}`;
  }
}

class Animal extends Student {

}
```

#### Super
ES5:
```
function Person(firstName, lastName){
  this.firstName = firstName;
  this.lastName = lastName;
}
function Student(){
  Person.apply(this, arguments);
}
```

ES6:
```
class Person {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
}

class Student extends Person {
  constructor(firstName, lastName){
    super(firstName, lastName);
  }
}
```
- `super` can only be used if a method by the same name exists in the parent class (in this case, the parent class is `Person` and the method is `constructor`)

#### Maps
- AKA 'hash maps' in other languages
- Similar to objects, but keys can be any data type
- Created using the `new` keyword
- New in `ES6`
```
var firstMap = new Map;
firstMap.set(1, 'Matt');
firstMap.set(false, 'a boolean');
firstMap.set('neat', 'a string');
firstMap.delete('neat');
firstMap.size // 2
```

**Why use maps?**
- Finding size is easy
- Keys can be any data type
- Prevents overwriting keys (unlike objects)

**When to use a map**
- Looking up keys dynamically (not hard coded strings)
- If you need keys that are not strings
- Frequently adding or removing key / value pairs
- Operating on multiple keys at a time

#### WeakMaps
- Similar to map, but all keys must be objects
- Values in a `WeakMap` can be cleared from memory if there is no reference to them
- More performant than maps, but can not be iterated over

#### Sets
- All values in a set are unique
- Any type of value can exist in a set
- Created using the `new` keyword
- New in `ES6`

```
var s = new Set;

// can also be created from an array
var s2 = new Set([3,1,4,1,2,1,5]) // {3,1,4,2,5}
```
```
s.add(10);
s.add(20);
s.add(10); // {20, 10}

s.size; // 2
s.has(10); // true
s.delete(20); // true
s.size; // 1
```

#### WeakSet
- Similar to a set, but all values MUST be objects
- Values can be cleared from memory if there is no reference to them
- More performant than sets but cannot be iterated over

#### Promises
- A one time guaranteed return of some future value
- When that value is determined, that value is resolved/fulfilled or rejected
- Friendly way to refactor callback code
- Created using the `new` keyword
- Every promise constructor accepts a callback function which contains two parameters, `resolve` and `reject` (most common names)
- `resolve` and `reject` are both functions to be run if the promise is resolved or rejected

**Promise.all**
- Accepts an array of promises and resolves all of them or rejects once a single one of the promises has been first rejected (fail fast)
- If all the passed-in promises fulfill, `Promise.all` is fulfilled with an array of values from the passed-in promises, in the same order as the promises passed in
```
function getMovie(title){
  return $.getJSON(`https://omdbapi.com?t=${title}&apikey=thewdb`)
}

var titanicPromise = getMovie('titanic');
var shrekPromise = getMovie('shrek');
var braveheartPromise = getMovie('braveheart');

Promise.all([titanicPromise, shrekPromise, braveheartPromise]).then(function(movies){
  return movies.forEach(function(value){
    console.log(value.Year);
  });
});

// 1997
// 2001
// 1995
```

#### Generators
- A special kind of function which cal pause execution and resume at any time
- Created using a `*`
- When invoked, a generator object is returned with the keys of `value` and `done`
- `Value` is what is returned from the paused function using the `yield` keyword

```
function* printValues(){
  yield 'First';
  yield 'Second';
  yield 'Third';
}

var g = printValues();
g.next().value; // "First"
g.next().value; // "Second"
g.next().value; // "Third"
```

**Iterating over a generator**
```
function* pauseAndReturnValues(num){
  for(let i = 0; i < num; i++){
    yield i;
  }
}

for(val of pauseAndReturnValues(3)){
  console.log(val);
}

// 0
// 1
// 2
```

**Async Generators**
```
function* getMovieData(movieName){
  console.log('starting');
  yield $.getJSON(`https://omdbapi.com?t=${movieName}&apikey=thewdb`);
  console.log('ending');
}

var movieGetter = getMovieData('titanic');
movieGetter.next().value.then(val => console.log(val));
```

#### Object.assign
```
var o = {name: 'Miller'};
var o2 = Object.assign({}, o);

o2.name = 'Matt';
o.name; // "Miller";
```
**Not a deep clone:**
```
var o = {
  instructors: ['Elie', 'Tim']
};
var o2 = Object.assign({}, o);
o2.push('colt');
o.instructors; // ["Elie", "Tim", "Colt"];
```

#### Array.from
- Convert other data types into arrays
```
var firstSet = new Set([1,2,3,4,3,2,1]);
var arratFromSet = Array.from(firstSet);
```

#### Additional ES6 Methods
`find`
- Invoked on arrays
- Returns the value found or `undefined` if not found

`findIndex`
- Returns an index or `-1` if the value is not found

`includes`
- returns a `boolean` if a value is in a string
- Easier than using `indexOf`
- Returns `-1` if value is not found

`Number.isFinite`
`every`

### *Section 18:* ES2016 and ES2017
`**`
- Exponentiation operator
`[].includes`
`padStart`
`padEnd`

#### ES2017 Async Functions
- A special kind of function that is created using the word `async`
- Meant for writing asynchronous code, specifically `Promises`
```
async function first(){

}
first();
first().then(val => console.log(val));  // "We did it!"
```
**Await**
- A reserved keyword that can only be used inside `async` functions
- Pauses the execution of the async function and is followed by a Promise
- Waits for the promise to resolve and resumes the async function's execution and returns the resolved value
- Think of a pause button (or yield with generators)
```
async function getMovieData(){
  console.log('starting!');
  var movieData = await $.getJSON(`https://omdbapi.com?t=titanic&apikey=thewdb`);
  // this line does not run until the promise is resolved
  console.log('all done!');
  console.log(movieData);
}
```

**Object async**
- Can place async functions as methods inside objects

**Handling errors**
- If a promise is rejected using await, an error will be thrown
- Can use `try/catch` statement to handle errors
```
async function getUser(user){
  try {
    var response = await $.getJSON(`https://api.github.com/users/${user}`);
    console.log(response.name);
  } catch(e) {
    console.log('User does not exist');
  }
}
```

**Writing better code with async**
```
async function getMovieData(){
  var titanicPromise = $.getJSON(`https://omdbapi.com?t=titanic&apikey=thewdb`);
  var shrekPromise = $.getJSON(`https://omdbapi.com?t=shrek&apikey=thewdb`);

  var titanicData = await titanicPromise;
  var shrekData = await shrekPromise;

  console.log(titanicData);
  console.log(shrekData);
}

getMovieData();
```
- Start the HTTP requests in parallel and await their resolved promises, rather than awaiting requests sequentially via `await $.getJSON(`https://omdbapi.com?t=titanic&apikey=thewdb`);`

**Await with Promise.all**
```
async function getMovieData(first, second){
  var moviesList = await Promise.all([
    $.getJSON(`https://omdbapi.com?t=${first}&apikey=thewdb`),
    $.getJSON(`https://omdbapi.com?t=${second}&apikey=thewdb`)
  ]);
  console.log(moviesList[0].Year);
  console.log(moviesList[1].Year);
}

getMovieData('shrek', 'blade');
```

#### Object Rest
- Gather remaining (rest) of keys and values in an object  and create a new one out of them

`var student = {first: 'Miller', last: 'Anderson', job: 'student', numSiblings: 5}`
```
var {first, last, ...data} = student;
first; // "Miller"
last; // "Anderson"
data; // { job: 'Student', numSiblings: 3 }
```

#### Object Spread
```
var defaults = {job: 'Instructor', ownsCat: true, ownsDog: true};

var miller = {...defaults, ownsCat: false};

var colt = {...defaults, ownsDog: false};
```

### *Section 19:* D3 and the DOM
**Data Driven Documents**

### *Section 25:* Introduction to React and JSX
#### Front-End Frameworks
- JS libraries that handle DOM manipulation
- Handles navigations (HTML5 push state)
- State management

#### JSX
**Babel** - A transpiler
**Transpiler** - converts from one source code version to another
  - Will be used to convert `JSX` to `Vanilla JS`

#### Create React App
**Webpack** - A module bundler for modern JavaScript applications
  - Combines different JS files into a `bundle.js`
  - Has a plugin system to run tools like babel
  - Also bundles other assets like `css`, `images`, etc

`create-react-app {appname}`

#### Javascript Import Statement
- `Imports` within `{ }` are not default imports and must match the name within the `export` file

#### Props
- Props are **immutable**
```
class ShowText extends Component {
  render() {
    return <div>{this.props.text</div>
  }
}
```
`<ShowText text="This is a prop named text" />`

**defaultProps**
```
class IngredientList extends Component {
  static defaultProps = {
    ingredients: []
  };

  render() {
    return (
      <ul>
        {this.props.ingredients.map((ing, i) =>
          <li key={i}>{ing}</li>
        )}
      </ul>
    );
  }
}
```

**PropTypes**
```
import PropTypes from 'prop-types';

class IngredientList extends Component {
  static defaultProps = {
    ingredients: PropTypes.arrayOf(PropTypes.string).isRequired
  };

  render() {
    return (
      <ul>
        {this.props.ingredients.map((ing, i) =>
          <li key={i}>{ing}</li>
        )}
      </ul>
    );
  }
}
```

#### State
- Stateful data that can change within an application
```
class App extends Component {
  constructor(props) {
    super(props);
    this.state = { favColor: 'red'};
  }
  render() {
    return(
      <div>
        My favorite color is {this.state.favColor}
      </div>
    );
  }
}
```
- `setState`

#### Pure Functions
- A function with no side effects
- Does not modify its inputs
- Is repeatable (same inputs, same outputs)
- All changes to `this.state` should be pure

#### Component Architecture
- `State` is always passed from a parent component down to a child component as a `prop`
- State should not be passed to a sibling or a parent
- Props don't change, but a component that inherited a parent's state as props can unmount and remount with the newly modified property
- State should be owned by one component

**setState**
- Calls the `render` method when updated

**Stateless Functional Component**
```
import React from 'react';

const Greeting = props => (
  <h1>Hello, {props.name}</h1>
);

export default Greeting;
```

#### Thinking in React
- 1) Break the UI into a Component Hierarchy
  - Draw boxes around every component and subcomponent in the mock and give them names
  - What should be a component?  Follow the *single responsibility principle*, which dictates that ideally a component should only do one thing
- 2) Build a Static Version in React
  - Build a version that takes the `data model` and renders the UI with no interactivity
  - **Don't use state at all yet**
  - It's usually easier to build components using a *top-down* approach
- 3) Identify the minimal (but complete) Representation of UI State
  - The key here is **DRY** *(Don't Repeat Yourself)*
  - Ask these questions to determine what is state:
    - 1) Is it passed in from a parent via props?  Probably not state.
    - 2) Does it remain unchanged over time?  Probably not state.
    - 3) Can you compute it based on any other state or props in your component?  Probably not state.
- 4) Identify Where Your State Should Live
  - Identify every component that renders something based on state
  - Find a common owner component (a single parent component housing both)
  - Either the common owner or another component higher up in the hierarchy should own the state
  - If none exists that makes sense to hold the state, create a new component meant simply for holding the state and add it somewhere in the hierarchy above the common owner component
- 5) Add Inverse Data Flow

#### setState Can Be Tricky
**Rule:**  When a `setState` depends on previous state, use a function parameter:
```
this.setState((prevState, props) => {
  return {
    counter: prevState.counter + 1
  };
});
```

- `setState` is **asynchronous**, so use a callback function if necessary:
```
this.setState({name: 'Matt'}, () => {
  console.log('State is up to date', this.state.name);
});
```

### *Section 28:* The Virtual DOM, Events, and Forms
#### Virtual DOM
- A data structure stored by React that tracks changes from one render state to the next
-  If something has changed from one render state to the next, the browser's DOM is updated (**reconciliation**)

#### Synthetic Events
- Supports all native browser events, but provides a consistent API on all browsers

#### React 16 (Fiber) Features
- Render can return an array of JSX elements or a string:
```
render() {
  return [
    <div key='a'>First Element</div>
    <div key='b'>Second Element</div>
  ]
}
```

#### Events
- Interaction in React is added directly to the component where the interaction should occur
**onClick**
```
class ClickExample extends Component {
  constructor(props){
    super(props);
    this.state = {name: 'miller'}
  }
  render() {
    return (
      <div>
        <p>{this.state.name}</p>
        <button type="button"
          onClick={() => this.setState({name: 'MILLER'})}>
          UPPERCASE
        </button>
      </div>
    );
  }
}
```

#### Forms
- Use an `onSubmit` event for form submission, **NOT** `onClick` (browsers handle behavior differently)

#### Refs
- A direct reference to a DOM element

**Use Cases**
- Manage focus, text selection, or media playback
- Triggering imperative animations
- Integrating with third-party DOM libraries

- Avoid `refs` when the job can be done with `React`

#### React
- Using the index of array elements as a key works only as long as elements in that array cannot be removed / modified

### *Section 29:* Component Lifecycle Methods
#### Mounting
- `constructor()`
- `componentWillMount()`
  - Called when constructor has finished but component hasn't mounted (`render()` hasn't been called)
- `render()`
- `componentDidMount()`
  - Occurs after components markup has been placed in the DOM

#### Unmounting
- `componentWillUnmount`

#### Updating
- `componentWillReceiveProps(nextProps)`
  - Occurs whenever `setState()` is called
- `shouldComponentUpdate(nextProps, nextState)`
- `componentWillUpdate(nextProps, nextState)`
- `render()`
- `componentDidUpdate(prevProps, prevState)`
- `forceUpdate(callback)`
  - skips `shouldComponentUpdate` and forces a render (avoid in most cases)

#### Examples
**componentWillUnmount**
```
const NUM_BOXES = 32;

class Boxes extends Component {
  constructor(props) {
    super(props);
    const boxes = Array(NUM_BOXES).fill.map(this.getRandomColor, this);
    this.state = {boxes};

    this.intervalId = setInterval(() => {
        const boxes = this.state.boxes.slice();
        const ind = Math.floor(Math.random()*boxes.length);
        boxes[ind] = this.getRandomColor();
        this.setState({boxes});
    }, 300)
  }
  componentWillUnmount(){
    clearInterval(this.intervalId);
  }
}
```

### *Section 31:* Authentication
#### One Way Hashing
- Converting data into a fixed length has string
- Can only recreate the hash if original data is known
- Applicable for saving passwords on your server

### JWT (JSON Web Token)
- A web standard for storing signed data
- Can use JWTs as proof that user has logged in before

**Format**
- Header
- Payload
- Signature

- Client generates a **header** and **payload** for content they are requesting
- Kept secure with **signature**, which is only generated server-side
- Server inspects **header** to ensure it hasn't been tampered with, then inspects **payload** for a user ID / relevant information

`jwt.io`

- Since **signature** is generated from **header** and **payload**, tampering either on client-side will invalidate signature

- **Secret Key** should be kept out of codebase, i.e. in `process.env.SECTET_KEY` to ensure only trusted eyes see key
  - **Secret Key** is used to decode hashed messages (i.e. Token)

#### Authentication vs Authorization
- Just because you are who you say you are, you may not necessarily have permission to perform a certain action

### *Section 32:* React Router
#### HTML5 History Object
- `history.back()`
- `history.forward()`
- `history.pushState({}, 'title', '/newpage')`

- Changes the url address bar
- Changes the browser's local navigation history
- **Does not** cause the browser to make a `GET` request
- What will we use it for?
  - Browser back button, internal links, etc should all seem to behave like a page with server rendering
  - Handling bookmarked react content

#### React Router
- Conditionally render React components based on URL and change URL
- A library to manage routing in your single page application
- A declarative API that uses components to make rendering decisions

#### BrowserRouter vs HashRouter
- BrowserRouter uses `history` object and makes changes to URL
- HashRouter adds hashes to URL instead and does *not* use `history` object
- BrowserRouter requires server support
- HashRouter does not require server support

#### React Router Setup
`npm install --save react-router-dom`
```
import React from 'react';
import ReactDOM from 'react-dom';
import { BrowserRouter as Router} from 'react-router-dom'
import App from './App';

ReactDOM.render(
    <Router>
      <App />
    </Router>,
    document.getElementById('root');
)
```

#### Switch and Route
```
import React, { Component } from 'react';
import {
  Switch, Route
} from 'react-rouder-dom';

const Homepage = () => (<div>HOMEPAGE</div>);
const About = () => (<div>ABOUT</div>);

const SwitchDemo = () => {
  <Switch>
    <Route path="/about" component={About} />
    <Route path="/" component={Homepage} />
  </Switch>
}
```
  - `<Switch>` acts as an `if else` block for components

#### Link
```
import React from 'react';
import { Link } from 'react-router-dom';
import SwitchDemo from './SwitchDemo';

const App = () => (
  <div>
    <Link to="/">HOME</Link>
    <Link to="/about">ABOUT</Link>
    <div>
      <SwitchDemo/>
    </div>
  </div>
)
```

#### NavLink
```
import React from 'react';
import { NavLink } from 'react-router-dom';
import SwitchDemo from './SwitchDemo';

const s={color: "red"};
const App = () => (
  <div>
    <NavLink exact activeStyle={s} to="/">
    HOME
    </NavLink>
    <NavLink exact activeStyle={s} to="/about">
    ABOUT
    </NavLink>
    <div>
      <SwitchDemo/>
    </div>
  </div>
)
```

#### URL Parameters
```
import React, { Component } from 'react';
import {
  Switch, Route
} from 'react-rouder-dom';

const Homepage = () => (<div>HOMEPAGE</div>);
const Name = ({match}) => (
  <div>Hello, {match.params.name}</div>
);

const SwitchDemo = () => {
  <Switch>
    <Route path="/:name" component={Name} />
    <Route path="/" component={Homepage} />
  </Switch>
}
```

#### Route Props
- A component inside of a route gets 3 props:
  1. **match** - info about how the url matches the route component
  2. **location** - where you are now, similar to window.location
  3. **history** - similar to HTML5 history object, allows explicit changes to the url

#### withRouter
- If a component is not rendered inside of a Route component, you can use `withRouter` to get route props
```
import {
  withRouter, Switch, Route
} from 'react-router-dom';

const SwitchDemo = ({history}) => (
  <div>
    <Switch>
    <Route path="/:name" component={Name}/>
    <Route path="/" component={Homepage}/>
    </Switch>
    <button onClick={() => history.push('/')}>
      Go Home
    </button>
  </div>
);
export default withRouter(SwitchDemo);
```

#### Render vs Component
- Use `render` to pass custom props to your component
- The route component can either use `render` *or* component (never both)
```
import { Route } from 'react-router-dom';
const teachers = ['Tim', 'Colt', 'Matt', 'Elie'];
const Teachers = ({teachers}) => (
  <ul>
    {teachers.map((teach, i) => (
        <li key={i}>{teach}</li>
    ))}
  </ul>
);

const App = () => (
    <Route path="/teachers" render={props => (
        <Teachers {...props} teachers={teachers} />
    )}/>
);
```
