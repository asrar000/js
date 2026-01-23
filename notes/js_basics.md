# (1)#################################################################################################################
📌 Function Arguments in JavaScript
✅ Calling Functions Without Arguments

In JavaScript, it is possible to call a function without passing arguments, even if parameters are defined.

If a parameter is defined and used inside the function

And the function is called without providing a corresponding argument

And no default value is assigned

➡️ The parameter’s value becomes undefined

This behavior is different from many other programming languages, where missing required arguments usually cause a compile-time or runtime error.

🔍 Example
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


Using default values prevents unexpected undefined behavior.

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


Extra arguments are ignored

Unless accessed via:

arguments object

Rest parameters (...args)

# ####################################################################################################################