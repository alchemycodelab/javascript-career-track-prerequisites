Blocks
===

## Indent blocks properly

```js
if(foo) {
  console.log('i am indented');
}
```

## Identify Blocks

Differentiate `{` `}` used in blocks versus other uses in JavaScript like
object literals:

```js
if(foo) { //open block

  return { // start object literal
    name: foo
  }; // end object literal

} //close block
```

## Omitting Blocks

With single statements, it is often appropriate to omit blocks:

```js
if(foo) console.log('single statement');

for(let i=0; i < cats.length; i++) save(cats[i]);

let parent;
while(node = node.parent) parent = node;
```

## Scope variables via `const` and `let` to blocks

```js
if(foo) {
  let x = 12;
  console.log('square of 12', Math.power(x, 2));
}

console.log(x); // error, x is not defined
```