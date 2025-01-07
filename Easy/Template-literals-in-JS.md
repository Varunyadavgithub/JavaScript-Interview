### **What are template literals in JavaScript, and how are they used ?**

Template literals, introduced in ES6 (ECMAScript 2015), are a modern way to create strings in JavaScript. They provide an easier and more readable syntax for creating and manipulating strings, including embedding expressions and using multi-line strings.

---

### **Syntax:**
Template literals are enclosed by backticks (`` ` ``) instead of single or double quotes.

#### Example:
```javascript
const greeting = `Hello, World!`;
```

---

### **Features of Template Literals**

#### 1. **String Interpolation**:
Template literals allow embedding expressions directly into strings using the `${expression}` syntax.

##### Example:
```javascript
const name = "Jone";
const age = 25;
const message = `My name is ${name} and I am ${age} years old.`;
console.log(message);
// Output: My name is Jone and I am 25 years old.
```
- **Expression inside `${}`**: Any valid JavaScript expression (variables, arithmetic operations, function calls, etc.) can be used.

---

#### 2. **Multi-line Strings**:
With template literals, you can easily create multi-line strings without using escape characters like `\n`.

##### Example:
```javascript
const multiLine = `This is a multi-line string.
It spans multiple lines.
No escape characters required.`;
console.log(multiLine);
// Output:
// This is a multi-line string.
// It spans multiple lines.
// No escape characters required.
```

---

#### 3. **Embedding Expressions**:
You can embed JavaScript expressions directly inside template literals, making them dynamic.

##### Example:
```javascript
const a = 10;
const b = 20;
const result = `The sum of ${a} and ${b} is ${a + b}.`;
console.log(result);
// Output: The sum of 10 and 20 is 30.
```

---

#### 4. **Tagged Templates**:
Tagged templates allow you to process template literals using a function. This feature is used in advanced scenarios like creating custom string formatting or preventing injection attacks.

##### Example:
```javascript
function highlight(strings, ...values) {
  return strings.reduce((result, str, i) => `${result}${str}<strong>${values[i] || ''}</strong>`, '');
}

const name = "Jone";
const age = 25;

const tagged = highlight`My name is ${name} and I am ${age} years old.`;
console.log(tagged);
// Output: My name is <strong>Jone</strong> and I am <strong>25</strong> years old.
```

---

#### 5. **Raw Strings**:
You can access the raw string content using the `String.raw` method, which is helpful for writing regular expressions or escaping characters.

##### Example:
```javascript
const rawString = String.raw`C:\Users\Jone\Documents\file.txt`;
console.log(rawString);
// Output: C:\Users\Varun\Documents\file.txt
```

---

### **Comparison with Traditional String Syntax**
| Feature               | Traditional Strings                | Template Literals         |
|-----------------------|------------------------------------|---------------------------|
| Multi-line strings    | Requires `\n` or concatenation    | Directly supports multi-line |
| String interpolation  | Concatenation with `+` operator   | Supports `${}` syntax     |
| Readability           | Less readable in complex cases    | More readable and concise |

---

### **When to Use Template Literals?**
- When you need to embed variables or expressions in strings.
- For creating multi-line strings without using escape characters.
- To simplify code and improve readability, especially when dealing with dynamic strings.

---

### **Conclusion:**
Template literals are a powerful and user-friendly feature in JavaScript that improve the way strings are created and manipulated. Their support for interpolation, multi-line strings, and advanced features like tagged templates makes them a preferred choice over traditional string syntax in modern JavaScript development.