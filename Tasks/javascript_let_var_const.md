# Understanding the differences between `let`, `var` and `const`

In JavaScript, we can declare a variable in different ways by using different keywords. Each keyword holds some specific reason or feature in JavaScript.

In JavaScript, a **`block`** is a section of code that is enclosed within curly braces `{}`. A **`block`** can contain any number of statements, including variable declarations, loops, conditional statements, function declarations, and more.

**`Blocks`** are used to group statements together and create a new scope. Variables declared inside a block are only accessible within that block and any nested blocks. This is known as block scoping and is a feature that was introduced in **ECMAScript 6 (ES6)**.  

Blocks are commonly used with control flow statements like `if`, `for`, and `while`.

---

## Let

### `let` is used to declare a block-scoped variable. Which means that the variable can only be accessed within the block of code where it was defined. It can also be reassigned a new value.

```js
// let example
function letExample() {
  let y = 10;
  if (true) {
    let y = 20; // different variable from above
    console.log(y); // Output: 20
  }
  console.log(y); // Output: 10
}
```

---

## Var
### `var` has function scope. In other words, variables declared with `var` are accessible throughout the entire function.  
### `var` was the only way to declare variables before **ES6**, and it has some different behavior compared to `let` and `const`.
```js
// var example
function varExample() {
  var x = 10;
  if (true) {
    var x = 20; // same variable as above
    console.log(x); // Output: 20
  }
  console.log(x); // Output: 20
}
```

---

## Const

### `const` is used to declare variables that **cannot** be reassigned to a new value. `const` variables must be assigned a value when they are declared, and that value **cannot** be changed.

```js
const z = 10;
z = 20; // Throws an error - Assignment to constant variable.
```

### It's worth noting that while the value of a const variable cannot be changed, if that value is an object or an array, its properties or elements can still be modified.  
  
```js
const arr = [1, 2, 3];
arr.push(4); // OK
console.log(arr); // Output: [1, 2, 3, 4]

const obj = {a: 1, b: 2};
obj.c = 3; // OK
console.log(obj); // Output: {a: 1, b: 2, c: 3}

```