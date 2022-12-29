# JAVASCRIPT INTERVIEW QUESTIONS

[JS Prototype](#Javascript-Prototype-Questions)
[Currying](#Currying)

### Javascript Prototype Questions

> Each object has a private property which holds a link to another object called its prototype
> const a = () => {}; // a.prototype = undefined (arrow function does not have prototype)
> [see more at: https://medium.com/@ajmeyghani/interview-questions-1145e3763bce]

```
function Animal(name, energy) {
    this.name = name;
    this.energy = energy;
}
Animal.prototype.eat = function(amount) {
    this.energy += amount;
}
Animal.prototype.play = function(length) {
    this.energy -= length;
}
function Dog(name, energy, breed) {
    Animal.call(name, energy);
    this.breed = breed;
}
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.bark = function() {
    console.log('woof woof');
    this.energy -= .1
}

let Charlie = new Dog('Charlie', 100, 'Lab');
Charlie.bark();
console.log(Charlie.constructor);

```

### Currying
> Currying is a transformation of a function with multiple arguments into a sequence of nested functions with a single argument.

```
function curry(f) { // curry(f) does the currying transform
  return function(a) {
    return function(b) {
      return f(a, b);
    };
  };
}

// usage
function sum(a, b) {
  return a + b;
}

let curriedSum = curry(sum);

alert( curriedSum(1)(2) );
```

### Promises
> Javascript promise is an object that acts as a proxy for an asynchronous function that is supposed to complete at some point.
[solve this at: https://www.codingame.com/playgrounds/347/javascript-promises-mastering-the-asynchronous/its-quiz-time]
[more at: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261]

> It will be in one of 3 possible states:
* Fulfilled
* Pending
* Rejected

```

const promise = new Promise((resolve, reject) => {
    reject(Error('Some Error Occurred'));
}).catch(error => console.log(error))
.then(error => console.log(error));

> Some error occurred
> undefined
```




