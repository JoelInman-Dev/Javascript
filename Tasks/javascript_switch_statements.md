# Switch Statements vs if statements

### A switch statement is a way to execute different code blocks based on the value of a given expression.

Let's say I have a variable called `dayOfWeek`, which represents the day of the week - go figure. It can be either 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', or 'Sunday'.

---

## Using an `if` Statement


```javascript
const dayOfWeek = 'Monday';
```
Now let's say I want to perform different actions based on the value of `dayOfWeek`. I could use a series of **if-else** statements:

```javascript
if (dayOfWeek === 'Monday') {
  // do something
} else if (dayOfWeek === 'Tuesday') {
  // do something else
} else if (dayOfWeek === 'Wednesday') {
  // do something else
} else if (dayOfWeek === 'Thursday') {
  // do something else
} else if (dayOfWeek === 'Friday') {
  // do something else
} else if (dayOfWeek === 'Saturday') {
  // do something else
} else if (dayOfWeek === 'Sunday') {
  // do something else
}
```
This works, but it can be a bit verbose and repetitive. A more concise way to achieve the same thing is to use a switch statement

---

## Using a Switch Statement

```javascript
switch (dayOfWeek) {
  case 'Monday':
    // do something
    break;
  case 'Tuesday':
    // do something else
    break;
  case 'Wednesday':
    // do something else
    break;
  case 'Thursday':
    // do something else
    break;
  case 'Friday':
    // do something else
    break;
  case 'Saturday':
    // do something else
    break;
  case 'Sunday':
    // do something else
    break;
}
```

In this example, the switch statement takes the value of `dayOfWeek` as its expression, and then checks each `case` against it. If the value of `dayOfWeek` matches a `case`, the code block associated with that `case` will be **executed**.

Note that each `case` must end with a `break statement`, which tells JavaScript to exit the switch statement once the code block has been executed. If you don't include a `break statement`, JavaScript will continue to execute the code blocks for all the subsequent cases, *even if they don't match the value of the expression.*  

This is called "falling through", and it can lead to unexpected behavior if you are not careful.

You can also include a `default` case at the end of the switch statement, which will be executed if none of the other cases match the value of the expression, acting as a fallback measure.

---

## Switch Statement 'default'

```javascript
switch (dayOfWeek) {
  case 'Monday':
    // do something
    break;
  case 'Tuesday':
    // do something else
    break;
  // other cases...
  default:
    // do something if none of the other cases match
    break;
}
```
switch statements can be more concise and easier to read than a series of if-else statements, but you need to remember to include a break statement after each case to avoid unexpected behavior.