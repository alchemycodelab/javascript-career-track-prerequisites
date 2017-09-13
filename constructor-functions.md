Constructor Functions
===

Prior to the introduction of the `class` in ES6, constructor functions
where the way to define "classes" in JavaScript. (Classes and constructor
functions work in mostly the same way at runtime).

## Defining the Constructor

The initialization code for an object goes into the constructor function:

```js
function Animal(name, type) {
    this.name = name;
    this.type = type;
}

const cat = new Animal('felix', 'cat');
const dog = new Animal('lassie', 'dog');

console.log(cat.name, dog.name);
// felix lassie
```

## Methods

Methods are a name for functions called on an object. For constructor
functions, we define methods on the prototype. This allow all instances
of that type of object to share a common set of functions.

```js
function Animal(name, type) {
    this.name = name;
    this.type = type;
    this.stomach = [];
    this.happiness = 1;
}

Animal.prototype.feed = function(food) {
    this.stomach.push(food);
    this.happiness += 2;
}
Animal.prototype.play = function(toy) {
    if(toy.animalType !== this.type) return;
    this.happiness += 1;
} 

const cat = new Animal('felix', 'cat');
const dog = new Animal('lassie', 'dog');
const ball = new Toy('ball', 'dog'); // name and type of toy

cat.feed('chicken');
dog.feed('chicken');

cat.play(ball);
dog.play(ball);

console.log(cat.happiness, dog.happiness);
// 2 3
```

## Chaining

Chaining refers to the an object tht returns itself so that additional
methods can be called directly from the prior method call.

```js
function Animal(name, type) {
    this.name = name;
    this.type = type;
    this.stomach = [];
    this.happiness = 1;
}

Animal.prototype.feed = function(food) {
    this.stomach.push(food);
    this.happiness += 2;
    return this;
}

Animal.prototype.play = function(toy) {
    if(toy.animalType !== this.type) return;
    this.happiness += 1;
    return this;
} 

Animal.prototype.potty = function() {
    this.stomach.shift();
    this.happiness += 1;
    return this;
} 

const dog = new Animal('lassie', 'dog');
const ball = new Toy('ball', 'dog'); // name and type of toy

dog.play(ball).feed('chicken').feed('bones').potty();

console.log(dog.happiness);
// 7
```
