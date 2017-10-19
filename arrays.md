Arrays
===

Arrays are one of the fundamental data structures in JavaScript, used to track lists of items.

## Length And Index 

Arrays have a `.length` property. Use `[` `]` to get set elements by index.

```js
const array = [1, 2, 3];

array.length // returns 3, count of elements

// get an element, 0-based indexes:
const number = array[0]; // number === 1

// get last element
array[array.length - 1]; // 3

// set an element:
array[0] = 12;

```

## Iterable

Iteration of arrays is based on using the `.length` and `[` `]` index of the array:

```js
const array = [1, 2, 3];

// indexes as length allow looping
for(let i = 0; i < array.length; i++) {
    console.log(array[i]);
}
// 1
// 2
// 3
```

## Methods for Changing an Array

### `.push` and `.pop`

These array methods add or remove an element from the **end** of an array.

```js
const letters = ['a', 'b', 'c'];

// `.push` returns new length of array
const newLength = letters.push('d'); // ['a', 'b', 'c', 'd']
console.log(newLength);
// 4
```

```js
const letters = ['a', 'b', 'c'];

// `.pop` returns removed element
const popped = letters.pop(); // ['a', 'b'];
console.log(popped);
// 'c'
```

Push will accept more than one argument:

```js
const letters = ['a', 'b', 'c'];
letters.push('d', 'e', 'f'); // ['a', 'b', 'c', 'd', 'e', 'f']
```

### `.unshift` and `.shift`

These array methods add or remove an element from the **start** of an array.

```js
const letters = ['a', 'b', 'c'];

// `.unshift` returns new length of array
const newLength = letters.unshift('d'); // ['d', 'a', 'b', 'c']
console.log(newLength);
// 4
```

```js
const letters = ['a', 'b', 'c'];

// `.shift` returns removed element
const unshift = letters.shift(); // ['a', 'b']
console.log(popped);
// 'c'
```

Like push, unshift accepts multiple arguments.

### `.splice`

Splice can handle any type of insertion and/or removal. Parameters (some optional) are:

`array.splice(<startingIndex>, <number of elements to remove>, <first element to add>, <second element to add>, ...)`

```js
const letters = ['a', 'b', 'c'];
letters.splice(2, 1, 'd', 'e'); // ['a', 'b', 'd', 'e'];
```

## `.slice`

Not to be confused with `.splice`, `.slice` copies an array:

```js
const letters = ['a', 'b', 'c'];
const copy = letters.slice();
copy.splice(1, 2);
console.log(letters);
// ['a', 'b', 'c']
console.log(copy);
// ['a']
```

Slice can optionally take start and end indexes from which to copy.

## Functional Array Methods

Many of the methods available on an array take a function. The first
two arguments to almost all of these methods are:

1. The current element of the array being iterated
1. The index of the current element

### `.forEach` 

Calls the given function for each element in the array:

```js
const array = [1, 2, 3];
array.forEach((element, index) => {
    console.log(index, '-', element);
});
// 0 - 1
// 1 - 2
// 2 - 3
```

### `.map` 

Creates a new array, passing each element to the given function
and putting the return value in the same index in the new array:

```js
const numbers = [1, 2, 3];
const squared = numbers.map(x => x * x);
console.log(squared);
// 1
// 4
// 9

const letters = ['a', 'b', 'c'];
const list = letters.map((letter, index) => {
    return `Index ${index} has letter "${letter}".`;
});
console.log(list);
// [
//  'Index 0 has letter "a".',
//  'Index 1 has letter "b".',
//  'Index 2 has letter "c".',
// ]
```

Recognize that this is an anti-pattern:

```js
const numbers = [1, 2, 3];
const squared = [];
numbers.forEach(x => {
    squared.push(x);
});
```

And should be replaced with a `.map` operation.

### `.filter`

Some of the array methods, like `.filter`, take functions called
predicates that test each element for some condition and return true
or false.  Other examples are `.find`, `.findIndex`, `.some`, and `.every`.

`.filter` returns a new array with only those elements that return true 
when passed to the predicate function:

```js
const numbers = [1, 7, 4, 2, 9, 3, 7];
const small = numbers.filter(n => n < 5);
console.log(small);
// [1, 4, 2, 3];
```

### `.find` and `.findIndex`

These are also predicate based array methods like `.filter`. 
Instead of returning a new array, `.find` returns the first element
"found" (returns `true` from the callback function). `findIndex` returns the index of the first found element.

```js
const fruits = [
    { id: 21, name: 'apple' },
    { id: 72, name: 'pear' },
    { id: 12, name: 'banana' },
    { id: 34, name: 'mango' }
];

function findById(id) {
    return fruits.find(fruit => fruit.id === id);
}

function getIndex(id) {
    return fruits.findIndex(fruit => fruit.id === id);
}

console.log(findById(72));
// { id: 72, name: 'pear' }

console.log(getIndex(72));
// 1
```

### `.indexOf`

IndexOf is a shorthand special case for `.findIndex`:

```js
const words = ['peach', 'mango', 'apple', 'banana'];
const foundIndex = words.findIndex(word => word === 'apple');
// found is 2

// does same thing as above:
const index = words.indexOf('apple');
// index is 2
```

### `.sort`

Unlike the previous array methods, calling `.sort` _changes the array_
rather than creating a new array. It also has a different style of 
callback function than the other array methods, a comparison function that
takes two items and you indicate the relative sort order by returning a negative number,
zero, or a positive number.

```js
const numbers = [3, 7, 2, 7, 2, 2, 9];
numbers.sort((a, b) => {
    if(a === b) return 0;
    if(a < b) return -1;
    return 1;
});
console.log(numbers);
// [2, 2, 2, 3, 7, 7, 9]
```

The default sort if lexical sorting (sorted alphabetically).

```js
const words = ['peach', 'mango', 'apple', 'banana'];
const numbers = [10, 1, 12, 30, 3, 7];

words.sort();
numbers.sort();

console.log(words);
// ['apple', 'banana', 'mango', 'peach']

console.log(numbers);
// [1, 10, 12, 3, 30, 7];
```

 
