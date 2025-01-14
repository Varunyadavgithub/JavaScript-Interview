### **Default and Named Exports in JavaScript**

JavaScript modules allow developers to share and reuse code across files efficiently. This is done through **export** and **import** statements. JavaScript offers two main ways to export code: **Default Exports** and **Named Exports**.

---

### **1. Default Exports**

Default exports are used to export a single value or functionality from a module. A module can only have one default export.

#### **Key Features of Default Exports**

- A module can have **only one default export**.
- Default exports are imported without curly braces `{}`.
- The name used to import the default export **does not need to match** the name of the export.

---

#### **Example: Default Export**

**File: `mathUtils.js`**

```javascript
export default function multiply(a, b) {
  return a * b;
}
```

**File: `app.js`**

```javascript
import multiplyNumbers from "./mathUtils.js";
console.log(multiplyNumbers(5, 3)); // Output: 15
```

**Explanation:**

- In `mathUtils.js`, the function `multiply` is exported as the default export.
- In `app.js`, the default export is imported without curly braces, and the name `multiplyNumbers` is used, even though it was exported as `multiply`.

---

### **2. Named Exports**

Named exports allow you to export multiple values or functionalities from a module. A module can have multiple named exports.

#### **Key Features of Named Exports**

- A module can have **multiple named exports**.
- Named exports must be imported using curly braces `{}`.
- The names of the imports must match the names of the exports unless renamed using the `as` keyword.

---

#### **Example: Named Export**

**File: `mathUtils.js`**

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

**File: `app.js`**

```javascript
import { add, subtract } from "./mathUtils.js";
console.log(add(5, 3)); // Output: 8
console.log(subtract(5, 3)); // Output: 2
```

**Explanation:**

- The functions `add` and `subtract` are exported as named exports in `mathUtils.js`.
- In `app.js`, the functions are imported using curly braces, and the names must match the exported names.

---

#### **Renaming Named Exports**

You can rename named exports while importing using the `as` keyword.

**File: `app.js`**

```javascript
import { add as addition, subtract as subtraction } from "./mathUtils.js";
console.log(addition(5, 3)); // Output: 8
console.log(subtraction(5, 3)); // Output: 2
```

---

### **3. Combining Default and Named Exports**

A module can have both a default export and named exports. This is useful when you want to export a main functionality (default) along with additional utilities (named).

#### **Example:**

**File: `mathUtils.js`**

```javascript
export default function divide(a, b) {
  return a / b;
}

export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

**File: `app.js`**

```javascript
import divide, { add, subtract } from "./mathUtils.js";
console.log(divide(10, 2)); // Output: 5
console.log(add(5, 3)); // Output: 8
console.log(subtract(5, 3)); // Output: 2
```

**Explanation:**

- The `divide` function is the default export and is imported without curly braces.
- The `add` and `subtract` functions are named exports and are imported with curly braces.

---

### **4. Default vs. Named Exports: Key Differences**

| Feature               | Default Export                | Named Export                     |
| --------------------- | ----------------------------- | -------------------------------- |
| **Number of Exports** | Only one per module           | Multiple per module              |
| **Import Syntax**     | `import value from 'module'`  | `import { value } from 'module'` |
| **Renaming**          | Can rename without `as`       | Requires `as` for renaming       |
| **Curly Braces**      | Not used                      | Required                         |
| **Use Case**          | For the primary functionality | For multiple utilities or values |

---

### **5. Why Use Exports in JavaScript?**

Using exports promotes:

1. **Code Reusability**: Functions and variables can be reused across multiple files.
2. **Separation of Concerns**: Each file/module can focus on a specific functionality.
3. **Maintainability**: Modular code is easier to read, debug, and maintain.
4. **Scalability**: Projects become easier to scale as functionalities are modularized.

---

### **When to Use Default and Named Exports?**

- Use **Default Exports** when:

  - The module has one main functionality.
  - You want the flexibility to rename the import without using `as`.

- Use **Named Exports** when:
  - The module contains multiple related utilities or values.
  - You need to export multiple functionalities from the same file.

---

With this understanding, you can choose between default and named exports to structure your JavaScript modules effectively!