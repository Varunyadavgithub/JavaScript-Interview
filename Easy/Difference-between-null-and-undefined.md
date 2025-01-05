## 5. What is the Difference Between `null` and `undefined` in JavaScript?

In JavaScript, both `null` and `undefined` represent the absence of a value, but they are used in different contexts and have distinct meanings. Let’s explore the differences between these two:

---

### **`undefined`**
1. **Definition:**
   - `undefined` is a built-in primitive value that indicates a variable has been declared but not yet assigned a value.
   
2. **When Does It Occur?**
   - A variable is declared but not initialized.
     ```javascript
     let x;
     console.log(x); // undefined
     ```
   - A function does not return a value.
     ```javascript
     function doSomething() {}
     console.log(doSomething()); // undefined
     ```
   - Accessing a property that doesn’t exist on an object.
     ```javascript
     const obj = {};
     console.log(obj.nonExistentProperty); // undefined
     ```
   - When no argument is passed to a function parameter.
     ```javascript
     function greet(name) {
       console.log(name);
     }
     greet(); // undefined
     ```

3. **Type:**
   - The type of `undefined` is `"undefined"`.
     ```javascript
     console.log(typeof undefined); // "undefined"
     ```

---

### **`null`**
1. **Definition:**
   - `null` is a special value in JavaScript that explicitly indicates the absence of any object value. It is often used as a placeholder to intentionally signify "no value" or "empty."

2. **When Is It Used?**
   - To explicitly assign an empty or non-existent value to a variable.
     ```javascript
     let x = null;
     console.log(x); // null
     ```
   - As a return value to indicate "no object" or "nothing found."
     ```javascript
     function getUser() {
       return null; // No user available
     }
     console.log(getUser()); // null
     ```

3. **Type:**
   - The type of `null` is `"object"` due to a historical bug in JavaScript.
     ```javascript
     console.log(typeof null); // "object"
     ```

---

### **Key Differences**

| **Aspect**              | **`undefined`**                                      | **`null`**                                    |
|-------------------------|-----------------------------------------------------|-----------------------------------------------|
| **Meaning**             | A variable has been declared but not assigned a value. | Explicitly indicates the absence of a value.  |
| **Type**                | `"undefined"`                                       | `"object"` (due to a JavaScript quirk).       |
| **Usage**               | Default state of uninitialized variables, missing function arguments, or nonexistent object properties. | Used explicitly to indicate an intentional lack of value. |
| **Assignment**          | Automatically assigned by JavaScript.               | Must be explicitly assigned by the developer. |
| **Equality Comparison** | `undefined == null` is `true` (loose equality).     | `undefined === null` is `false` (strict equality). |

---

### **Examples**

1. **`undefined` Example:**
   ```javascript
   let variable; // Declared but not initialized
   console.log(variable); // undefined

   const obj = {};
   console.log(obj.property); // undefined
   ```

2. **`null` Example:**
   ```javascript
   let variable = null; // Intentionally no value
   console.log(variable); // null

   const obj = {
     key: null // Represents no value intentionally
   };
   console.log(obj.key); // null
   ```

3. **Equality Comparison:**
   ```javascript
   console.log(null == undefined); // true
   console.log(null === undefined); // false
   ```

---

### **Conclusion**
- Use `undefined` when JavaScript itself indicates the lack of an assignment or a value.
- Use `null` when you want to intentionally assign "nothing" or "no value" to a variable or object property.