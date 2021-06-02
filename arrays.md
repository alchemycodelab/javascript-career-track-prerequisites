Arrays
===

Arrays are one of the fundamental data structures in JavaScript, used to track lists of items. Arrays are stored contiguously in memory. Reading or writing a single element is `O(1)` constant time. Accessing the list (iteration) is `O(n)`.

## Length And Index 

Arrays have a `.length` property. Use `[` `]` to get and set elements by index.

```js
const array = ['a', 'b', 'c'];

array.length // returns 3, count of elements

// get an element, 0-based indexes:
const letter = array[0]; // 'a'

// get last element
array[array.length - 1]; // 'c'

// set an element:
array[1] = 'f'; 
// array is now ['a', 'f', 'c']

```

## Iterable

Iteration of arrays is based on using the `.length` and `[` `]` index of the array:

```js
const array = [1, 2, 3];

// indexes and length allow looping
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

Basic `push`:

```js
const letters = ['a', 'b', 'c'];

// `.push` returns new length of array
const newLength = letters.push('d'); 
// letters is now ['a', 'b', 'c', 'd']
console.log(newLength);
// 4
```

Basic `pop`:

```js
const letters = ['a', 'b', 'c'];

// `.pop` returns removed element
const popped = letters.pop(); 
// letters is now ['a', 'b'];
console.log(popped);
// 'c'
```

`push` will accept more than one argument:

```js
const letters = ['a', 'b', 'c'];
letters.push('d', 'e', 'f'); 
// letters is now ['a', 'b', 'c', 'd', 'e', 'f']
```

### `.unshift` and `.shift`

These array methods add or remove an element from the **start** of an array.

`unshift`:

```js
const letters = ['a', 'b', 'c'];

// `.unshift` returns new length of array
const newLength = letters.unshift('d'); 
// letters is now ['d', 'a', 'b', 'c']
console.log(newLength);
// 4
```

`shift`

```js
const letters = ['a', 'b', 'c'];

// `.shift` returns removed element
const letter = letters.shift(); 
// letters is now ['b', 'c']
console.log(letter);
// 'a'
```

Like push, unshift accepts multiple arguments.

### `.splice`

Splice can handle any type of insertion and/or removal. Parameters (some optional) are:

`array.splice(<startingIndex>, <number of elements to remove>, <first element to add>, <second element to add>, ...)`

```js
const letters = ['a', 'b', 'c'];
letters.splice(2, 1, 'd', 'e'); 
// letters is now ['a', 'b', 'd', 'e'];
```

## `.slice`

Not to be confused with `.splice`, `.slice` copies an array:

```js
const letters = ['a', 'b', 'c'];
const copy = letters.slice();
copy.splice(1, 2);
console.log(copy);
// ['a']
console.log(letters);
// ['a', 'b', 'c']
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
const array = ['a', 'b', 'c'];
array.forEach((element, index) => {
    console.log(index, '-', element);
});
// 0 - a
// 1 - b
// 2 - c
```

### `.map` 

Creates a new array, passing each element to the given function
and putting the return value in the same index in the new array:

```js
const numbers = [1, 2, 3];
const squared = numbers.map(x => x * x);
console.log(squared);
// [1, 4, 9]

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
    squared.push(x * x);
});
```

And should be replaced with a `.map` operation:

```js
const numbers = [1, 2, 3];
const squared = numbers.map(x => x * x);
```

### `.filter`

Some of the array methods, like `.filter`, take functions called
"predicates" that test each element for some condition and return true
or false.  Other examples are `.find`, `.findIndex`, `.some`, and `.every`.

`.filter` returns a new array with only those elements that return "truthy" 
when passed to the predicate function:

```js
const numbers = [1, 7, 4, 2, 9, 3, 7];
const small = numbers.filter(n => n < 5);
console.log(small);
// [1, 4, 2, 3];
```

### `.find` and `.findIndex`

These are also predicate based array methods (like `.filter`). 
Instead of returning a new array, `.find` returns the first element
"found" (returns a truthy value from the callback function). Returns 
`undefined` if no match.

`findIndex` returns the index of the first found element. Returns
`-1` if no match.

```js
const fruits = [
    { id: 21, name: 'apple' },
    { id: 72, name: 'pear' },
    { id: 12, name: 'banana' },
    { id: 34, name: 'mango' }
];

const found = fruits.find(fruit => fruit.id === 72);
console.log(found);
// { id: 72, name: 'pear' }

const index = fruits.findIndex(fruit => fruit.id === 72);
console.log(index);
// 1
```

### `.indexOf`

`indexOf` is a shorthand case for `.findIndex` where the match is
based on equality of the value:

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
rather than creating a new array (it does return a value of the array itself). 

It also has a different style of callback function than the other array methods, a comparison function that takes two items and you indicate the relative sort order by returning a negative number, zero, or a positive number.

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

The default sort is lexical sorting (sorted alphabetically).

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

 
