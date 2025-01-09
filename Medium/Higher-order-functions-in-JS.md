### **What are higher-order functions in JavaScript ?**

Higher-order functions are a powerful and versatile feature in JavaScript that allow you to write more expressive and flexible code. A higher-order function is a function that either:

1. **Takes another function as an argument** (a callback function), or
2. **Returns a new function as its result.**

These functions enable JavaScript to support functional programming paradigms, which are key to handling complex problems in a modular way.

## Characteristics of Higher-Order Functions

- Can accept other functions as arguments.
- Can return functions as output.
- Enable the creation of abstractions and reusable utilities.

### Examples of Higher-Order Functions in JavaScript

#### 1. Functions Taking Other Functions as Arguments

Higher-order functions like `map`, `filter`, and `reduce` take callback functions as arguments.

##### Example: `map`

```javascript
const numbers = [1, 2, 3, 4, 5];

// Double each number using map
const doubled = numbers.map((num) => num * 2);

console.log(doubled); // [2, 4, 6, 8, 10]
```

#### 2. Functions Returning Other Functions

A function can return another function to create custom behavior.

##### Example: Function Returning a Function

```javascript
function multiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

## Commonly Used Higher-Order Functions

### 1. `forEach`

Executes a provided function once for each array element.

```javascript
const names = ["Alice", "Bob", "Charlie"];
names.forEach((name) => console.log(name));
// Output: Alice, Bob, Charlie
```

### 2. `filter`

Creates a new array with elements that pass the test implemented by the provided function.

```javascript
const ages = [10, 18, 21, 30, 15];
const adults = ages.filter((age) => age >= 18);

console.log(adults); // [18, 21, 30]
```

### 3. `reduce`

Executes a reducer function on each element of the array, resulting in a single output value.

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);

console.log(sum); // 10
```

### 4. `sort`

Sorts the elements of an array in place.

```javascript
const fruits = ["apple", "banana", "cherry"];
fruits.sort((a, b) => a.localeCompare(b));

console.log(fruits); // ['apple', 'banana', 'cherry']
```

## Advantages of Higher-Order Functions

1. **Code Reusability:** They allow you to abstract functionality and reuse code.
2. **Modularity:** Functions can be broken down into smaller, reusable components.
3. **Improved Readability:** Code becomes more concise and expressive.
4. **Functional Composition:** They enable chaining and functional pipelines.

## Use Cases of Higher-Order Functions

- **Data Transformation:** Use `map` and `filter` to manipulate arrays efficiently.
- **Asynchronous Programming:** Pass callback functions to handle asynchronous operations (e.g., `setTimeout` or Promises).
- **Custom Utility Functions:** Create dynamic behavior by returning functions.

### Example: Asynchronous Callbacks

```javascript
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);
```

### Example: Chaining Higher-Order Functions

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter((num) => num % 2 === 0) // Filter even numbers
  .map((num) => num * 2); // Double the even numbers

console.log(result); // [4, 8]
```

## Key Differences Between Regular and Higher-Order Functions

| Regular Functions            | Higher-Order Functions     |
| ---------------------------- | -------------------------- |
| Perform specific tasks       | Operate on other functions |
| Return values or `undefined` | Can return functions       |
| Do not accept functions      | Can accept functions       |

## Summary

Higher-order functions are a cornerstone of functional programming in JavaScript. By enabling functions to accept other functions as arguments or return them, they provide a way to write flexible, reusable, and expressive code. Understanding and using higher-order functions effectively can significantly improve your ability to handle complex programming challenges.
