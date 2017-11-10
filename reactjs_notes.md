- React acts like an *agent* for the browser

- Component names must start with a capital

- React will update HTML Views in the DOM when the **State** of one of its **Components** changes

- React stores a virtual representation of the HTML Tree (Virtual DOM) in memory
    - State changes modify the HTML Tree of the Virtual DOM first
    - This State change only changes the Tree hierarchy where necessary, rather than recreating the entire tree -- **Tree Reconciliation**
    - This new Virtual HTML Tree is then shared with the Browser's DOM


- The `React` Library can be used without a Browser, the `ReactDOM` library is required for use with a Browser

- In React, every HTML Element is an **Object**

> React has a smart diffing algorithm that it uses to only regenerate in its DOM node what actually needs to be regenerated while it keeps everything else as is.

- React stores both the last DOM Version used by the browser and the latest DOM Version created by the Virtual DOM.  It compares the two and instructs the browser to only update the computed difference rather than the entire DOM node

- All **Components** are reusable
    - At their core, components are just vanilla JS functions

**JSX**
- Put JS expressions in '{}'
    - JS Objects also count as expressions in JSX
- Cannot use `if` statements, but `ternary operators` are ok


```
// Wrong:
onClick={this.handleClick()}
// Right:
onClick={this.handleClick}
```
