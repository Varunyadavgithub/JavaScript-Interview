### **What is hoisting in JavaScript ?**

Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed. This means you can use variables and functions before they are declared in the code.

However, only the declarations are hoisted, not the initializations or assignments.

---

## Key Points About Hoisting

1. **Declaration Before Execution**:

   - JavaScript "hoists" the declarations of variables and functions to the top of their scope.
   - This makes them accessible before their actual line of declaration in the code.

2. **Partial Behavior**:

   - Only the declarations are hoisted, not the assignments or initializations.

3. **Applicable to Variables and Functions**:
   - `var` (function-scoped) is hoisted.
   - `let` and `const` (block-scoped) are hoisted but are not initialized (remain in the "temporal dead zone").
   - Function declarations are fully hoisted.

---

## Hoisting With `var`

Variables declared with `var` are hoisted and initialized with `undefined`.

### Example:

```javascript
console.log(a); // Output: undefined
var a = 10;
console.log(a); // Output: 10
```

### Behind the Scenes:

The code above is interpreted like this by the JavaScript engine:

```javascript
var a;
console.log(a); // undefined
a = 10;
console.log(a); // 10
```

---

## Hoisting With `let` and `const`

Variables declared with `let` and `const` are hoisted but are not initialized. They remain in the **temporal dead zone (TDZ)** from the start of the block until the declaration is encountered.

### Example:

```javascript
console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 20;
```

### Behind the Scenes:

The JavaScript engine hoists `b` but does not initialize it:

```javascript
// Temporal Dead Zone
let b;
console.log(b); // ReferenceError
b = 20;
```

---

## Hoisting With Functions

### Function Declarations:

Function declarations are fully hoisted, meaning you can call them even before they appear in the code.

#### Example:

```javascript
sayHello(); // Output: Hello, world!

function sayHello() {
  console.log("Hello, world!");
}
```

### Function Expressions:

Function expressions (using `var`, `let`, or `const`) are hoisted differently. Only the variable declaration is hoisted, not the function definition.

#### Example With `var`:

```javascript
console.log(sayHi); // Output: undefined
var sayHi = function () {
  console.log("Hi there!");
};

sayHi(); // TypeError: sayHi is not a function
```

#### Example With `let` or `const`:

```javascript
console.log(sayHi); // ReferenceError: Cannot access 'sayHi' before initialization
const sayHi = function () {
  console.log("Hi there!");
};
```

---

## Summary of Hoisting Behavior

| **Type**                               | **Hoisted?** | **Initialized?**      | **Access Before Declaration** |
| -------------------------------------- | ------------ | --------------------- | ----------------------------- |
| `var`                                  | Yes          | Yes, with `undefined` | Allowed (returns `undefined`) |
| `let`                                  | Yes          | No (in TDZ)           | Not Allowed (ReferenceError)  |
| `const`                                | Yes          | No (in TDZ)           | Not Allowed (ReferenceError)  |
| Function Declaration                   | Yes          | Fully                 | Allowed                       |
| Function Expression (`var`)            | Yes          | No                    | Allowed but as `undefined`    |
| Function Expression (`let` or `const`) | Yes          | No                    | Not Allowed                   |

---

## Practical Tips to Avoid Hoisting Confusion

1. **Declare Variables at the Top**:

   - Always declare variables at the beginning of their scope.

2. **Use `let` and `const`**:

   - Prefer `let` and `const` over `var` to reduce unexpected behaviors.

3. **Understand Temporal Dead Zone (TDZ)**:

   - Be mindful of the TDZ when using `let` and `const`.

4. **Define Functions Before Calling**:
   - Even though function declarations are hoisted, defining them before calling improves code readability.

---

## Conclusion

Hoisting is a fundamental concept in JavaScript that affects how variables and functions are declared and accessed. While it provides flexibility, understanding its nuances and limitations is essential for writing predictable and bug-free code. Use modern practices like `let`, `const`, and clear structure to mitigate potential issues related to hoisting.