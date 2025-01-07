### **What Are JavaScript Data Types?**

---

In JavaScript, **data types** define the kind of data that can be stored and manipulated in a program. JavaScript is a **dynamically typed language**, meaning variables are not explicitly declared with a specific type but can hold values of any type, which may change during execution.

---

### **JavaScript Data Types**

JavaScript has two main categories of data types:
1. **Primitive Data Types** (basic and immutable)
2. **Non-Primitive Data Types** (complex and mutable)

---

### **1. Primitive Data Types**

Primitive data types represent single, immutable values. They are stored directly in the variable's memory location.

#### **Primitive Types in JavaScript**:

| Data Type       | Description                                                                                  | Example                   |
|------------------|----------------------------------------------------------------------------------------------|---------------------------|
| **Number**       | Represents numeric values, including integers and floating-point numbers.                   | `42`, `3.14`, `-7`       |
| **String**       | Represents a sequence of characters.                                                        | `'Hello'`, `"World"`      |
| **Boolean**      | Represents logical values: `true` or `false`.                                               | `true`, `false`           |
| **Undefined**    | Represents a variable that has been declared but not assigned a value.                      | `let x; // undefined`     |
| **Null**         | Represents an intentional absence of value (explicitly set by the programmer).              | `let y = null;`           |
| **BigInt**       | Represents large integers beyond the range of `Number`.                                     | `12345678901234567890n`   |
| **Symbol**       | Represents unique and immutable values, often used as object property keys.                 | `Symbol('id')`           |

---

#### **Examples of Primitive Data Types**

```javascript
// Number
let age = 25;
let price = 99.99;

// String
let greeting = "Hello, World!";
let singleQuoteString = 'JavaScript';

// Boolean
let isLoggedIn = true;
let hasAccess = false;

// Undefined
let uninitializedVar;
console.log(uninitializedVar); // Output: undefined

// Null
let emptyValue = null;
console.log(emptyValue); // Output: null

// BigInt
let bigNumber = 12345678901234567890n;
console.log(bigNumber); // Output: 12345678901234567890n

// Symbol
let uniqueKey = Symbol('key');
console.log(uniqueKey); // Output: Symbol(key)
```

---

### **2. Non-Primitive (Complex) Data Types**

Non-primitive data types are objects that can store collections of data or more complex entities.

#### **Non-Primitive Types in JavaScript**:

| Data Type | Description                                                                                   | Example                              |
|-----------|-----------------------------------------------------------------------------------------------|--------------------------------------|
| **Object** | Represents collections of key-value pairs. Includes arrays, functions, and other objects.    | `{name: 'John', age: 30}`            |

---

#### **Examples of Non-Primitive Data Types**

1. **Objects**:
   ```javascript
   let person = {
       name: "John",
       age: 30,
       isEmployed: true
   };
   console.log(person.name); // Output: John
   ```

2. **Arrays**:
   Arrays are special objects used to store ordered collections of data.
   ```javascript
   let fruits = ["Apple", "Banana", "Cherry"];
   console.log(fruits[1]); // Output: Banana
   ```

3. **Functions**:
   Functions are first-class objects and can be assigned to variables or passed as arguments.
   ```javascript
   function greet() {
       return "Hello!";
   }
   console.log(greet()); // Output: Hello!
   ```

4. **Dates**:
   JavaScript provides the `Date` object to work with dates and times.
   ```javascript
   let today = new Date();
   console.log(today); // Output: Current date and time
   ```

---

### **Key Differences Between Primitive and Non-Primitive Types**

| Feature                 | Primitive Data Types             | Non-Primitive Data Types        |
|--------------------------|----------------------------------|----------------------------------|
| **Mutability**           | Immutable                       | Mutable                         |
| **Stored in**            | Stack                           | Heap                            |
| **Pass by**              | Value                           | Reference                       |

---

### **Special Cases**

#### **1. `typeof` Operator**
The `typeof` operator is used to determine the type of a value.

```javascript
console.log(typeof 42);           // Output: "number"
console.log(typeof "Hello");      // Output: "string"
console.log(typeof true);         // Output: "boolean"
console.log(typeof undefined);    // Output: "undefined"
console.log(typeof null);         // Output: "object" // Legacy behavior
console.log(typeof Symbol('id')); // Output: "symbol"
console.log(typeof {name: "Alice"}); // Output: "object"
```

#### **2. `null` vs `undefined`**
- **`null`**: Represents a deliberate assignment of "no value."
- **`undefined`**: Represents an uninitialized or missing value.

```javascript
let x;
console.log(x); // Output: undefined

let y = null;
console.log(y); // Output: null
```

---

### **Dynamic Typing in JavaScript**

JavaScript is dynamically typed, meaning variables can change their type during runtime.

Example:
```javascript
let data = "Hello";
console.log(typeof data); // Output: string

data = 123;
console.log(typeof data); // Output: number

data = true;
console.log(typeof data); // Output: boolean
```

---

### **Conclusion**

Understanding JavaScript's data types is fundamental to writing efficient and bug-free code. Mastery over primitive and non-primitive types, along with concepts like mutability, scope, and dynamic typing, will help you handle data effectively in your JavaScript programs.