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
- Use `node *filename.js*` to execute Javascript with node
- The `faker` NPM package is useful for creating dummy data

### *Section 23:* Server Side Frameworks
**Libraries vs. Frameworks**
> The most important difference between a Library and Framework is *Inversion of Control*

- You call a library, a framework calls *you*
- Frameworks make decisions for you (basic scaffolding), with predetermined 'white spots' that you fill out (think *MadLibs*)

**Popular frameworks**
- `Express` for `Node`
- `RubyOnRails` for `Ruby`
- `Flask` for `Python`

**Why Express?**
- Lightweight framework (hides less from the user than heavyweight frameworks like `Rails`)
> Fast, unopinionated, minimalist Web framework for **Node.js**

- Unopinionated = flexible

- Route order matters
- **DRY** - **D**on't **R**epeat **Y**ourself

**Route Parameters**
- `app.get('/table/:id')`
  - Match a route with `/table/*anything*`

### *Section 24:* Intermediate Express
**EJS** - **E**mbedded **J**ava**S**cript
**EJS Control Flow**

### *Section 25:* Working With APIs *Connecting with other applications*
**A**pplication **P**rogram(ing) **I**nterface
- Interfaces for code/computers to talk to one another

**Web APIs**
`ifttt.com` -> If This, Then That
  - Connect multiple APIs
`programmableweb.com` -> API library

- Most commonly, Web APIs send `JSON` or `XML` data

`request`
- NPM package for making HTTP calls from Node

**Status Codes**
- `200` -> OK
- `404` -> Not found

`%20` -> URL encoded version of `' '`

`JSON.parse(*data*)` -> parse string as JSON
