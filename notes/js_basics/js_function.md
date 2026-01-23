# 📌 Function Arguments in JavaScript

## ✅ Calling Functions Without Arguments

In JavaScript, it is possible to call a function **without passing arguments**, even if parameters are defined.

If:
- A parameter is defined and used inside the function
- The function is called without providing a corresponding argument
- No default value is assigned  

➡️ The parameter’s value becomes **`undefined`**

This behavior is different from many other programming languages, where missing required arguments usually cause a **compile-time** or **runtime error**.

---

## 🔍 Example

```js
function greet(name) {
  console.log(name);
}

greet(); // undefined
Explanation:
name exists

No argument is passed

name === undefined

❌ No error occurs

🧠 Why JavaScript Allows This
JavaScript behaves this way because:

JavaScript is dynamically typed

Function parameters are not enforced

Missing arguments automatically become undefined

JavaScript does not check the number of arguments passed

⚠️ Real Danger (Important)
function add(a, b) {
  return a + b;
}

add(2); // NaN (2 + undefined)
⚠️ This often leads to silent bugs, not immediate errors.

✅ Default Parameters (Safer Approach)
function add(a = 0, b = 0) {
  return a + b;
}

add(2); // 2
Using default values prevents unexpected undefined behavior and makes functions safer.

🆚 Comparison with Other Languages
Language	Missing Argument Behavior
JavaScript	Parameter becomes undefined
Python	❌ Error (unless default value is provided)
Java / C / C++	❌ Compile-time or runtime error
TypeScript	❌ Compile-time error (by default)
🧠 Extra Detail: Extra Arguments
JavaScript also allows extra arguments to be passed.

function f(a) {
  console.log(a);
}

f(1, 2, 3); // 1
Behavior:
Extra arguments are ignored

Unless accessed via:

arguments object

Rest parameters (...args)

⚠️ Two Important Things to Know About Functions
1️⃣ Default Parameter as a Function
If a function parameter has another function as its default value, and no argument is passed,
➡️ that default function will be called every time the function is invoked.

function getValue() {
  console.log("called");
  return 10;
}

function test(x = getValue()) {
  return x;
}

test(); // "called"
test(); // "called"
2️⃣ Prefer Parameters Over Side Effects
It is always easier to understand a function that:

Accepts parameters

Works with them

Returns a result

Compared to a function that:

Takes no parameters

Modifies outer variables as a side effect

✅ Pure, parameter-driven functions are:

Easier to read

Easier to test

Easier to debug

✅ Key Takeaway
JavaScript does not enforce argument counts

Missing arguments become undefined

Default parameters prevent bugs

Clear function inputs lead to cleaner, safer code