Operators and Comparisons
===

## Operator shorthand
Operators that are applied to a variable and then reassigned to that
same variable can use the following shorthand syntax:

```js
const x = 4;
x += 8; // x is now 12
x /= 3  // x is now 4
x *= 2  // x is now 8

// the above is shorthand for:
const x = 4;
x = x + 8;
x = x / 3;
x = x * 2;
```

## Incrementor and Decrementor

`++` and `--` respectively add and subtract `1` from the current 
variable value. Depending on whether they are place before or after
the variable determine whether the prior or new value is returned:

```js
let x = 1;
console.log(x++); 
// 1 (not 2!);
console.log(x); 
// 2

console.log(++x);
// 3
```

## Comparisons

Use `===` and `!==` _unless_ explicitly type cast is needed:

```js
function doubleNumber(n) {
    if(n === 0) throw new Error('Expected positive number to double');
}

const input = document.getElementById('name-input');
// html input controls return strings
if(input.value == 3) alert('correct!');

```

Avoid comparing against `true` and `false` as it is largely unnecessary:

```js
// this is redundant:
if(condition === true) alert('true!');

// just test the condition:
if(condition) alert('true!');
```

