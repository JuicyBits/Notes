### Overview
- React acts like an *agent* for the browser

- React will update HTML Views in the DOM when the **State** of one of its **Components** changes

- React stores a virtual representation of the HTML Tree (Virtual DOM) in memory
    - State changes modify the HTML Tree of the Virtual DOM first
    - This State change only changes the Tree hierarchy where necessary, rather than recreating the entire tree -- **Tree Reconciliation**
    - This new Virtual HTML Tree is then shared with the Browser's DOM

- The `React` Library can be used without a Browser, the `ReactDOM` library is required for use with a Browser
    - `ReactDOM` contains the logic to convert virtual DOM to real DOM

- In React, every HTML Element is an **Object**

> React has a smart diffing algorithm that it uses to only regenerate in its DOM node what actually needs to be regenerated while it keeps everything else as is.

- React stores both the last DOM Version used by the browser and the latest DOM Version created by the Virtual DOM.  It compares the two and instructs the browser to only update the computed difference rather than the entire DOM node

### JSX  
- JSX is a JS extension that allows for the creation of XML style syntax to build React.createElement calls
- Put JS expressions in '{}'
    - Expression means JS must return a value
    - JS Objects also count as expressions in JSX
    - Cannot use `if` statements, but `ternary operators` are ok

```
// Wrong:
onClick={this.handleClick()}
// Right:
onClick={this.handleClick}
```

### Props vs State
- State is private to its Component and can be changed from within the component itself
- Props are external, passed down from Components higher in the hierarchy
- Props cannot be changed internally

### State
- Any changes made to the `state` will cascade down to child components whose `props` values are derived from `state` props
- use `this.setState()` to modify the state

`ReactDOM.render(*<Component />*, *Existing DOM element)`

### Writing Good Components
**Typechecking with PropTypes**
- After `React 15.5`, must be imported via `import PropTypes from 'prop-types';`
- Used to validate data types for Component props

```
*ComponentName*.propTypes = {
    *propName*: React.PropTypes.string,
    *propName*: React.PropTypes.number.isRequired,
};
```
- Specify data type and requirement status of properties

```
Application.propTypes = {
  players: React.PropTypes.arrayOf(React.PropTypes.shape({
    name: React.PropTypes.string.isRequired,
    score: React.PropTypes.number.isRequired,
    id: React.PropTypes.number.isRequired,
  })).isRequired,
}
```
- Use `React.PropTypes.shape` to specify array structure of properties
**Default property values with DefaultProps**

```
*ComponentName*.defaultProps = {
    *propName*: "Default Name",
};
```

### Decomposing an Application
- **Decompose**: Break a large component in to smaller components that can be composed together  
- Strike a balance -- break up components so they are neither too large, nor too small
- Break a component into smaller components when:
    - The component has too much markup
    - The component does too many things
    - The component is reused

### Loops and Lists in JSX
- Use `array.map` to create a list of JSX elements from an array of JavaScript values
    - Similar to a `foreach` loop

### Components
- All **Components** are reusable
    - At their core, components are just vanilla JS functions

- Component names must start with a capital

**Stateless functional component**: A component defined as a function. It takes only props as an argument and returns a virtual DOM
```
const Header = (props) => {
  return(
    <div className="header">
      <h1>{props.title}</h1>
    </div>
  );
}
```

**Component Class**: A component definition that can include things like state, helper methods and other advanced hooks into the page’s DOM
```
const Application extends React.Component{
    render(){
        return(
            <div>...</div>
        );
    }
}
```

### Unidirectional Data Flow
- Two main types of State:

    - **Application State**: The state or data in our application that is core to the functionality of the application as a whole. This usually includes a list of the models and data being manipulated by the interface. If we were to reload our application, the Application state is what we would like to persist the most
    - **Local Component State**: This is state that is used to allow a component to function. Local component state is typically not used by other components in the application, and is less important to persist if the application resets.

> "A component only knows about itself, the properties passed to it, and any child components it may have"

### Working with Forms in React
- Working with Forms in React requires special consideration, since forms are inherently stateful

### Special Notes
- **Be aware of binding issues when using `arrow functions`.  `This` within an arrow function has a different lexical scope**

- **When writing Tables in React, include `tbody` and `thead` -- this is because the browser will automatically create these DOM elements if they are not present, causing discrepancies b/n the Virtual DOM and actual DOM trees**

- Use `componentDidMount()` to hold code that should be executed when the component is successfully mounted to the DOM
- Use `componentWillUnmount()` to hold cleanup code that should be executed when a module (component) is removed from the DOM

- Use `$r` in console to view the top-level React component
    - Use `$r.setState()` to alter the state
