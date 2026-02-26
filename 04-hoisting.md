# 📘 JavaScript Hoisting (From First Principles)

Hoisting is the memory allocation of variables and functions during the Creation Phase of execution.  
`var` is initialized with undefined, function declarations are fully hoisted, and `let/const` stay in the Temporal Dead Zone until initialized.

---

## 🧠 1. What is Hoisting?

Hoisting is JavaScript's default behavior of moving **declarations** to the top of their scope during the Creation Phase.

Important:

👉 Only declarations are hoisted  
👉 Initializations are NOT hoisted  

---

## 🏗 2. First Principle: Why Does Hoisting Happen?

Remember Execution Context?

Every execution context has two phases:

1. Creation Phase (Memory setup)
2. Execution Phase (Code runs line by line)

During the **Creation Phase**:

- `var` variables are allocated memory and set to `undefined`
- Function declarations are stored fully in memory
- `let` and `const` are allocated but NOT initialized

This memory setup is what we call **hoisting**.

Hoisting is not magic.
It is just memory allocation before execution.

---

# 🌍 3️⃣ Hoisting with `var`

```js
console.log(a);
var a = 10;
```

### What Happens Internally:

During Creation Phase:

```
a → undefined
```

During Execution Phase:

```
console.log(a); → undefined
a = 10;
```

Output:

```
undefined
```

JavaScript treats it like:

```js
var a;
console.log(a);
a = 10;
```

---

# 🔥 4️⃣ Hoisting with Function Declarations

```js
greet();

function greet() {
  console.log("Hello");
}
```

Output:

```
Hello
```

Why?

Because during Creation Phase:

```
greet → full function definition stored in memory
```

So it can be called even before it appears in the code.

---

# ⚠️ 5️⃣ Hoisting with `let` and `const`

```js
console.log(a);
let a = 10;
```

Output:

```
ReferenceError
```

Why?

Because:

- `let` and `const` are hoisted
- But they are NOT initialized
- They stay in something called the **Temporal Dead Zone (TDZ)**

---

## 💀 Temporal Dead Zone (TDZ)

The time between:

- Variable hoisting
- And variable initialization

During this period, accessing the variable throws an error.

Example:

```js
console.log(a); // ❌ ReferenceError
let a = 10;
```

TDZ exists only for `let` and `const`.

---

# 🚫 6️⃣ Hoisting with Function Expressions

```js
greet();

var greet = function() {
  console.log("Hello");
};
```

Output:

```
TypeError: greet is not a function
```

Why?

Creation Phase:

```
greet → undefined
```

Execution Phase:

```
greet(); // undefined()
```

Since `greet` is undefined at that moment, it cannot be called.

---

# 🧠 7️⃣ Summary Table

| Type                  | Hoisted? | Initialized? | Usable Before Declaration? |
|-----------------------|----------|--------------|----------------------------|
| var                   | Yes      | Yes (undefined) | Yes (prints undefined) |
| let                   | Yes      | No           | No (ReferenceError)       |
| const                 | Yes      | No           | No (ReferenceError)       |
| Function Declaration  | Yes      | Yes (full function) | Yes |
| Function Expression   | Depends on var/let | No | No |

---

# 🧪 Practice Section

---

## 🔹 Practice 1

```js
console.log(x);
var x = 5;
```

What prints? Why?

Prints undefined on the screen, because var is hoisted and initialized
as undefined during creation phase.
---

## 🔹 Practice 2

```js
sayHi();

function sayHi() {
  console.log("Hi");
}
```

What prints? Why?

Prints Hi on the screen, because function declarations are hoisted 
at the top of scope during global creation phase and 
can also be called before the function itself.

---

## 🔹 Practice 3

```js
sayHello();

var sayHello = function() {
  console.log("Hello");
};
```

What happens? Why?

Prints TypeError: sayHello is not a function, on the screen because var is intitialized
and hoisted as a var undefined during creation phase.

---

## 🔹 Practice 4 (TDZ)

```js
console.log(a);
let a = 20;
```

Why does this throw an error instead of printing undefined?

Prints ReferenceError on the screen, because let and const are not initialized,
they are pushed in Temporal dead zone, during creation phase.

---
