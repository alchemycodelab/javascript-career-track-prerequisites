Control Flow
===

## `if` and `else`

Write singular `if`, `if` with `else`, and chained `if`, `else if`, `else` control flow constructs:

```js
// single `if`
if(foo) {
  foo = foo + '!';
}

// `if` with `else`
if(foo) {
  foo = foo + '!';
}
else {
  foo = ':(';
}

// `if` with `else if` and `else`
if(foo) {
  foo = foo + '!';
}
else if(bar) {
  bar = bar + '!';
}
else {
  foo = ':(';
}
```

## Loops

### `for`

Write `for` loops and understand the three statements:

```js
for(
  /*initializer*/ let i = 0; 
  /*condition test*/ i < cats.length;  
  /*post-loop update*/ i++ 
) {
  const cat = cats[i];
  console.log(cat.name);
}
```

### `while`

Write `while` loops:

```js
let i = 0; // initialize
while(i < cats.length) { // condition test
  const cat = cats[i];
  console.log(cat.name);
  i++; // update before next loop
}
```

### `break` and `continue` for loops

`break` and `continue` and keywords used to exit or skip control flow.

```js
let i = 0; // initialize
while(true) {
  const cat = cats[i];
  console.log(cat.name);
  i++; // update before next loop
  if(i === cats.length) break; // exits the while loop
}
```

```js
for(let i = 0; i < cats.length; i++) {
  const cat = cats[i];
  if(cat.type !== 'tuxedo') continue; // skips to next loop
  console.log(cat.name);
}
```

`return` and `throw` _only_ apply to functions and not control flow
  

