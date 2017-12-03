### *Section 2:* Introduction to Front End Dev
- **Restaurant Analogy**: The backend is everything that happens in the kitchen; the front end is what is is plated and sent to the table

### *Section 7:* Bootstrap
- Mobile first, grid-based system
- Can write nested grids
- Sizes: `xs` `s` `m` `lg` `xl`
- Works well with `FontAwesome` icons

### *Section 13:* DOM Manipulation
**The DOM** - Document Object Model
  - Interface between JS and HTML/CSS
  - Model HTML Tags into JS objects that can be manipulated
  - Everything is stored in the `document` object
  - Use `console.dir(document)` to view entire document object w/ object syntax
  - `document` is the root node from which all elements stem

**Select and Manipulate Workflow**
  - **Select** the DOM element to **Manipulate**

**Important Selector Methods**
  - `document.getElementById()`
  - `document.getElementsByClassName()`
    - **NOTE**: Returns a `Node List`, NOT an array (think of a node list as a lightweight array)
  - `document.getElementsByTagName()`
    - Returns a `Node List`
  - `document.querySelector()`
    - Uses CSS-like selector syntax (`#`, `.`, `Tag Name`)
  - `document.querySelectorAll()`
   - Returns a `Node List`

**Separation of Concerns**
- `HTML` for structure
- `CSS` for presentation
- `JS` for behavior
- The less overlap, the better (generally)

**DOM Manipulation**
- Rather than directly manipulating style with CSS, *best practice* is to define a CSS class and toggle it on or off with JS
- `classList`
  - A read-only list **(not array)** that contains the classes for a given element
  - `*DOM Element*.classList.add()`
  - `*DOM Element*.classList.remove()`
  - `*DOM Element*.classList.toggle()`

- Manipulating text and content
  - `*DOM Element*.textContent = "foobar";`
      - Set or receive text content without inner HTML (no **strong** or *italics*)
  - `*DOM Element*.innerHTML`

- Manipulating Attributes
  - `getAttribute()`
  - `setAttribute()`

- DOM Events
  - *Process:* Select an element and add an **event listener**
  - `element.addEventListener(type, callbackFunction)`

### *Section 16:* Intro to jQuery
> jQuery is a DOM Manipulation library, and the most popular Javascript library, period

**Why use jQuery?**
- Fix "broken" DOM API (old DOM)
- Brevity and Clarity
- Ease of use
- Cross-Browser Support
- AJAX
- Popularity

**Why NOT use jQuery?**
- The DOM API is no longer "broken"
- Does nothing you can't do without it
- Unnecessary dependency
- Performance
- Lots are transitioning away from jQuery

**Useful Methods**
- `$().css()`
- `val()`
- `text()`
- `attr()`
- `html()`
- `addClass()`
- `removeClass()`
- `toggleClass()`

### *Section 17:* Advanced jQuery
**jQuery Events**
- `click()`
- `keypress()`
- `on()`
  - **Most common** jQuery Event Method
- Why use `On()`?
  - `click()` only adds listeners for existing elements
  - `on()` will add listeners for all potential future elements
    - use `parentElement.on(eventType, child, callback())` to add event listeners to children that are appended dynamically-- add the listener to a parent that is always present on page load so the event can 'waterfall' to all children of type `child`

**Effects**

### *Section 19:* Patatap Clone
**Libraries**
- `Paper.js`
- `Howler.js`

- The HTML5 `canvas` element is used to create animations and graphics using javascript

### *Section 21:* The Command Line
- `rm` -> remove files
- `rm -rf` -> remove entire directory (including child files / directories)

### *Section 22:* Intro to Node
