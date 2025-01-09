### **What is the Difference Between Shallow Copy and Deep Copy ?**

When working with objects or arrays in programming, it’s important to understand the concepts of **shallow copy** and **deep copy**. These concepts determine how data is copied from one object or array to another and how changes to the original data affect the copied data.

---

### **Shallow Copy**

A **shallow copy** creates a new object or array, but it only copies the reference of nested objects or arrays. This means that if the original data contains other objects or arrays, the shallow copy will still reference the same memory location for those nested objects or arrays.

#### **Characteristics:**

1. Copies only the top-level properties.
2. Does not duplicate nested objects or arrays; instead, it references them.
3. Changes made to nested objects or arrays in the original will reflect in the shallow copy (and vice versa).

#### **Examples of Shallow Copy:**

1. **Using `Object.assign()` (for objects):**

```javascript
const original = { name: "Alice", details: { age: 25 } };
const shallowCopy = Object.assign({}, original);

shallowCopy.name = "Bob"; // Changes only the copy
shallowCopy.details.age = 30; // Changes the original's nested object too

console.log(original.details.age); // Output: 30
```

2. **Using the Spread Operator (for objects and arrays):**

```javascript
const originalArray = [1, 2, { a: 3 }];
const shallowCopyArray = [...originalArray];

shallowCopyArray[2].a = 10; // Changes the original nested object
console.log(originalArray[2].a); // Output: 10
```

---

### **Deep Copy**

A **deep copy** creates a new object or array and recursively copies all levels of nested objects or arrays. This means that the copied data is completely independent of the original data.

#### **Characteristics:**

1. Duplicates all nested structures.
2. The copy is independent of the original; changes to one do not affect the other.
3. More computationally expensive compared to a shallow copy.

#### **Examples of Deep Copy:**

1. **Using `JSON.parse(JSON.stringify())`:**

```javascript
const original = { name: "Alice", details: { age: 25 } };
const deepCopy = JSON.parse(JSON.stringify(original));

deepCopy.details.age = 30; // Changes only the copy
console.log(original.details.age); // Output: 25
```

**Note:** This method does not handle special cases like functions, `undefined`, `Date`, or circular references.

2. **Using a Utility Library like Lodash:**

```javascript
const _ = require("lodash");

const original = { name: "Alice", details: { age: 25 } };
const deepCopy = _.cloneDeep(original);

deepCopy.details.age = 30; // Changes only the copy
console.log(original.details.age); // Output: 25
```

3. **Manual Recursion:**

```javascript
function deepCopy(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj;
  }

  const copy = Array.isArray(obj) ? [] : {};
  for (let key in obj) {
    copy[key] = deepCopy(obj[key]);
  }
  return copy;
}

const original = { name: "Alice", details: { age: 25 } };
const deepCopyObj = deepCopy(original);

deepCopyObj.details.age = 30; // Changes only the copy
console.log(original.details.age); // Output: 25
```

---

### **Key Differences Between Shallow Copy and Deep Copy**

| Feature                   | Shallow Copy                           | Deep Copy                                                     |
| ------------------------- | -------------------------------------- | ------------------------------------------------------------- |
| **Copies Top-Level Data** | Yes                                    | Yes                                                           |
| **Copies Nested Data**    | No (references nested objects)         | Yes (creates independent copies)                              |
| **Original-Dependent**    | Changes in nested data affect the copy | Changes in nested data do not affect                          |
| **Performance**           | Faster and less memory-intensive       | Slower and more memory-intensive                              |
| **Methods**               | `Object.assign()`, Spread Operator     | `JSON.parse(JSON.stringify())`, Recursive Function, Libraries |

---

### **When to Use**

- **Shallow Copy:**  
  Use when you are dealing with simple data structures where nested objects are not modified independently.

- **Deep Copy:**  
  Use when working with complex data structures and need to ensure that the copy is completely independent of the original.

---

### **Conclusion**

Understanding the difference between shallow copy and deep copy is crucial for managing data in JavaScript effectively. While shallow copies are faster and sufficient for simple scenarios, deep copies are indispensable when dealing with deeply nested data structures that require complete independence from the original object or array.