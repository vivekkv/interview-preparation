# JAVASCRIPT INTERVIEW QUESTIONS

[JS Prototype](#Javascript-Prototype-Questions)
[Currying](#Currying)
[Prmoise](#Promises)
[Closure](#Closures)

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
```
> primitive data types can store only a single value
> top store multiple values we need to use non primitive data type
```

### What do you mean by strict mode in javascript and characteristics of javascript strict-mode?
* Duplicate arguments are not allowed by developers.
* Duplicate arguments are not allowed by developers.
* In strict mode, you won't be able to use the JavaScript keyword as a parameter or function name.
* Engineers will not be allowed to create global variables in 'Strict Mode.

### Explain “this” keyword.
* The “this” keyword refers to the object that the function is a property of
* The value of the “this” keyword will always depend on the object that is invoking the function.

# Explain call(), apply() and, bind() methods.

### call():
> This method invokes a method (function) by specifying the owner object

```
function sayHello(){
  return "Hello " + this.name;
}
        
var obj = {name: "Sandy"};
        
sayHello.call(obj);
```

### apply(): 
> The apply method is similar to the call() method. The only difference is that, call() method takes arguments separately whereas, apply() method takes arguments as an array.

```
function saySomething(message){
  return this.name + " is " + message;
}        
var person4 = {name:  "John"};
saySomething.apply(person4, ["awesome"]);

```
### bind();
> This method returns a new function, where the value of “this” keyword will be bound to the owner object, which is provided as a parameter.

```
var bikeDetails = {
    displayDetails: function(registrationNumber,brandName){
    return this.name+ " , "+ "bike details: "+ registrationNumber + " , " + brandName;
  }
}
var person1 = {name:  "Vivek"};
var detailsOfPerson1 = bikeDetails.displayDetails.bind(person1, "TS0122", "Bullet");
// Binds the displayDetails function to the person1 object
detailsOfPerson1();
//Returns Vivek, bike details: TS0122, Bullet
```

###  Explain Scope and Scope Chain in javascript.
> Scope in JS determines the accessibility of variables and functions at various parts of one’s code.
* Global Scope
* Local or Function Scope
* Block Scope

# Closures
> A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

> In JavaScript, a closure is a function that has access to the variables in the outer scope even after the outer function has completed executing. This is possible because the inner function maintains a reference to the variables in the outer scope.

```
function outerFunction() {
  let outerVariable = 'I am a variable in the outer function';

  function innerFunction() {
    console.log(outerVariable);  // Output: "I am a variable in the outer function"
  }

  return innerFunction;
}

let closure = outerFunction();
closure();  // Output: "I am a variable in the outer function"

```
