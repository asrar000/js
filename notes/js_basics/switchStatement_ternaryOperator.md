### Why choose swtich statement over conditonal(if,else if and else ) statements

if...else statements do the job of enabling conditional code well, but they are not without their downsides. They are mainly good for cases where you've got a couple of choices, and each one requires a reasonable amount of code to be run, and/or the conditions are complex (for example, multiple logical operators). For cases where you just want to set a variable to a certain choice of value or print out a particular statement depending on a condition, the syntax can be a bit cumbersome, especially if you've got a large number of choices.

In such a case, switch statements are your friend — they take a single expression/value as an input, and then look through several choices until they find one that matches that value, executing the corresponding code that goes along with it. 

```js
switch (expression) {
  //Very important that is swtich statement by default is strict equality
  case choice1:
    // run this code
    break;

  case choice2:
    // run this code instead
    break;

  // include as many cases as you like

  default:
    // actually, just run this code
    break;
  
  /*Remember that a break inside the default statement is not required. The default statement itself is also not mandatory. If the value or expression does not match any of the case statements and there is no default statement, the program will simply exit the switch block.
  */
}
```

### An important note about switch statmeent in js
# JavaScript Switch Statements - Equality and Complex Expressions

## Overview

Switch statements are **primarily designed for equality checks**, but there are some nuances worth understanding.

## Standard Switch (Equality Only)

The standard switch uses **strict equality (`===`)** to compare the switch expression with each case:

```javascript
switch (value) {
  case 1:
    // executes if value === 1
    break;
  case 'hello':
    // executes if value === 'hello'
    break;
}
```

## You Can Use Expressions in Cases

While the comparison is equality-based, you **can** use expressions in your case values:

```javascript
const x = 5;
switch (x) {
  case 2 + 3:  // evaluates to 5
    console.log('matched!');
    break;
  case Math.max(1, 2):  // evaluates to 2
    console.log('not matched');
    break;
}
```

## Workaround for Complex Conditions

For complex conditions, you can use `switch(true)` as a pattern:

```javascript
const age = 25;

switch (true) {
  case age < 18:
    console.log('Minor');
    break;
  case age >= 18 && age < 65:
    console.log('Adult');
    break;
  case age >= 65:
    console.log('Senior');
    break;
}
```

This works because each case expression is evaluated, and if it's `true`, it matches `switch(true)`.

## When to Use What

- **Simple equality checks** → use standard switch
- **Complex conditions/ranges** → use if-else or switch(true), Here the if-else conditional block is more readable than
switch(true)
- **Readability matters** → if-else is often clearer for complex logic

## Conclusion

While switch is fundamentally equality-based, there are creative ways to handle more complex scenarios if needed. 

### Simple switch statement mainly focusing on the grouping of case statement

```js
let a = 3;

switch (a) {
  case 4:
    alert('Right!');
    break;

  case 3: // (*) grouped two cases
  case 5:
    alert('Wrong!');
    alert("Why don't you take a math class?");
    break;
  //Here we can see that  no OR(||) is used and also no identation of case 5 under case 3 
  default:
    alert('The result is strange. Really.');
}
```

### ❗❗❗ Dont forget the break statement
It is good practice to include a break statement in the default case, even if your current code does not require it. In the future, you may add new case statements after the last existing one and forget to include a break, assuming it is not necessary. To avoid this risk, it is a good idea to always add a break statement to the last case statement as well. This helps prevent unintentional fall-through behavior and potential bugs when the code is modified later.
***Summary Add break statement always even to default and without default the last case statement for future proofing*** 


### A Complex ternay operator example

```js
let message;

if (login === 'Employee') {
  message = 'Hello';
} else if (login === 'Director') {
  message = 'Greetings';
} else if (login === '') {
  message = 'No login';
} else {
  message = '';
}


/*
This is an if–else if–else block written using strict comparison (===).
Now the same logic will be converted into a complex ternary operator.
*/

message = login === 'Employee' ? 'Hello' :
          login === 'Director' ? 'Greetings' :
          login === '' ? 'No login' : '';

/*
This form of complex ternary operator is discouraged  
because it reduces code readability.
*/

```