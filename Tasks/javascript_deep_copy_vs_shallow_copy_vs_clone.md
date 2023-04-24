# Javascript Deep Copy, Shallow Copy and Clone

## Defining Deep Copy vs Shallow Copy

When we want to create a copy of an object in Javascript, we can use either a `shallow copy` or a `deep copy`.

A `shallow copy` creates a NEW object that shares some or all of the properties of the original object. 

In other words, the NEW object points to the same memory location as the original object for some or all of its properties.

## Shallow Copy

```javascript
const originalObj = {a: 1, b: 2};
const shallowCopy = {...originalObj};
```

Above, when defining `shallowCopy`, I am using the spread operator `(...)` to create a new object (`shallowCopy`) - which has the same properties as the `originalObj`. 

However, the `shallowCopy` points to a **different** memory location than the `originalObj`, except for the **property values**, which are using the same memory location as the `originalObj`. Effectively `shallowCopy` is simply a reference to the `originalObj`.

---

## Deep Copy

A deep copy, on the other hand, creates a NEW object that has all the properties of the `originalObj`, but with new memory locations for all its properties. Meaning any changes to a `deepCopy`'s property value will have no bearing on the `originalObj`'s property values.

```javascript
const originalObj = {a: 1, b: {c: 2}};
const deepCopy = JSON.parse(JSON.stringify(originalObj));
```

In this example, I am using `JSON.stringify()` to convert the `originalObj` to a JSON string, and then using `JSON.parse()` to convert the JSON string back to an object. This creates a new object (`deepCopy`) with new memory locations for all the properties, *including nested objects.*

Deep copying can be slower and more memory-intensive than shallow copying, especially for large or complex objects.

Additionally, `deep copying` may not work for all types of objects, such as [objects with circular references or functions](https://github.com/joelinman-nxp/Javascript/blob/main/Tasks/javascript_objects_with_circular_references).

In general, we should choose between shallow and deep copying based on our specific use case and the structure of the object we want to make a copy of.

---

## Cloning

In JavaScript, there are different ways to `clone` an object, which means creating a copy of an object that has the same `properties` and `values` as the original object.

One way to clone an object is to use the `Object.assign()` method.

```javascript
const originalObj = {a: 1, b: 2};
const cloneObj = Object.assign({}, originalObj);
```
With this example, I'm using `Object.assign()` to create a new object (`cloneObj`) and assign all the `properties` of the `originalObj` to it. The first argument of `Object.assign()` is an empty object (`{}`), which will be the target object that receives the `properties`.

Another way to `clone` an object is to use the spread operator `(...)` which I will go into more, inside my [Destructing Objects and Arrays with JavaScript](https://github.com/joelinman-nxp/Javascript/blob/main/Tasks/javascript_) write up.

```javascript
const originalObj = {a: 1, b: 2};
const cloneObj = {...originalObj};
```

Above I am using the spread operator `(...)` to create a new object (`cloneObj`) and assign all the `properties` of the `originalObj` to it.

Both of these cloning methods featured so far create `shallow copies` of the object, which means that if the original object has properties that are themselves objects or arrays, those properties will be referenced to the same memory location in the new object.

If you need to create a deep copy of an object, you can use JSON.parse() and JSON.stringify() as shown in the above Deep copy example that I covered.