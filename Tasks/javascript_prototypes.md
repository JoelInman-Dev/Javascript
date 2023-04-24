# What are Javascript Protoypes?

In JavaScript, every object has a *special* internal property called `[[Prototype]]` that refers to another object.  
This other object is known as the object's "prototype", and it's used as a fallback source of default properties and methods for the object.  
Suppose we have an `object` called `person`, which has two properties: `name` and `age`.

```javascript
const person = {
  name: 'Joel',
  age: 33,
  hourlyRate: 10,
};
```
Now, let me create another `object` called `employee`, which is supposed to represent an employee in a company. I want the `employee object` to inherit the `name` and `age` properties from the `person object`, so I can achieve that by using the `Object.create()` method:

```javascript
const employee = Object.create(person);
employee.id = 10980;
employee.jobTitle = 'Developer';
employee.timeAtWork = 40; // hours
employee.wages = function() { return this.hourlyRate * this.timeAtWork; };
```
Using this `Object.create()` method, I can create a new `object` called `employee` that has `person` as its `prototype`. I then add a couple of new properties to the `employee object` called `id`, `jobTitle` & `hourlyRate`.  

Now, if I try to access the `name` property of `employee`, JavaScript will first look for it in the `employee` object. Since it's not found there, JavaScript will then look for it in the `person object` (which is the `employee's prototype`).  

If it's found there, JavaScript will use that value. Otherwise, it will return `undefined`.

```javascript
console.log( employee.name ); // 'Joel'
console.log( employee.id ); // 10980
console.log( employee.addressPostcode ); // Underfined
console.log( parseInt( employee.wages() ) ); // 400
```
JavaScript `prototypes` allow us to create objects that inherit `properties` and `methods` from other `objects`.  
The `create()` method, and JavaScript will automatically use the `prototype` as a fallback source of `properties` and `methods` when they're not found in the `object` itself.