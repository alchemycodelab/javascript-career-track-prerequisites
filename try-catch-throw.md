Try/Catch and Throw
===

## Try Catch Blocks

Potentials errors can be "caught" in JavaScript by putting the code you want
to "try" into a try block. If an error occurs in the code being run in the `try`, control flow will be passed to the "catch" block and include the error that occurred:

```js
const person = undefined;

try {
    // person is undefined, so accessing name throw an error
    console.log(person.name); 
}
catch(err) {
    console.log(err);
    // "Cannot access property name of undefined"
}
```

## Throw

The `throw` keyword can be used to create and throw a new error. Note
that `throw`, like `return` terminates function execution. 

```js

function divide(x, y) {
    if(y === 0) {
        // this ends code execution in the function
        throw new Error('Cannot divide by zero');
    }
     
    return x / y;
}
```