# Function Naming Best Practices

## Functions Represent Actions

Functions represent **actions**, so their names should usually be **verbs**. A good function name should be:

* **Brief**
* **Accurate**
* **Descriptive**

The goal is that someone reading the code can quickly understand **what the function does** just by reading its name.

---

## Use Verb Prefixes Consistently

A widespread and effective practice is to start function names with a **verb prefix** that describes the action being performed.

> ⚠️ The entire team should agree on what each prefix means and use them consistently.

### Common Prefixes and Their Meanings

| Prefix    | Meaning               | Expected Return            |
| --------- | --------------------- | -------------------------- |
| `show…`   | Display something     | usually no return          |
| `get…`    | Retrieve a value      | value                      |
| `calc…`   | Perform a calculation | calculated result          |
| `create…` | Create something      | created object             |
| `check…`  | Perform a check       | boolean (`true` / `false`) |

### Examples

```js
showMessage(..)      // shows a message
getAge(..)           // returns the age
calcSum(..)          // calculates and returns a sum
createForm(..)       // creates and returns a form
checkPermission(..)  // returns true or false
```

With clear prefixes, a quick glance at a function name tells you:

* **What it does**
* **What kind of value it returns**

---

## One Function = One Action

A function should do **exactly what its name suggests — nothing more**.

If two independent actions are needed, they usually deserve **two separate functions**. If those actions are commonly used together, you can create a **third function** that calls both.

### ❌ Bad Examples

```js
getAge()          // ❌ Bad if it also shows an alert
createForm()      // ❌ Bad if it also adds the form to the DOM
checkPermission() // ❌ Bad if it also shows access messages
```

These names imply a **single responsibility**, and adding extra behavior violates that expectation.

> You may define different meanings for prefixes, but once defined, **all functions using the same prefix must follow the same rules**.

---

## Ultrashort Function Names (Rare Exceptions)

Some libraries use extremely short function names:

* jQuery: `$()`
* Lodash: `_()`

These are **special cases**, usually for functions that are:

* Used very frequently
* Widely recognized

👉 In general, **avoid ultrashort names** in normal code. Prefer clarity over brevity.

---

## Functions Are Better Than Comments

Well-written functions often act as **self-documenting comments**.

* Functions should be **small**
* Functions should do **one thing**
* Large logic should be split into **smaller functions**

This makes code:

* Easier to read
* Easier to test
* Easier to debug

---

## Example: Improving Readability with Functions

### ❌ Less Readable Version

```js
function showPrimes(n) {
  nextPrime:
  for (let i = 2; i < n; i++) {
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }
    alert(i); // a prime
  }
}
```

### ✅ More Readable Version (Self-Describing Code)

```js
function showPrimes(n) {
  for (let i = 2; i < n; i++) {
    if (!isPrime(i)) continue;
    alert(i); // a prime
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if (n % i == 0) return false;
  }
  return true;
}
```

### Why This Is Better

* `isPrime()` clearly describes **what the check does**
* The logic reads almost like natural language
* The code is **self-describing**

---

## Key Takeaways

* Use **verbs** for function names
* Use **consistent prefixes**
* One function should perform **one action only**
* Prefer **clarity over cleverness**
* Functions often replace the need for comments

> Clean function names make your code readable, maintainable, and professional.
