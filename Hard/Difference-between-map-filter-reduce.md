### **What is the difference between `map()`, `filter()`, and `reduce()` methods?**

The `map()`, `filter()`, and `reduce()` methods are essential higher-order functions in JavaScript, widely used for handling arrays in a functional programming style. Each serves a distinct purpose and offers unique functionality. Below is a comprehensive breakdown of their behavior, characteristics, and practical examples.

---

## **1. `map()`**

### **Purpose:**

The `map()` method iterates through each element in an array, applies a transformation or function to it, and returns a **new array** containing the transformed elements.

### **Key Characteristics:**

- Executes a provided callback function for **every element** in the array.
- Returns a **new array** with the results of the callback.
- **Does not modify** the original array.
- The length of the output array is always the same as the input array.

### **Common Use Cases:**

- Converting values (e.g., multiplying numbers, formatting strings).
- Extracting specific data from an array of objects.

### **Example Explained:**

```javascript
const numbers = [1, 2, 3, 4];
const squaredNumbers = numbers.map((num) => num * num);

console.log(squaredNumbers); // [1, 4, 9, 16]
```

**Explanation:**

1. The `map()` function iterates over each element in `numbers`.
2. It applies the transformation `num * num` to each element.
3. It returns a **new array** `[1, 4, 9, 16]` without altering the original array.

---

## **2. `filter()`**

### **Purpose:**

The `filter()` method filters out elements from an array that do not satisfy a specific condition (predicate) and returns a **new array** containing only the elements that meet the condition.

### **Key Characteristics:**

- Applies the callback function to each element and checks if it returns a **truthy** value.
- Returns a **new array** with the elements that passed the test.
- **Does not modify** the original array.
- The length of the output array can be less than or equal to the input array.

### **Common Use Cases:**

- Filtering out specific elements based on a condition.
- Extracting elements that match a criterion.

### **Example Explained:**

```javascript
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbers = numbers.filter((num) => num % 2 === 0);

console.log(evenNumbers); // [2, 4, 6]
```

**Explanation:**

1. The `filter()` function checks each element in `numbers` for the condition `num % 2 === 0`.
2. It includes only the elements that return `true` for this condition (i.e., even numbers).
3. It returns `[2, 4, 6]` as a new array, leaving the original array unchanged.

---

## **3. `reduce()`**

### **Purpose:**

The `reduce()` method processes an array and reduces it to a single value by applying a reducer function to each element. It’s incredibly versatile and can perform various operations like summing elements, merging arrays, or building objects.

### **Key Characteristics:**

- The callback function takes two main arguments:
  - **Accumulator**: Holds the cumulative result.
  - **Current Value**: The current element being processed.
- Can take an **initial value** for the accumulator (default is the first element of the array if not provided).
- Returns a **single value** (e.g., number, string, or object).
- **Does not modify** the original array.

### **Common Use Cases:**

- Calculating sums, averages, or other aggregate values.
- Flattening arrays.
- Creating or updating objects.

### **Examples Explained:**

#### **Summing Elements:**

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);

console.log(sum); // 10
```

**Explanation:**

1. The `reduce()` function starts with an initial `accumulator` value of `0`.
2. It adds each `currentValue` to the `accumulator`:
   - Step 1: `0 + 1 = 1`
   - Step 2: `1 + 2 = 3`
   - Step 3: `3 + 3 = 6`
   - Step 4: `6 + 4 = 10`
3. Returns `10` as the final result.

#### **Flattening Arrays:**

```javascript
const nestedArrays = [
  [1, 2],
  [3, 4],
  [5, 6],
];
const flattenedArray = nestedArrays.reduce(
  (accumulator, currentValue) => accumulator.concat(currentValue),
  []
);

console.log(flattenedArray); // [1, 2, 3, 4, 5, 6]
```

**Explanation:**

1. Starts with an empty array (`[]`) as the initial accumulator.
2. Combines each sub-array into the accumulator using `concat()`.
3. Returns a single, flat array `[1, 2, 3, 4, 5, 6]`.

#### **Creating Objects:**

```javascript
const fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];
const fruitCount = fruits.reduce((accumulator, fruit) => {
  accumulator[fruit] = (accumulator[fruit] || 0) + 1;
  return accumulator;
}, {});

console.log(fruitCount); // { apple: 3, banana: 2, orange: 1 }
```

**Explanation:**

1. Starts with an empty object (`{}`) as the accumulator.
2. For each fruit, checks if it exists in the accumulator. If yes, increments its count; otherwise, initializes it to `1`.
3. Returns `{ apple: 3, banana: 2, orange: 1 }`.

---

## **Comparison Summary**

| **Method**   | **Purpose**                           | **Returns**             | **Modifies Original Array?** |
| ------------ | ------------------------------------- | ----------------------- | ---------------------------- |
| **map()**    | Transforms each element of the array  | A new transformed array | No                           |
| **filter()** | Filters elements based on a condition | A new filtered array    | No                           |
| **reduce()** | Reduces the array to a single value   | A single value          | No                           |

---

## **When to Use Which Method?**

- **Use `map()`**: For transforming or modifying all elements of an array to produce a new array.

  - Example: Converting an array of temperatures from Celsius to Fahrenheit.

- **Use `filter()`**: For extracting a subset of elements from an array that satisfy a given condition.

  - Example: Extract all students with grades above 80.

- **Use `reduce()`**: For aggregating, accumulating, or building a single value or object from an array.
  - Example: Calculating the total price of items in a cart.

---

These methods form the backbone of functional programming in JavaScript, allowing for clean, concise, and expressive code. With practice, their use becomes intuitive and highly efficient for array manipulations.
