## 2. Explain Scopes (Global, Local, Functional, Block) in JavaScript

## What is Scope in JavaScript?

In JavaScript, **scope** refers to the visibility or accessibility of variables, objects, and functions in different parts of the code during runtime. JavaScript uses lexical scoping, which means the scope of a variable is determined by where it is declared in the source code, and nested functions have access to variables in their outer scopes.

There are four main types of scopes in JavaScript:

1. **Global Scope**
2. **Local Scope**
3. **Functional Scope**
4. **Block Scope**

Let's dive into each one in detail.

---

## 1. Global Scope

- **Definition**: Variables declared in the global scope are accessible anywhere in the JavaScript code, even inside functions and blocks.

- **Characteristics**:
  - Global variables are declared outside of any function or block.
  - They are available throughout the entire code after being declared.
  - In a browser, global variables are attached to the `window` object (e.g., `window.myGlobalVariable`).
  - In Node.js, global variables are available globally, but they're not attached to the `window` object.

- **Example**:

```javascript
// Global scope
let globalVariable = "I am a global variable";

function testFunction() {
  console.log(globalVariable); // Can access globalVariable inside the function
}

testFunction(); // Output: "I am a global variable"
console.log(globalVariable); // Output: "I am a global variable" (accessible here too)
```

In the above example, `globalVariable` is accessible both inside the `testFunction()` and outside it because it is declared in the global scope.

---

## 2. Local Scope

- **Definition**: Local scope refers to the area where variables are accessible within a specific function or block. 

- **Characteristics**:
  - Variables declared inside a function or block are **local** to that function/block.
  - They are not accessible outside the function or block in which they are defined.

- **Example**:

```javascript
function testLocalScope() {
  let localVariable = "I am a local variable";
  console.log(localVariable); // Output: "I am a local variable"
}

testLocalScope();
console.log(localVariable); // Error: localVariable is not defined
```

In the above example, `localVariable` is only accessible inside the `testLocalScope()` function. Trying to access it outside the function results in a ReferenceError.

---

## 3. Functional Scope

- **Definition**: Functional scope refers specifically to the scope created by a function. In JavaScript, functions create their own scope, meaning variables declared inside a function are only accessible within that function.

- **Characteristics**:
  - Variables declared with `var` inside a function are **function-scoped**.
  - Variables declared with `let` and `const` inside a function are block-scoped but are still confined to the function.
  - A function's inner functions have access to the outer function's variables, creating a concept known as **closure**.

- **Example**:

```javascript
function outerFunction() {
  var outerVar = "I am from the outer function";

  function innerFunction() {
    console.log(outerVar); // Can access outerVar from the outer function (closure)
  }

  innerFunction(); // Output: "I am from the outer function"
  console.log(outerVar); // Output: "I am from the outer function"
}

outerFunction();
console.log(outerVar); // Error: outerVar is not defined
```

In the above example, `outerVar` is available inside the `outerFunction()` and its inner function `innerFunction()`. However, `outerVar` cannot be accessed outside of the function because it is function-scoped.

---

## 4. Block Scope

- **Definition**: Block scope refers to the scope of variables declared inside a block (a section of code enclosed in `{}`), such as inside loops, `if` statements, or other blocks.

- **Characteristics**:
  - Variables declared using `let` or `const` inside a block are **block-scoped**.
  - Variables declared with `var` are not block-scoped but are function-scoped or globally scoped depending on where they are declared.

- **Example with `let` and `const` (Block Scoping)**:

```javascript
if (true) {
  let blockScopedVar = "I am block-scoped";
  const blockScopedConst = "I am also block-scoped";
  console.log(blockScopedVar); // Output: "I am block-scoped"
  console.log(blockScopedConst); // Output: "I am also block-scoped"
}

console.log(blockScopedVar); // Error: blockScopedVar is not defined
console.log(blockScopedConst); // Error: blockScopedConst is not defined
```

Here, `blockScopedVar` and `blockScopedConst` are only accessible within the `if` block. Trying to access them outside the block will result in an error.

---

## `var` vs `let`/`const` in Scope

- **`var`** is function-scoped and doesn't have block scope.
- **`let`** and **`const`** are both block-scoped.

### Example with `var`:

```javascript
for (var i = 0; i < 3; i++) {
  console.log(i); // Output: 0 1 2
}

console.log(i); // Output: 3 (i is still accessible here because var is function-scoped)
```

### Example with `let`:

```javascript
for (let j = 0; j < 3; j++) {
  console.log(j); // Output: 0 1 2
}

console.log(j); // Error: j is not defined (let is block-scoped)
```

---

## Summary

- **Global Scope**: Variables are accessible throughout the code.
- **Local Scope**: Variables are only accessible inside the function or block they are declared in.
- **Functional Scope**: Functions create their own scope, and inner functions can access variables from their outer functions (closures).
- **Block Scope**: Variables declared with `let` or `const` are only accessible inside the block they are declared in.

Understanding the different types of scopes in JavaScript is crucial for managing variable lifetimes, ensuring the integrity of code, and avoiding common bugs like accidental variable reassignments.