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

### `.reduce`

`.reduce` is used to transform an array into another data structure
based on visiting each element in the array. 

It adds another parameter to the callback function of the data 
structure being used to accumulate the result (sometimes called the 
"accumulator"). This must be returned from each call to the supplied 
function in order to be supplied to the next function call or to 
provide the final value. 

The `.reduce` call itself also takes a second parameter that is the initial value for the accumulator:

```js
const numbers = [3, 2, 9, 4];
const sum = numbers.reduce((total, n) => {
    return total + n;
    return total;
}, 0);
console.log(sum);
// 18
```

If the second initial value is omitted, the first call
to reduce is the first and second elements of the array.
The above `sum` can be written more succinctly as:

```js
const numbers = [3, 2, 9, 4];
const sum = numbers.reduce((total, n) => total + n);
console.log(sum);
// 18
```

`.reduce` can also be used for more complex transformations:

```js
const animals = [
    { type: 'cat',  name: 'felix'    }
    { type: 'bird', name: 'polly'    }
    { type: 'dog',  name: 'lassie'   }
    { type: 'cat',  name: 'garfield' }
    { type: 'bird', name: 'tweety'   }
];

const animalsByType = animals.reduce((byType, animal) => {
    if(!byType[animal.type]) byType[animal.type] = [];
    byType[animal.type].push(animal.name);
    return byType;
}, {});

console.log(animalsByType);
// {
//     cat: ['felix', 'garfield'],
//     dog: ['lassie'],
//     bird: ['polly', 'tweety']
// }
```

### `.sort`

Unlike the previous array methods, calling `.sort` _changes the array_
rather than creating a new array. It also has a different style of 
callback function than the other array methods