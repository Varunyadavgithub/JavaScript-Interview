## 4. What are Arrow Functions and How Are They Different from Regular Functions?

Arrow functions were introduced in ES6 (ECMAScript 2015) as a concise syntax for writing functions in JavaScript. They offer a shorter way to define functions compared to the traditional `function` keyword.

#### Syntax of Arrow Functions
Here’s the syntax for an arrow function:

```javascript
// Regular function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => a + b;
```

#### Key Features of Arrow Functions
1. **Concise Syntax:**
   - Arrow functions allow you to write cleaner and shorter function expressions.
   - If the function body has only one statement and that statement returns a value, you can omit the braces `{}` and the `return` keyword.

   ```javascript
   // Regular function
   const square = function (x) {
     return x * x;
   };

   // Arrow function
   const square = x => x * x;
   ```

2. **Implicit `return`:**
   - If the function body is a single expression, the result of that expression is returned automatically.

   ```javascript
   const greet = () => 'Hello!';
   ```

3. **No `this` Binding:**
   - Arrow functions do not have their own `this`. Instead, they inherit `this` from their surrounding (lexical) scope.
   - This makes arrow functions particularly useful in scenarios where preserving the context of `this` is important, such as in callbacks.

   ```javascript
   function Person() {
     this.age = 0;

     setInterval(() => {
       this.age++;
       console.log(this.age); // Correctly refers to the enclosing `this`
     }, 1000);
   }

   const p = new Person();
   ```

4. **Cannot Be Used as Constructors:**
   - Arrow functions cannot be used with the `new` keyword because they do not have their own `this`.

   ```javascript
   const MyClass = () => {};
   const obj = new MyClass(); // TypeError: MyClass is not a constructor
   ```

5. **No `arguments` Object:**
   - Arrow functions do not have their own `arguments` object. Instead, you can use rest parameters (`...args`) to achieve a similar effect.

   ```javascript
   const sum = (...args) => args.reduce((total, num) => total + num, 0);
   console.log(sum(1, 2, 3)); // 6
   ```

6. **Cannot Use `yield`:**
   - Arrow functions cannot be used as generator functions because they do not have a `yield` keyword.

#### Differences Between Arrow Functions and Regular Functions
| **Aspect**              | **Arrow Functions**                                         | **Regular Functions**                          |
|-------------------------|-----------------------------------------------------------|------------------------------------------------|
| **Syntax**              | Concise and compact                                      | Verbose                                        |
| **`this` Binding**      | Lexical (inherits `this` from the parent scope)          | Dynamic (depends on how the function is called) |
| **`arguments` Object**  | Not available; use rest parameters instead               | Available by default                           |
| **Constructor Usage**   | Cannot be used as constructors                           | Can be used as constructors                    |
| **`yield` Keyword**     | Cannot be used                                           | Can be used in generator functions             |

#### Example
```javascript
// Regular function
function RegularFunction() {
  console.log(this); // Refers to the calling context
}

// Arrow function
const ArrowFunction = () => {
  console.log(this); // Refers to the surrounding context
};

// Example of lexical `this` in arrow functions
const person = {
  name: 'Varun',
  greet: function () {
    const sayHi = () => console.log(`Hi, ${this.name}`);
    sayHi(); // Arrow function captures `this` from `greet` method
  }
};

person.greet(); // Hi, Varun
```

Arrow functions simplify coding in many situations, especially when dealing with callbacks or methods requiring lexical `this`. However, they should not be used when a dynamic `this` or `arguments` object is required.