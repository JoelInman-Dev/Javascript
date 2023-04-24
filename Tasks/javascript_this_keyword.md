# THIS Keyword | Using it With Traditional Functions and Arrow Functions

The `this` keyword in JavaScript is a special variable that refers to the **current object** or **context**. It is often used inside functions to refer to the object that the function belongs to, or to the object that is being acted upon.

---

## `this` in Traditional Functions
In traditional functions, the value of `this` depends on how the function is called. When a function is called as a method of an object, `this` refers to that object.

```javascript
const person = {
  name: 'Joel',
  sayHello() {
    console.log(`Hello, my name is ${this.name}.`);
  }
};

person.sayHello(); // Hello, my name is Joel.
```

Here, the `sayHello()` function is defined as a method of the person object. So, when I call `person.sayHello()`, `this` refers to the person object, so the output is "*Hello, my name is Joel*"...

---

## `this` in different enclosing lexical contexts

However, the value of `this` can change when a function is called within a *different* context.

```javascript
function sayHello() {
  console.log(`Hello, my name is ${this.name}.`);
}

const person1 = { name: 'Joel' };
const person2 = { name: 'NotJoel' };

person1.sayHello = sayHello;
person2.sayHello = sayHello;

person1.sayHello(); // Hello, my name is Joel.
person2.sayHello(); // Hello, my name is NotJoel.
```

In the above example, I am defining the `sayHello()` function separately from any object (outside of the context of a `person` object for example).  

Then I am adding the function as a method of the `person1` and `person2` objects using the `=` operator. 

Now, when we call `person1.sayHello()`, this refers to the `person1` object, so the output is "*Hello, my name is Joel.*".  

When we call `person2.sayHello()`, this refers to the `person2` object, so the output is "*Hello, my name is NotJoel*"...

---

## `this` in Arrow Functions

On the other hand, arrow functions do not have their own `this binding`. Instead, they inherit the `this` value from the enclosing lexical context.

```javascript
const person = {
  name: 'Joel',
  sayHello: () => {
    console.log(`Hello, my name is ${this.name}.`);
  }
};

person.sayHello(); // Hello, my name is undefined.
```
Here, the `sayHello()` method is defined as an arrow function. Because arrow functions do not have their own `this binding`, `this` in this context refers to the global `this`, which does not have a `name` property. Therefore, the output is "*Hello, my name is undefined*"...

The `this` keyword in JavaScript refers to the current object or context. In traditional functions, the value of `this` depends on how the function is called, while arrow functions inherit the `this` value from the enclosing lexical context.
