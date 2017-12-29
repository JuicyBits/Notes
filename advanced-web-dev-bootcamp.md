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

### Project: Building A Startup Site
**Advanced CSS Properties**
`background-clip`
`background-size`
`background-position`
`box-sizing: border-box;`

### Async Foundations
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

**The Stack and the Heap**
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
