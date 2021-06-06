`this` Context 
===

The keyword `this` changes context for a function based on where it is called.

## Call Site

The context for `this` is determined by where the function is actually called via `(` `)`,
also know as the call site.

The simplest way to know what `this` will be is to look to the left of 
the `.` at the call site.

```js
const person = {
    name: 'Jill',
    greet() {
        console.log(`Hello my name is ${this.name}`);
    }
};

person.greet(); // <-- this is a call site, "person" is the `this` context
// Hello my name is Jill

const greet = person.greet; // <-- this is assigning the function to a variable
greet(); // <-- this is also a call site, there is no "." and thus no `this` context
// Hello my name is undefined

const cat = { name: 'felix' };
cat.meow = greet;
cat.meow() // <-- call site! "cat" is to the left of the "."
// Hello my name is felix
```

The second case is an example of the biggest mistake made when passing a function that needs
its `this` context to work correctly. Usually it happens when passing the function 
as a callback method:

```js
// When passing the function as an argument, it is no longer associated 
// with the person object:
button.addEventListener('click', person.greet); 

// when button clicked:
// Hello my name is undefined
```

## Classes

When using constructor functions or classes, the call site is still the 
determining factor for what the `this` context will be.

```js

class Person {
    constructor(name) {
        this.name = name;
    }

    logName() {
        console.log(this.name);
    }
}

const person = new Person('Joe');

person.logName();
// Joe

const log = person.logName;
log();
// undefined
```

## Arrow Functions

Arrow functions are context-less. This means they don't follow the call site rules,
instead `this` refers to what `this` is _where the arrow function is defined_.

```js
class Person {
    constructor(name) {
        this.name = name;
    }

    logName() {
        // (B) arrow function picks up `this` from call to `logName` where it is defined
        setTimeout(() => { 
            console.log(this.name); // (C) call site for arrow function doesn't matter, so this works as expected
        });
    }
}

const person = new Person('Jackie');
person.logName(); // (A) call site for `logName` with `person` as context
```

This characteristic of arrow functions is a feature and solves many `this` problems
in asynchronous JavaScript.

## Modern JavaScript and global `this`

In earlier versions of JavaScript, `this` would be set to the global context like `window`
if there was no call site context. In modern JavaScript (ES6 and on), it will
be undefined.
