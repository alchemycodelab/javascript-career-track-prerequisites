Functions
===

Functions are one of the core datatypes in JavaScript. Functions _are_ Objects but have a special ability to be "called" using `()`. 

It is important to distinguish between a function as an object, and calling a function which runs the code defined in the function.

## Parameters and Arguments

A function definition includes the parameters defined for that function. The values passed when calling a function are the "arguments" passed to the function.

```js
// the function "add" as two defined parameters, `x` and `y`.
function add(x, y) {
    return x + y;
}

// The values `1` and `2` are being passed 
// as arguments to the add function.
add(1, 2);
```

## Types of Function Definitions

There are three main types of functions that can be defined in JavaScript.

### Function Declarations

Declared functions are stand-alone functions with a name. Declared functions
_can_ be used by code prior to the function declaration.

```js

console.log(add(1, 2)); // this works!
// 3

function add(x, y) {
    return x + y;
}

```

### Function Expressions

Function expressions are used as an expression, meaning they can be assigned to 
variables or passed to other functions. They cannot be called prior to being
defined.

```js
// this will throw an error as "add" has not yet been defined
// add(3, 4);

const add = function(a, b) { return x + y; }

button.addEventListener('click', function(event){
    alert('clicked!');
});
```

Function expressions without a name are sometimes referred to as
anonymous functions.

### Arrow Functions

Arrow functions are expression functions defined without the `function` keyword 
that use an `=>` (arrow) syntax between the parameters and the function body.

```js
// normal function expression:
button.addEventListener('click', function(event) {
    alert('clicked!');
});

// arrow function expression:
button.addEventListener('click', (event) => {
    alert('clicked!');
});
```

When an arrow function has a single parameter, the parenthesis may optionally be omitted.
If there are no parameters, the parenthesis _must_ be included.

If the arrow function only returns a single expression, the block delimiters (`{` `}`) and
`return` keyword may also be omitted.

```js
const numbers = [1, 2, 3];

// function expression:
numbers.map(function(x) {
    return x * x;
});

// arrow function:
numbers.map((x) => {
    return x * x;
});

// omit parenthesis on single parameter:
numbers.map(x => {
    return x * x;
});

// omit block and return on single expression return:
numbers.map(x => x * x);
```
