Variables
===

## `let` and `const`

Modern JavaScript does not typically use `var`. Instead, use:

* `const` for variables that will not be re-assigned.
* `let` for variables that will be assigned

Default to using `const`, and only use `let` when the variable needs to be reassigned.

The value stored in `const` can me modified, the variable just cannot be assigned
a new value:

```js
const letters = ['a', 'b', 'c'];

// okay!
letters.push('d') // letters is now ['a', 'b', 'c', 'd']

// throws an error because variable is being re-assigned!
letters = ['d', 'e', 'f']
