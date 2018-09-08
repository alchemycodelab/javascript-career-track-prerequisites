Blocks
===

## Indent blocks properly

All child code with the block should be indented one level. There should
never be anything in the block that has the same left-margin as the parent
containing block.

```js
if(foo) {
  console.log('I am indented');
}
```

## Identify us of curly-braces for blocks

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

When declaring `const` and `let` variables, they are scoped
to the containing block:

```js
if(foo) {
  let x = 12;
  console.log('square of 12', Math.power(x, 2));
}

console.log(x); // error, x is not defined
```