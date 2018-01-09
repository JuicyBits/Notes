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
- Subset of **TDD**
- Involves being verbose with our style and describing the behavior of the functionality
- Helpful when testing the design of the software

**Other Kinds of Tests**
- **Integration Tests** - Test multiple units and how they function / behave together
- **Acceptance Tests** - Test whether entire application satisfies a provided spec
- **Stress Test** - Test application effectiveness under stressful / unideal circumstances
