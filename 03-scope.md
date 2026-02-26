# 📘 JavaScript Scope (From First Principles)

Scope defines where variables are accessible in JavaScript.  
JavaScript uses lexical scoping, meaning scope depends on where functions are written, forming a scope chain.

---

## 🧠 1. What is Scope?

Scope determines **where variables are accessible** in your code.

In simple words:

Scope answers the question —  
👉 "From where can I access this variable?"

---

## 🏗 2. First Principle: Why Does Scope Exist?

Imagine if every variable was accessible everywhere.

- Variables would collide.
- Bugs would increase.
- Code would become unpredictable.

So JavaScript creates boundaries.

Those boundaries are called **Scopes**.

---

## 📦 3. Types of Scope in JavaScript

JavaScript has 3 main types of scope:

1. Global Scope  
2. Function Scope  
3. Block Scope  

---

# 🌍 1️⃣ Global Scope

A variable declared outside any function or block belongs to the Global Scope.

It can be accessed from anywhere.

```js
var name = "Aditya";

function greet() {
  console.log(name);
}

greet(); // Aditya
```

Here:

- `name` is global
- Accessible inside the function

⚠️ Global variables stay in memory for the lifetime of the program.

---

# 🏠 2️⃣ Function Scope

Variables declared inside a function are only accessible inside that function.

```js
function test() {
  var message = "Hello";
  console.log(message);
}

test();
console.log(message); // ❌ Error
```

Here:

- `message` exists only inside `test`
- Outside → ReferenceError

Each function creates its own scope.

---

# 🧱 3️⃣ Block Scope

Block scope is created using `{ }`.

But only with:

- `let`
- `const`

Not `var`.

```js
if (true) {
  let a = 10;
  const b = 20;
  var c = 30;
}

console.log(a); // ❌ Error
console.log(b); // ❌ Error
console.log(c); // ✅ 30
```

Why?

- `let` and `const` respect block scope.
- `var` ignores block scope.

---

## 🔍 4. Lexical Scope (Very Important)

JavaScript uses **Lexical Scope**.

That means:

Scope is determined by **where the function is written**, not where it is called.

Example:

```js
function outer() {
  var x = 10;

  function inner() {
    console.log(x);
  }

  inner();
}

outer();
```

Output:

```
10
```

Why?

Because `inner` is written inside `outer`,  
so it has access to `outer`’s variables.

This is lexical scoping.

---

## 🔗 5. Scope Chain

When JavaScript looks for a variable:

1. It checks current scope
2. If not found → goes to outer scope
3. Keeps going until global
4. If not found anywhere → ReferenceError

Example:

```js
var a = 1;

function one() {
  var b = 2;

  function two() {
    var c = 3;
    console.log(a, b, c);
  }

  two();
}

one();
```

Lookup for variables inside `two()`:

- `c` → found inside `two`
- `b` → found in `one`
- `a` → found in global

This chain is called **Scope Chain**.

---

## 🚫 6. Shadowing

When a variable inside a scope has the same name as outer variable.

```js
var x = 5;

function test() {
  var x = 10;
  console.log(x);
}

test(); // 10
```

The inner `x` shadows the outer `x`.

---

## 💥 7. Illegal Shadowing

```js
let a = 10;

{
  var a = 20; // ❌ SyntaxError
}
```

You cannot shadow `let` using `var` in the same scope chain.

---

# 🧪 Practice Section

---

## 🔹 Practice 1

Predict output:

```js
var a = 100;

function test() {
  var a = 10;
  console.log(a);
}

test();
```

Prints 10 on the screen, var a = 10 of function test() shadows var a = 100.

---

## 🔹 Practice 2

```js
var a = 100;

function outer() {
  function inner() {
    console.log(a);
  }
  inner();
}

outer();
```
Prints 100 on the screen, it access a through scope chain and finds it in the global chain.

---

## 🔹 Practice 3

```js
function x() {
  var a = 10;
}

console.log(a);
```

What happens? Why?

Prints ReferenceError on the screen, because a is function scope, meaning
only the scope in which it is declared and its inner scope can access it.

---