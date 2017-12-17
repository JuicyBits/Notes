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

### *Section 27:* Databases
**SQL vs. NoSQL**
- Rigid vs. flexible
- Tabular data vs. BSON data

- Default `Mongo` port: **27017**

**Mongo Shell Basics**
- `insert`
  - `db.*collection*.insert({key: 'value', key: 'value'})`
- `find`
- `update`
  - `db.*collection*.update({*existing key: 'value'*}, {$set: {*new key: 'value'*}})`
    - Update an entry without overwriting its existing properties
- `remove`
  - `db.*collection*.remove({*key: 'value'}).limit(3)`
    - Remove 3 entries matching the provided key/value

**Mongoose**
> Elegant `mongodb` modeling for `node.js`

- `Mongoose` is an `ODM` - **O**bject **D**ata **M**apper**

```
let schema = new mongoose.Schema({
  key: dataType,
  key: dataType,
  key: dataType
});
```
- Define a new schema

`let VAR = mongoose.model('singularCollectionName', schema);`
- Model an object for document instancing


### *Section 29:* RESTful Routing
`REST` - **RE**presentational **S**tate **T**ransfer**
  - A mapping between HTTP routes and CRUD functionality
  - A pattern for defining routes

| Name | Path | HTTP Verb | Purpose |
|-----|----|-----|------|
| Index | /dogs | GET| Display a list of all dogs |
| New   | /dogs/new | GET | Displays form to make a new dog |
| Create | /dogs | POST | Add a new dog to DB |
| Show  | /dogs/:id | GET | Shows info about one dog |
| Edit  | /dogs/:id/edit | GET | Show edit form for one dog |
| Update | /dogs/:id | PUT | Update a particular dog, then redirect somewhere |
| Destroy | /dogs/:id | DELETE | Delete a particular dog, then redirect somewhere |

**Useful Libraries**
- `MomentJS`

**More on HTML Forms**
- Currently, HTML Forms only support `POST` and `GET` requests (`POST` will default as `GET`)
  - `GET` and `PUT` requests will add a query string with all form data to URL
  - Workaround?  `method override`
    - Add `?_method=PUT` to end of query string to override request type
    - **Must install `method-override` package**

**Sanitizing User Input**
- Use `express-sanitizer` package
- `app.use(expressSanitizer());`
- `req.body.*content* = req.sanitize(req.body.*content*);`

### *Section 30:* Data Associations
**Embedded Data**
- Store `1` side data of a `1:M` relationship on the `M` side within an array property

**Object References**
- Rather than storing embedded data in an array on the `M` side, store a reference to that data (ID, primary key) that lives in another collection

**Promise Deprecation Error**
```
(node:3341) DeprecationWarning: Mongoose: mpromise (mongoose's default promise library) is deprecated, plug in your own promise library instead: http://mongoosejs.com/docs/promises.html
```
- Fix with `mongoose.Promise = global.Promise;` before calling `mongoose.connect`

### *Section 31:*
**Nested Routes**
`/campgrounds/:id/comments/new`
 - The nested `comments` route appears after the campground route, as it is dependent on the `id` to link the comment with a particular campground instance

### *Section 32:* Intro to Authentication with Passport
**What tools are we using?**
- Passport
- Passport Local
- Passport Local Mongoose
- Express-Session

**Useful Passport Methods**
- `req.isAuthenticated()`
- `req.logout()`

`app.get('/*path*/', *middleware function*, (req, res) => {})`
  - Middleware function is called before request is even parsed
  - Remember to `return next();` in middleware to continue to next event

### *Section 32:* Manual Authentication
**Useful Passport Local / Passport Local Mongoose Methods**
- `*MODEL*.register(*object*, *password*, (err, *inserted object*) => {})`
- `passport.authenticate(*strategy*, {
  successRedirect: *redirect path*,
  failureRedirect *failure path*
  })`

**REMEMBER:** POST requests and other HTTP Methods can be sent without access to forms (using products like `Postman`)

### *Section 35:* YelpCamp: Update and Destroy
- Use Mongoose's `.equals()` method to compare an `ObjectID` as a string
- Use `res.locals.*property name*` to make properties accessible to template engines
**Error-Driven Development**
- Write the code you *want* to work, fix errors as they come

**Requiring directories and index.js**
- When `require(*directory*)` is used with no extension, `index.js` will be used automatically (no need for `require(*directory*/index.js)`)

### *Section 36:* YelpCamp: UI Improvements
**Connect Flash**
- Package used to display alerts and information to end users
- `req.flash(*key*, *value*)`
  - Determines which flash messages appear on the **next** request

- `modernizr` is a Javascript library for making HTML, CSS, and JS features compatible for all browser types

- Want to vertically align content?
  - Instead of `translate` in CSS, try `align-top: 40vh`
  - `vh` = View Height

### *Section 37:* Git and Github
`git init`
- Initialize git repo
`git status`
`git add`
- Add a file to track (git doesn't automatically track all files in a repo)
`git add .`
  - Add all changed / untracked files to stage for commit
`git commit -m ""`
- Commit files with message (*use present tense*)
`git log`
- View history of git commits
`git checkout`
  - `git checkout master`
  - `git checkout *commit hash*`
```
git revert --no-commit *commit hash..head
git commit
```
  - Revert to a previous commit and move the head to that commit

### *Section 38:* Deploying with Heroku
`heroku create`
  - Create a new Heroku app
`git push heroku master`
  - Push master branch to heroku
`heroku logs`
  - View error logs

Heroku automatically installs the latest dependencies (based on `package.json`) before running `start` script

**Run heroku terminal commands from local terminal**
- `Heroku run *command*`

**Deploying YelpCamp with mLab**
- mLab is a `DBaaS` (Database as a Service)

**Environment Variables**
- Not a node specific concept
- Variables particular to server instance
- Hidden
- Useful for creating distinct variables for production / dev environments (IP, PORT, DB URL, etc...)
- `process.env.*variable*`

### Adding User Authentication
- The `locus` package can be used for debugging
  - `eval(require('locus'))`

### Fuzzy Searching
- Use `req.query` to access query string data from GET requests
