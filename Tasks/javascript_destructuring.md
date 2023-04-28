# Destructuring Objects & Arrays

Destructuring is a way to unpack the values from an array or object into separate variables. This can be useful when you need to work with the individual values of an array or object, rather than the entire array or object itself.

---

## Destructuring Arrays

Here's an example of how to destructure an array:

```js
const vehicles = ['Audi A6', 'Yamaha R1', 'Toyota Hilux'];


// Destructuring the array into three separate variables
const [car, motorcycle, pickup] = vehicles;

console.log(car); // "Audi A6"
console.log(motorcycle); // "Yamaha R1"
console.log(pickup); // "Toyota Hilux"
```

The destructuring syntax uses square brackets `[]` to surround the names of the variables that you want to create. The names of the variables must be in the order of the items within the array as there are no key/value relationships like in an object. This also means you are free to name your variables however you want.

---

## Destructuring Objects

You can also use destructuring to unpack the values from an object:

```js
const car = {
  make: 'Audi',
  model: 'A6',
  engine: {
    fuel: 'Diesel',
    engineSize: '3.0',
    horsepower: 300,
  },
  colour: 'Black',
  tintedWindows: true,
  extras: {
    spareWheel: true,
    powerSteering: true,
    soundSystemUpgrade: false
  }
};

// Destructuring the object into three separate variables
const { make, model, engine, ...carMeta } = car;

console.log(make); // "Audi"
console.log(model); // "A6"
console.log(engine); // { fuel: 'Diesel', engineSize: '3.0', horsepower: 300 }
console.log(carMeta) // { colour: 'Black', tintedWindows: true, extras: { spareWheel: true, powerSteering: true, soundSystemUpgrade: false } }
```

The destructuring syntax for objects is similar to the syntax for arrays. The only difference is that you use curly braces `{}` to surround the names of the variables that you want to create. The names of the variables must match the names of the properties in the object.

---

## Default Values

You can also use destructuring to set default values for variables. The following code will set the `transmission` variable to the value of `"Automatic"` **if** the `transmission` property is not defined in the object:

```js
const car = {
  make: 'Audi',
  model: 'A6',
  engine: {
    fuel: 'Diesel',
    engineSize: '3.0',
    horsepower: 300,
  },
  colour: 'Black',
  tintedWindows: true,
  extras: {
    spareWheel: true,
    powerSteering: true,
    soundSystemUpgrade: false
  }
};


// Destructuring the object into separate variables, with a default value for transmission
const { make, model, engine: { transmission = "automatic", ...engine}, ...carMeta  } = car;

console.log(make); // "Audi"
console.log(model); // "A6"
console.log(engine); // { fuel: 'Diesel', engineSize: '3.0', horsepower: 300 }
console.log(transmission); // "Automatic"
console.log(carMeta); // { colour: 'Black', tintedWindows: true, extras: { spareWheel: true, powerSteering: true, soundSystemUpgrade: false } }
```

---

## Destructuring Functions

You can also use destructuring to pass multiple arguments to a function. 

For example, the following code snippet I have written will pass the `make`, `horsepower` and a new `transmission` property of the `car` object to the `drivingAway` function:

```js
// Car Object 
const car = {
  make: 'Audi',
  model: 'A6',
  engine: {
    fuel: 'Diesel',
    engineSize: '3.0',
    horsepower: 300,
  },
  colour: 'Black',
  tintedWindows: true,
  extras: {
    spareWheel: true,
    powerSteering: true,
    soundSystemUpgrade: false
  }
};

// Passing destructured properties as function parameters 
function drivingAway({ make, engine: {horsepower, transmission = "Automatic"} }) {
    
  console.log( `ooh, look at you in your new ${transmission} ${make}, speeding off with your ${horsepower}bhp.`);

}

drivingAway(car); // "ooh, look at you in your new Automatic Audi, speeding off with your 300bhp."
```
