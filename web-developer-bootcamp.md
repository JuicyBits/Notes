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
