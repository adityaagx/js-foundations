# 📘 JavaScript Closures (From First Principles)

A closure is created when a function remembers variables from its lexical scope even after the outer function has finished execution.  
Closure = Function + Persistent reference to outer variables.

---

## 🧠 1. What is a Closure?

A closure is created when:

👉 A function remembers variables from its outer (lexical) scope  
👉 Even after the outer function has finished executing  

In simple words:

A closure is a function bundled together with its surrounding state.

---

## 🏗 2. First Principle: Why Do Closures Exist?

Remember:

- Every function creates a new execution context.
- Every function has access to its outer scope (lexical scope).
- JavaScript uses a scope chain.

Now here’s the powerful part:

Even when the outer function is done,  
the inner function still remembers the outer variables.

That memory retention is called a **closure**.

---

# 🔥 3️⃣ Basic Example

```js
function outer() {
  var count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer();
counter(); 
counter();
counter();
```

---

## 🧠 What Happens Internally?

Step 1:
`outer()` runs.

Creation Phase:
```
count → undefined
inner → function definition
```

Execution Phase:
```
count → 0
return inner
```

Normally, when `outer()` finishes, its execution context is removed.

BUT...

Because `inner` is returned and stored in `counter`,
JavaScript keeps the variables of `outer` alive.

So `count` does NOT get destroyed.

---

## 🚀 When We Call:

```js
counter();
```

`inner()` executes.

It still has access to:

```
count → stored from outer()
```

So output becomes:

```
1
2
3
```

That is closure.

---

# 🔗 4️⃣ Closure = Function + Lexical Environment

Closure is not just the function.

It is:

```
Function + Reference to outer variables
```

That’s why inner can access outer even after outer is gone from call stack.

---

# 🧩 5️⃣ Real-World Use Case

### Private Variables

```js
function createUser() {
  var password = "12345";

  return {
    getPassword: function() {
      return password;
    }
  };
}

const user = createUser();
console.log(user.getPassword());
```

You cannot access `password` directly.

But the inner function can.

That’s data privacy using closures.

---

# 💥 6️⃣ Common Interview Question

```js
function x() {
  var a = 10;
  function y() {
    console.log(a);
  }
  return y;
}

var z = x();
z();
```

Output:

```
10
```

Even though `x()` is finished,
`y()` remembers `a`.

Because of closure.

---

# ⚠️ 7️⃣ Closures in Loops (Classic Problem)

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

Output:
```
4
4
4
```

Why?

Because:

- `var` is function scoped
- All callbacks share the same `i`
- By the time they run, loop is finished
- `i = 4`

---

## ✅ Fix Using `let`

```js
for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

Output:
```
1
2
3
```

Because `let` creates a new block scope for each iteration.

Each closure gets its own `i`.

---

# 🧠 8️⃣ Why Closures Are Important

Closures are used in:

- React hooks
- Event listeners
- Callbacks
- setTimeout
- Data privacy
- Module patterns
- Memoization
- Functional programming

Without closures, modern JavaScript wouldn’t exist.

---

# 🧪 Practice Section

---

## 🔹 Practice 1

```js
function outer() {
  var x = 5;
  return function inner() {
    console.log(x);
  };
}

const fn = outer();
fn();
```

What prints? Why?

Prints 5 on the screen because outer function returns inner function,
which gets the value of x from outer function.
---

## 🔹 Practice 2

```js
function counter() {
  var count = 0;
  return function() {
    count++;
    console.log(count);
  };
}

const c1 = counter();
c1();
c1();
```

What prints?

Prints 1 and 2 on the screen.
---

## 🔹 Practice 3 (Tricky)

```js
function test() {
  var a = 10;
  return function() {
    a = a + 5;
    console.log(a);
  };
}

const t = test();
t();
t();
t();
```

Predict output.

Prints 15, 20, 25
---
