# Equality Comparisons and Sameness

There are three value comparison operations available in Javascript. These are `Strict Equality`, `Equality` and `Object.is()`. The type of value comparison operator you choose will inevitably depend on the sort of comparison you want to perform.

## Assignment ( `=` )

A single equals operator ( `=` )does not process any type of comparison between values. Instead a single equals operator ( `=` ) is used as the operator to assign a value.

```javascript
const this = 'that';
```

## Equality ( `==` )
The equality operator (==) will attempt to convert the operands to the same type before comparing them. For example, if you compare the string "1" to the number 1, the equality operator will convert the string to a number and then compare the two numbers. This means that the following code will return `true`:

```javascript
const a = "1";
const b = 1;

console.log(a == b); // true

```

## Strict Equality ( `===` )
The strict equality operator (===), on the other hand, will not attempt to convert the operands to the same type. Instead, it will compare the operands directly. This means that the following code will return `false`:

```javascript
const a = "1";
const b = 1;

console.log(a === b); // false, a string is not equal to an integer

```

## Object.is`()`
