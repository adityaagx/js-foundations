# 📘 JavaScript Execution Context

Execution Context is the environment where JavaScript runs code, storing variables, functions, scope, and `this`.  
Every execution context is created in two phases — Creation Phase (memory setup) and Execution Phase (code runs line by line using the call stack).

---

## 🧠 1. What is Execution Context?

An **Execution Context** is the environment in which JavaScript code is evaluated and executed.

Whenever JavaScript runs code, it creates a special environment to handle:

* Variables
* Functions
* Scope
* `this` keyword

Think of it like:

> 📦 “A box where JavaScript stores everything needed to run your code.”

---

## ⚡ 2. Types of Execution Context

JavaScript has **three types** of execution contexts:

### 1️⃣ Global Execution Context (GEC)

* Created when the JS file first runs
* Only created once
* `this` refers to:

  * `window` (in browsers)
  * `global` (in Node.js)

Example:

```js
var name = "Aditya";

console.log(this); // window (in browser)
```

---

### 2️⃣ Function Execution Context (FEC)

* Created every time a function is invoked
* Each function call gets its own separate execution context

Example:

```js
function greet() {
  var message = "Hello";
  console.log(message);
}

greet();
```

When `greet()` runs → a new execution context is created.

---

### 3️⃣ Eval Execution Context (Rarely used)

Created when code runs inside `eval()`.

```js
eval("var x = 10");
```

⚠️ Avoid using `eval()` in real projects.

---

## 🔥 3. How Execution Context is Created (Two Phases)

Every execution context has **two phases**:

---

# 🏗 Phase 1: Creation Phase (Memory Creation Phase)

Before executing code, JavaScript scans it and:

### ✔ Allocates memory for:

* Variables → set to `undefined`
* Functions → store full function definition

Example:

```js
console.log(a);
var a = 10;
```

Behind the scenes (Creation Phase):

```
a → undefined
```

That’s why this prints:

```
undefined
```

---

# 🚀 Phase 2: Execution Phase

Now JavaScript executes code line by line:

```js
var a = 10;
```

Now:

```
a → 10
```

---

## 🎯 4. Execution Context Contains 3 Important Things

Every execution context has:

### 1️⃣ Variable Environment

Stores:

* Variables
* Function declarations

---

### 2️⃣ Scope Chain

Determines:

* Where JS looks for variables

Example:

```js
var a = 10;

function test() {
  console.log(a);
}

test();
```

JS doesn’t find `a` inside `test()`, so it looks outside → finds it in global scope.

That lookup system = **Scope Chain**

---

### 3️⃣ `this` Keyword

Depends on how function is called.

Example:

```js
console.log(this); 
```

In browser → `window`

---

## 🧩 5. Execution Stack (Call Stack)

JavaScript is **single-threaded** → it executes one thing at a time.

It uses something called the **Call Stack**.

Think of it like a stack of plates:

* When function is called → pushed onto stack
* When function finishes → popped from stack

Example:

```js
function one() {
  two();
}

function two() {
  console.log("Hello");
}

one();
```

### How Stack Works:

```
Global()
→ one()
→ two()
```

After execution:

```
two() removed
one() removed
Global remains
```

---

## 🎬 6. Step-by-Step Behind the Scenes Example

```js
var x = 5;

function multiply(num) {
  return num * 2;
}

var result = multiply(x);
console.log(result);
```

### What Happens Internally:

### Global Creation Phase:

```
x → undefined
multiply → function definition
result → undefined
```

### Global Execution Phase:

```
x → 5
result → multiply(5)
```

### Function Execution Context Created:

```
num → 5
```

Returns:

```
10
```

Now:

```
result → 10
```

Final Output:

```
10
```

---

# 🧪 Practice Section

---

## 🔹 Practice 1

What will this print?

```js
console.log(a);
var a = 20;
```

Global Creation -
a = undefined

Global execution -
it prints undefined because during the creation phase, a was allocated memory and initialized with undefined.

Js runs line by line, a value get updates to 20 after undefined but it never prints.

---

## 🔹 Practice 2

Predict output:

```js
function test() {
  console.log(a);
}

var a = 10;
test();
```

Global creation Phase -
Memory gets allocated
Function test definition
a = undefined

Global & Function Execution

var = 10

Function execution context -

test function runs
checks for local variables and parameters.
It creates a Scope Chain link to access outer Global variables.

Prints 10 on the screen.

---

## 🔹 Practice 3 (Call Stack Understanding)

```js
function first() {
  console.log("First");
  second();
}

function second() {
  console.log("Second");
}

first();
```

Write the stack order.

Global creation phase - 
First - function definition
Second - function definiton

Execution Phase -

First function first gets called, goes to the stack, 
prints First on the screen and calls function second.

Function second goes to the stack, runs and prints Second.

Function second is removed.
Function first is rmeoved.

---

# 🎯 Why This Topic is IMPORTANT

If you master execution context:

* Hoisting becomes easy
* Scope becomes easy
* Closures become easy
* `this` becomes easy
* Async JS becomes easier

This is the **foundation of advanced JavaScript**.

---
