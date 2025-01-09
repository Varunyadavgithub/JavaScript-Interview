### **What is the Difference Between Function Declaration and Function Expression?**

In JavaScript, functions can be defined in two main ways: **function declarations** and **function expressions**. Both approaches allow you to create functions, but they have key differences in syntax, behavior, and usage.

## 1. **Function Declaration**

A **function declaration** is a way to define a function with the `function` keyword, followed by the function name, and its body. This method is hoisted, meaning the function can be called before its definition in the code.

### Syntax:

```javascript
function functionName() {
  // Function body
}
```

### Example:

```javascript
// Function declaration
function greet() {
  console.log("Hello, World!");
}

// Function call (can be done before the function definition due to hoisting)
greet(); // Output: "Hello, World!"
```

### Key Points:

- **Hoisted:** The function declaration is hoisted to the top of its scope, meaning you can call the function before it is defined.
- **Named function:** The function is given a name and can be called by that name.

---

## 2. **Function Expression**

A **function expression** defines a function as part of an expression. This means the function is typically assigned to a variable or passed as an argument to another function. Unlike function declarations, function expressions are **not hoisted** and can only be called after they are defined.

### Syntax:

```javascript
const functionName = function () {
  // Function body
};
```

### Example:

```javascript
// Function expression
const greet = function () {
  console.log("Hello, World!");
};

// Function call (must be done after the function definition)
greet(); // Output: "Hello, World!"
```

### Key Points:

- **Not Hoisted:** The function expression is not hoisted, so it must be defined before it is called.
- **Anonymous or Named:** A function expression can be anonymous (without a name) or named.
  - **Anonymous:** `const greet = function() {}`.
  - **Named:** `const greet = function greetFunction() {}`.
- **Assigned to Variables:** The function is usually assigned to a variable, allowing it to be passed around as a value.

---

## **Key Differences**

| Feature                  | Function Declaration                                                   | Function Expression                                                           |
| ------------------------ | ---------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Hoisting**             | Hoisted to the top of its scope (can be called before its definition). | Not hoisted (must be defined before calling).                                 |
| **Syntax**               | `function functionName() { ... }`                                      | `const functionName = function() { ... }`                                     |
| **Name**                 | Always has a name (the function name).                                 | Can be anonymous or named.                                                    |
| **Use Case**             | Suitable for defining reusable functions.                              | Often used for passing functions as arguments or assigning them to variables. |
| **Calling the Function** | Can be called before the function definition.                          | Can only be called after the function is defined.                             |

---

### **Example of Hoisting Behavior (Function Declaration vs Expression)**

```javascript
// Function Declaration Example
greet(); // Output: "Hello, World!"
function greet() {
  console.log("Hello, World!");
}

// Function Expression Example
greet(); // Error: greet is not a function
const greet = function () {
  console.log("Hello, World!");
};
```

In the function declaration example, `greet()` works even before the function definition because the declaration is hoisted. However, in the function expression example, calling `greet()` before its definition results in an error because the function expression is not hoisted.

---

### **Summary**

- **Function Declarations** are hoisted, can be called before they are defined, and are typically used for defining reusable functions.
- **Function Expressions** are not hoisted and can only be invoked after they are assigned. They are commonly used for passing functions as arguments or assigning them to variables.

Understanding the differences between these two allows for better function handling and helps avoid common pitfalls in JavaScript code.