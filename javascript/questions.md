# JAVASCRIPT INTERVIEW QUESTIONS

[JS Prototype](#Javascript-Prototype-Questions)

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