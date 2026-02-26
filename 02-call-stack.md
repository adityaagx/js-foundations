# 📘 JavaScript Call Stack (From First Principles)

The Call Stack is a LIFO data structure that manages execution contexts in JavaScript.  
Whenever a function is called, its execution context is pushed onto the stack, and removed when finished.

---

## 🧠 1. What is the Call Stack?

The Call Stack is a data structure that JavaScript uses to keep track of function execution.

JavaScript is single-threaded, meaning it can execute only one thing at a time.

To manage this, it uses a **stack** (LIFO – Last In, First Out).

Whoever gets called last → executes first → leaves first.

---

## 🏗 2. First Principle: Why Do We Even Need a Stack?

Think from zero.

When a function is called:

- JavaScript must pause the current code
- Execute the new function
- Then return back to where it left

So it needs a system to remember:

- Where it was
- What function is running
- What to execute next

That system = **Call Stack**

---

## 📦 3. What is a Stack?

A stack follows one rule:

LIFO → Last In, First Out

Like:

- Stack of plates
- Browser back history
- Undo feature

Example:

Push → Add to top  
Pop → Remove from top  

---

## ⚙ 4. How Call Stack Works in JavaScript

Step 1 → Global Execution Context is created  
Step 2 → It is pushed into the Call Stack  
Step 3 → When a function is called, a new Function Execution Context is created  
Step 4 → That Function Execution Context is pushed on top  
Step 5 → When function finishes, it is popped off  

Global always stays at the bottom.

---

## 🔥 5. Basic Example

```js
function greet() {
  console.log("Hello");
}

greet();
```

---

### Step-by-Step Stack Flow

Initial Stack:

```
| Global |
```

When `greet()` is called:

```
| greet  |
| Global |
```

After `greet()` finishes:

```
| Global |
```

Output:

```
Hello
```

---

## 🧩 6. Nested Function Example

```js
function one() {
  two();
}

function two() {
  three();
}

function three() {
  console.log("Done");
}

one();
```

---

### Stack Flow

Start:

```
| Global |
```

Call `one()`:

```
| one    |
| Global |
```

Call `two()`:

```
| two    |
| one    |
| Global |
```

Call `three()`:

```
| three  |
| two    |
| one    |
| Global |
```

After execution:

Pop `three()`

```
| two    |
| one    |
| Global |
```

Pop `two()`

```
| one    |
| Global |
```

Pop `one()`

```
| Global |
```

Final Output:

```
Done
```

---

## 💥 7. What is Stack Overflow?

If functions keep calling each other without stopping, the stack keeps growing.

Eventually memory limit is reached.

Example:

```js
function loop() {
  loop();
}

loop();
```

This causes:

RangeError: Maximum call stack size exceeded

Why?

Because:

- Function keeps pushing new execution contexts
- Nothing is ever popped
- Memory limit hits

That is called **Stack Overflow**

---

## 🎯 8. Important Rules

1. JavaScript is single-threaded.
2. Only one execution context runs at a time.
3. The Call Stack follows LIFO.
4. Global Execution Context is always at the bottom.
5. Every function call creates a new execution context.

---

# 🧪 Practice Section

---

## 🔹 Practice 1

Predict the stack order:

```js
function a() {
  b();
}

function b() {
  console.log("Inside B");
}

a();
```

Write stack push and pop order.

stack order -

Global

Push a()

Stack becomes - 

 a
 Global

 Push b()

 Stack becomes -

 b
 a
 Global

 b() executes, prints Inside B

 Pop b()

 Stack becomes - 

 a
 Global

 Pop a()

 Stack becomes -

 Global

---

## 🔹 Practice 2

What happens here?

```js
function x() {
  y();
}

function y() {
  x();
}

x();
```

Will it stop or crash?

Why?

It will crash because x and y functions will keep getting pushed in loop,
resulting in stack overflow and then crash.

---

## 🔹 Practice 3 (Think Deep)

```js
console.log("Start");

function test() {
  console.log("Inside Test");
}

test();

console.log("End");
```

Write:

1. Stack flow
2. Output order

---

Stack starts -

| Global |

Push console.log("start")

|console.log(start)|
| Global |

Prints start on the screen, stack becomes -

| Global |

Function test is already declared in the creation phase, hence move to test()

Push function call test() to stack, stack becomes -

| test |
| Global |

Executes test function, prints Inside Text on the screen, stack becomes -

| Global |

Push console.log(End) to the stack, stack becomes -

| console.log(End) |
| Global |

Executes and prints End on the screen, stack becomes -

| Global |

----
