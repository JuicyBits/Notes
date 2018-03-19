## Debugging
1. Add `debugger;` to function
2. In terminal, run `node inspect [FILE NAME]`
3. In terminal, enter `c` to continue
4. In terminal, type `repl` to inspect variables

## Algorithm Solving Help
- Remember `for(let value of iterable)` syntax
- Remember `Array.every()` helper method
- Remember `Array.indexOf()` helper method
- Remember `Array.includes()` and `String.includes()` helper methods

## Regular Expressions
- Patterns used to match character combinations in strings
- Used with `match`, `replace`, `search`, and `split` methods of `String`
- `str.replace(/[^\w]/g, '')`
  - `\w` matches with all alphanumeric characters and `_`
  - `^\w` signifies a negated complimented character set:  When there are **not** alphanumeric characters, there is a match
- `str.match(/[aeiou]/gi)`
  - Return an array with all characters in `str` that are vowels, ignoring case (`i`), and not stopping on first match (`g`)

## Runtime Complexity
- Describes the performance of an algorithm
- How much more processing power / time is required to run your algorithm is we double the inputs?

### String Reverse
- `abc` -> `cba`  
- `abcdefgh` -> `hgfedcba`
- Each additional char = 1 step through 1 loop
- This would be `N` or `linear` runtime

### Steps Algorithm
- as `n` increased by one, many more tasks had to be executed (`n*n` things in total)
- This would be `N^2` or `quadratic` runtime

## Determining Complexity

| Name | Notation | Definition |
|-----|--------|--------|
| Constant Time |
| Logarithmic Time |

## Data Structures
- Ways of organizing information with optimal 'runtime complexity' for adding or removing records
- Javascript natively implements several data structures
- JS Arrays implement queues

### Queue
- An ordered list of functions waiting to be placed on the stack
- Added on a FIFO basis (First in First Out)

| Queue | Array Equivalent |
| Add to queue | `array.unshift()` |
| Remove from queue | `array.pop()` |
