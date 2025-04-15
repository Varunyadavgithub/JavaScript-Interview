# 🌶️ Currying in JavaScript — A Complete Guide

## 🔍 What is Currying?

**Currying** is a concept in functional programming where a function is transformed into a sequence of **functions that take one argument at a time**.

Instead of writing a function that takes multiple arguments all at once, you break it down so that **each function returns another function**, which eventually returns the final result.

---

## 🧠 Why Use Currying?

- **Reusability**: You can reuse partially applied functions.
- **Function Composition**: Currying helps in composing functions together.
- **Customization**: You can customize functions more flexibly.

---

## 📌 Case 1: Normal Function (No Currying)

```js
function Addition(a, b, c) {
    return a + b + c;
}

let res = Addition(2, 3, 4);
console.log(res); // Output: 9
```

This function takes all three arguments at once.

---

## 📌 Case 2: Curried Function

```js
function Addition(a) {
    return function(b) {
        return function(c) {
            return a + b + c;
        }
    }
}
```

### Usage:

```js
let res = Addition(2);    // returns function(b)
let data = res(4);        // returns function(c)
let data1 = data(7);      // returns a + b + c
console.log(data1);       // Output: 13
```

### OR (in one line):

```js
let res = Addition(2)(4)(7);
console.log(res); // Output: 13
```

✅ This is **currying in action**!

---

## 💡 Real-World Use Case of Currying

```js
const userObj = {
    name: "Aman",
    age: 25,
};

function userInfo(obj) {
    return function(infoType) {
        return obj[infoType];
    }
}

let res = userInfo(userObj);
console.log(res("name")); // Output: "Varun"
console.log(res("age"));  // Output: 25
```

Here, `userInfo(userObj)` returns a function which can be reused to fetch any property of that object dynamically.

---

## 🔁 Infinite Currying

Currying is not just limited to a fixed number of arguments — we can make it **infinite**!

### ❌ Incorrect Way

```js
function add(a) {
    return function(b) {
        return function(c) {
            return a + b + c;
        }
    }
}
console.log(add(4)(5)(7)()); // ❌ TypeError: add(...)(...)(...)(...) is not a function
```

This only works for 3 arguments. We can't call it like `add(4)(5)(7)(...)`.

---

## ✅ Correct Infinite Currying

```js
function add(a) {
    return function(b) {
        if (b) return add(a + b);
        return a;
    }
}

console.log(add(4)(5)(7)(9)()); // Output: 25
```

### ✅ How It Works:

- Each function call keeps **adding to `a`** and returns a new function.
- When you finally **call with no argument**, it stops and returns the result.

---

## 🧪 How to Make Curried Function That Accepts Any Number of Args at Once

If you want to call a function like this:

```js
add(2)(4)(6)(8)(10)(); // -> 30
```

Here’s a generic version:

```js
function currySum(a) {
    return function next(b) {
        if (b !== undefined) {
            return currySum(a + b);
        } else {
            return a;
        }
    }
}
```

---

## 🔚 Conclusion

- **Currying** converts a function with multiple arguments into a chain of functions with single arguments.
- It allows for **clean, reusable, and composable code**.
- Use it for:
  - Configurable logic
  - Partial application
  - Building DSL-like APIs
- And yes, you can even create **infinitely curried functions** that resolve when you stop supplying new arguments.

---

## 📝 Quick Summary

| Feature             | Description |
|---------------------|-------------|
| Currying            | Breaking a function into smaller functions |
| Benefit             | Reusability, readability, modularity |
| Real-life Use Case  | Dynamic object property access |
| Infinite Currying   | Allows dynamic number of arguments |
| Return Trigger      | Use a check (like `if (!b)`) to return final value |

---

## 🚀 Practice Task

Try creating a curried function `multiply(a)(b)(c)` and `greet(greeting)(name)`!

Happy Coding! 😄