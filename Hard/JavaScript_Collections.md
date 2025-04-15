# 🧭 JavaScript Collections — Map, Set, WeakMap & WeakSet

JavaScript provides built-in collection types for storing groups of values:

- `Map`
- `Set`
- `WeakMap`
- `WeakSet`

These offer **better performance, flexibility, and functionality** than regular objects and arrays for certain use cases.

---

## 🔹 1. Map

### ✅ What is a Map?

A `Map` is a collection of key-value pairs, similar to objects, but with more features.

### 🧠 Key Features:

- Keys can be of **any data type** (including objects, functions, etc.)
- Maintains the **insertion order**
- Can easily get the size

### 📦 Syntax:

```js
const myMap = new Map();
myMap.set("name", "Varun");
myMap.set(1, "One");
myMap.set(true, "Boolean");

console.log(myMap.get("name"));  // "Varun"
console.log(myMap.size);         // 3
```

### 🔄 Iterating:

```js
for (let [key, value] of myMap) {
    console.log(key, value);
}
```

---

## 🔹 2. Set

### ✅ What is a Set?

A `Set` is a collection of **unique values**.

### 🧠 Key Features:

- Stores **only unique** values
- Can hold values of any type
- Maintains insertion order

### 📦 Syntax:

```js
const mySet = new Set();
mySet.add(1);
mySet.add(2);
mySet.add(2); // ignored, already exists

console.log(mySet.has(1));   // true
console.log(mySet.size);     // 2
```

### 🔄 Iterating:

```js
mySet.forEach(value => console.log(value));
```

---

## 🔸 3. WeakMap

### ✅ What is a WeakMap?

A `WeakMap` is like a `Map`, but:

- Keys must be **objects**
- Keys are **weakly referenced** (not prevented from garbage collection)

### 🧠 Key Features:

- Can't iterate or check size
- Great for storing private data tied to DOM elements or objects
- Helps avoid memory leaks

### 📦 Syntax:

```js
const wm = new WeakMap();
let obj = {};

wm.set(obj, "private value");
console.log(wm.get(obj)); // "private value"

obj = null; // Now the key-value pair is eligible for garbage collection
```

> ⚠️ `WeakMap` methods: `set`, `get`, `has`, `delete`

---

## 🔸 4. WeakSet

### ✅ What is a WeakSet?

A `WeakSet` is like a `Set`, but:

- Only stores **objects**
- Objects are held **weakly**
- Not iterable

### 🧠 Key Features:

- Cannot check size or iterate
- Useful for managing object references without memory leaks

### 📦 Syntax:

```js
const ws = new WeakSet();
let user = { name: "Varun" };

ws.add(user);
console.log(ws.has(user)); // true

user = null; // Automatically removed from the WeakSet
```

---

## 🔁 Comparison Table

| Feature       | Map        | Set       | WeakMap      | WeakSet     |
|---------------|------------|-----------|--------------|-------------|
| Keys/Values   | key-value  | values    | key-value    | values      |
| Key type      | Any        | Any       | Object only  | Object only |
| Duplicates    | No         | No        | No           | No          |
| Order         | Preserved  | Preserved | N/A          | N/A         |
| Iterable      | ✅         | ✅        | ❌           | ❌          |
| Garbage Col.  | ❌         | ❌        | ✅           | ✅          |
| Size Access   | ✅         | ✅        | ❌           | ❌          |

---

## 🚀 Use Cases

| Use Case                             | Best Collection |
|--------------------------------------|-----------------|
| Unique values                        | `Set`           |
| Key-value store with non-string keys| `Map`           |
| Memory-safe object-key storage       | `WeakMap`       |
| Track object references              | `WeakSet`       |

---

## 🧪 Quick Practice

- Store usernames uniquely → `Set`
- Cache user metadata → `Map`
- Track element-specific data safely → `WeakMap`
- Track whether objects were seen → `WeakSet`

---

## 🧠 Summary

- Use `Map`/`Set` when you need **iteration** and **full data control**
- Use `WeakMap`/`WeakSet` when dealing with **temporary object references** and **memory-sensitive operations**

---

Happy Coding! 🚀