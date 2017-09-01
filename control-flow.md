Control Flow
===

Students should be proficient to fluent with the following control flow statements

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
  let i = 0; /*initializer*/
  i < cats.length;  /*condition test*/
  i++ /*update after loop*/) {
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

```js
let i = 0; // initialize
while(true) {
  const cat = cats[i];
  console.log(cat.name);
  i++; // update before next loop
  if(i === cats.length) break; // condition test
}
```

```js
for(let i = 0; i < cats.length; i++) {
  const cat = cats[i];
  if(cat.type !== 'tuxedo') continue;
  console.log(cat.name);
}
```

Know that `return` does not apply to loops
  

