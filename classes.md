Classes
===

## Defining the Classes

The `class` keyword precedes the name of the class and introduces
a code block for specifying the properties and methods of the class.
There is a special `constructor` method used for initializing class
instances. The other defined methods are assigned to the class `prototype`
and will be shared by all created class instances.

```js
class Animal {
    constructor(name, type) {
        this.name = name;
        this.type = type;
    }

    speak() {
        return `I am ${this.name} the ${this.type}!`;
    }
}

const cat = new Animal('felix', 'cat');
const dog = new Animal('lassie', 'dog');

console.log(cat.speak())
// I am felix the cat!
console.log(dog.speak())
// I am lassie the dog!
```

Notice that unlike an object literal, there are no commas separating the methods
of class.

## Methods

"Method" is a name for function that is a property of an object. For constructor
functions, we define methods on the prototype. This allow all instances
of that type of object to share a common set of functions.

```js
class Toy {
    constructor(name, animalType) {
        this.name = name;
        this.animalType = animalType;
    }
}

class Animal {
    constructor(name, type) {
        this.name = name;
        this.type = type;
        this.stomach = [];
        this.happiness = 1;
    }

    feed(food) {
        this.stomach.push(food);
        this.happiness += 2;
    }

    play(toy) {
        if(toy.animalType !== this.type) return;
        this.happiness += 1;
    } 
}

const cat = new Animal('felix', 'cat');
const dog = new Animal('lassie', 'dog');

const ball = new Toy('ball', 'dog');

cat.feed('chicken');
dog.feed('chicken');

cat.play(ball);
dog.play(ball);

console.log(cat.happiness, dog.happiness);
// 2 3
```

## Chaining

Chaining refers to the an object that returns itself on method
calls so that additional methods can be called directly from
the prior method call.

```js
class Animal {
    constructor(name, type) {
        this.name = name;
        this.type = type;
        this.stomach = [];
        this.happiness = 1;
    }

    feed(food) {
        this.stomach.push(food);
        this.happiness += 2;
        return this;
    }

    play(toy) {
        if(toy.animalType !== this.type) return;
        this.happiness += 1;
        return this;
    } 

    potty() {
        this.stomach.shift();
        this.happiness += 1;
        return this;
    } 
}

const dog = new Animal('lassie', 'dog');
const ball = new Toy('ball', 'dog');

dog.play(ball).feed('chicken').feed('bones').potty();

console.log(dog.happiness);
// 7
```
