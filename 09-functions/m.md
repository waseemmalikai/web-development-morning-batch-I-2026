# **Functions in JavaScript**
### **Objective**:
By the end of this chapter, students will understand how to define, call, and use functions to write clean, reusable, and efficient JavaScript code. They’ll learn about function declarations, expressions, scope, closures, recursion, and modern features like arrow functions and default parameters.

---

## **1. Introduction to Functions**
### **Why Functions?**
- **Avoid repetition**: Functions let you reuse code (e.g., logging, calculations).
- **Modularity**: Break complex tasks into smaller, manageable pieces.
- **Abstraction**: Hide implementation details behind a simple interface.

**Example**:
```js
// Without functions
console.log("Hello, Alice!");
console.log("Hello, Bob!");
console.log("Hello, Charlie!");

// With functions
function greet(name) {
    console.log(`Hello, ${name}!`);
}
greet("Alice");
greet("Bob");
greet("Charlie");
```

---

## **2. Defining Functions**
### **A. Function Declarations**
- Syntax: `function name(parameters) { ... }`
- Hoisted: Can be called before declaration.
- **Example**:
  ```js
  function square(number) {
      return number * number;
  }
  console.log(square(4)); // 16
  ```

### **B. Function Expressions**
- Syntax: `const name = function(parameters) { ... };`
- Not hoisted: Must be defined before calling.
- **Example**:
  ```js
  const square = function(number) {
      return number * number;
  };
  console.log(square(4)); // 16
  ```

### **C. Arrow Functions**
- Shorter syntax: `(parameters) => { ... }`
- No `this`, `arguments`, or `new` binding.
- **Example**:
  ```js
  const square = (number) => number * number;
  console.log(square(4)); // 16
  ```

---

## **3. Calling Functions**
### **A. Basic Function Calls**
- **Example**:
  ```js
  function greet(name) {
      return `Hello, ${name}!`;
  }
  console.log(greet("Alice")); // "Hello, Alice!"
  ```

### **B. Parameters and Arguments**
- **Parameters**: Placeholders in the function definition.
- **Arguments**: Actual values passed to the function.
- **Example**:
  ```js
  function add(a, b) {
      return a + b;
  }
  console.log(add(2, 3)); // 5
  ```

### **C. Default Parameters**
- Provide fallback values for missing arguments.
- **Example**:
  ```js
  function greet(name = "Guest") {
      return `Hello, ${name}!`;
  }
  console.log(greet()); // "Hello, Guest!"
  ```

---

## **4. Function Scope and Closures**
### **A. Local and Global Scope**
- **Local variables**: Only accessible inside the function.
- **Global variables**: Accessible everywhere (use sparingly).
- **Example**:
  ```js
  let globalVar = "I'm global";
  function showScope() {
      let localVar = "I'm local";
      console.log(globalVar); // "I'm global"
      console.log(localVar);  // "I'm local"
  }
  showScope();
  // console.log(localVar); // Error: localVar is not defined
  ```

### **B. Closures**
- Functions remember their outer scope even after execution.
- **Example**:
  ```js
  function outer() {
      let outerVar = "I'm outer";
      function inner() {
          console.log(outerVar); // "I'm outer"
      }
      return inner;
  }
  const innerFunc = outer();
  innerFunc();
  ```

### **C. IIFE (Immediately Invoked Function Expressions)**
- Run once and create a private scope.
- **Example**:
  ```js
  (function() {
      console.log("I run immediately!");
  })();
  ```

---

## **5. Advanced Function Concepts**
### **A. Recursion**
- Functions calling themselves.
- **Example**:
  ```js
  function factorial(n) {
      return n <= 1 ? 1 : n * factorial(n - 1);
  }
  console.log(factorial(5)); // 120
  ```

### **B. The `arguments` Object**
- Access all arguments passed to a function.
- **Example**:
  ```js
  function sumAll() {
      let sum = 0;
      for (let i = 0; i < arguments.length; i++) {
          sum += arguments[i];
      }
      return sum;
  }
  console.log(sumAll(1, 2, 3)); // 6
  ```

### **C. Rest Parameters**
- Collect variable arguments into an array.
- **Example**:
  ```js
  function sumAll(...args) {
      return args.reduce((sum, num) => sum + num, 0);
  }
  console.log(sumAll(1, 2, 3)); // 6
  ```

---

## **6. Functions and Loops**
### **A. Functions as Loop Helpers**
- Encapsulate loop logic for reusability.
- **Example**:
  ```js
  function logItems(items) {
      for (const item of items) {
          console.log(item);
      }
  }
  logItems(["apple", "banana", "cherry"]);
  ```

### **B. Functional Iteration**
- Use `map`, `filter`, and `reduce` to replace loops.
- **Example**:
  ```js
  const numbers = [1, 2, 3, 4];
  const doubled = numbers.map(num => num * 2); // [2, 4, 6, 8]
  ```

---

## **7. Best Practices**
### **A. Naming Functions**
- Use verbs (e.g., `getUser`, `calculateTotal`).
- Keep names descriptive and concise.

### **B. One Function, One Task**
- Avoid functions that do too much.
- **Example**:
  ```js
  // Bad: Does multiple things
  function processUser(user) {
      const fullName = `${user.firstName} ${user.lastName}`;
      console.log(fullName);
      return fullName.toUpperCase();
  }

  // Good: Single responsibility
  function getFullName(user) {
      return `${user.firstName} ${user.lastName}`;
  }
  function logAndUppercase(text) {
      console.log(text);
      return text.toUpperCase();
  }
  ```

### **C. Avoid Side Effects**
- Prefer pure functions (same input → same output).
- **Example**:
  ```js
  // Impure: Modifies external state
  let total = 0;
  function addToTotal(num) {
      total += num;
  }

  // Pure: No side effects
  function add(a, b) {
      return a + b;
  }
  ```

---

## **8. Common Pitfalls**
### **A. Closures in Loops**
- Use `let` or IIFE to avoid issues.
- **Example**:
  ```js
  for (let i = 0; i < 3; i++) {
      setTimeout(() => console.log(i), 1000); // Logs 0, 1, 2
  }
  ```

### **B. Forgetting to Return**
- Always return a value if the function is meant to produce one.
- **Example**:
  ```js
  function add(a, b) {
      a + b; // Missing return!
  }
  console.log(add(2, 3)); // undefined
  ```

---

## **9. Exercises**
1. **Basic Function**: Write a function `multiply(a, b)` that returns the product of `a` and `b`.
2. **Default Parameters**: Write a function `greet(name, greeting = "Hello")` that greets a user.
3. **Closure**: Create a function `createCounter()` that returns a function to increment and log a counter.
4. **Recursion**: Write a recursive function `fibonacci(n)` to return the nth Fibonacci number.
5. **Refactor Loops**: Rewrite a `for` loop using `map` or `filter`.

---

## **10. Summary**
- Functions are **reusable blocks of code**.
- Use **declarations** for hoisting, **expressions** for flexibility, and **arrow functions** for conciseness.
- Understand **scope**, **closures**, and **recursion**.
- Prefer **pure functions** and **functional iteration** for cleaner code.
