
# 📘 09 -  Functions Basics in javaScript

Functions are one of the **main building blocks** of JavaScript. They allow code to be reused many times without repetition, making scripts clean, efficient, and maintainable.

For example:

* Show a message when a visitor logs in.
* Show another message when they log out.
* Reuse the same code in different parts of the program.

We’ve already seen built-in functions like `alert()`, `prompt()`, and `confirm()`.
But we can also create our own functions.

---

## 🔹 Function Declaration

A function is declared with the `function` keyword:

```js
function showMessage() {
  alert('Hello everyone!');
}
```

Syntax:

```js
function name(parameter1, parameter2, ... parameterN) {
  // function body
}
```

Calling the function:

```js
showMessage();
showMessage(); // executes again
```

✅ Avoids code duplication. If logic changes, update only in one place.

---

## 🔹 Local Variables

Variables declared inside a function are only visible inside that function.

```js
function showMessage() {
  let message = "Hello, I'm JavaScript!";
  alert(message);
}

showMessage(); // works
alert(message); // ❌ Error
```

---

## 🔹 Outer Variables

A function can also access variables declared outside of it.

```js
let userName = 'John';

function showMessage() {
  let message = 'Hello, ' + userName;
  alert(message);
}

showMessage(); // Hello, John
```

Functions can **modify outer variables**:

```js
let userName = 'John';

function showMessage() {
  userName = "Bob"; // modifies outer variable
  alert('Hello, ' + userName);
}

alert(userName); // John
showMessage();
alert(userName); // Bob
```

⚠️ If a local variable has the same name, it **shadows** the outer variable.

---

## 🔹 Global Variables

* Declared outside any function.
* Visible everywhere (unless shadowed).
* Best practice → minimize usage, store only project-wide data.

---

## 🔹 Parameters & Arguments

Functions accept data using **parameters**.

```js
function showMessage(from, text) {
  alert(from + ': ' + text);
}

showMessage('Ann', 'Hello!'); 
showMessage('Ann', "What's up?");
```

* **Parameters** → variables in the function declaration.
* **Arguments** → values passed when calling.

### Example with parameter modification:

```js
function showMessage(from, text) {
  from = '*' + from + '*'; // modify copy
  alert(from + ': ' + text);
}

let from = "Ann";
showMessage(from, "Hello"); // *Ann*: Hello
alert(from); // Ann (unchanged outside)
```

---

## 🔹 Default Values

If a parameter is missing → it becomes `undefined`.

```js
function showMessage(from, text = "no text given") {
  alert(from + ": " + text);
}

showMessage("Ann"); // Ann: no text given
```

### Evaluation of Defaults

* Default parameters are evaluated **each time** the function is called.
* Example:

```js
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() only runs if text is not provided
}
```

---

## 🔹 Default Parameters in Old JavaScript

Before ES6, defaults were implemented manually:

```js
function showMessage(from, text) {
  if (text === undefined) {
    text = 'no text given';
  }
  alert(from + ": " + text);
}
```

Or using `||` operator:

```js
function showMessage(from, text) {
  text = text || 'no text given'; 
  alert(from + ": " + text);
}
```

---

## 🔹 Alternative Default Parameters

You can assign defaults later:

```js
function showMessage(text) {
  if (text === undefined) {
    text = 'empty message';
  }
  alert(text);
}
```

Using `||` operator:

```js
function showMessage(text) {
  text = text || 'empty';
  alert(text);
}
```

Using **nullish coalescing (`??`)**:

```js
function showCount(count) {
  alert(count ?? "unknown");
}

showCount(0);    // 0
showCount(null); // unknown
showCount();     // unknown
```

---

## 🔹 Returning a Value

A function can return a result:

```js
function sum(a, b) {
  return a + b;
}

let result = sum(1, 2);
alert(result); // 3
```

### Multiple Returns

```js
function checkAge(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm('Do you have permission from your parents?');
  }
}
```

### Return without value

```js
function doNothing() {}
alert(doNothing() === undefined); // true
```

Equivalent:

```js
function doNothing() {
  return;
}
```

---

## 🔹 Return Pitfalls

⚠️ Never break a line right after `return`.

Bad:

```js
return
  (a + b); // ❌ returns undefined
```

Good:

```js
return (
  a + b
);
```

---

## 🔹 Function Naming

Functions are **actions** → names should be verbs.

Common prefixes:

* `show...` → display something.
* `get...` → return value.
* `calc...` → perform calculation.
* `create...` → construct object/data.
* `check...` → return boolean.

Examples:

```js
showMessage();
getAge();
calcSum();
createForm();
checkPermission();
```

---

## 🔹 One Function = One Action

A function should do exactly **one thing**.

❌ Bad examples:

* `getAge` → should only return age, not show alert.
* `createForm` → should only create form, not insert it into DOM.

✅ Keep single responsibility.

---

## 🔹 Ultrashort Names

Libraries sometimes use very short names:

* `$` → jQuery
* `_` → Lodash

⚠️ In general, descriptive names are better.

---

## 🔹 Functions as Comments

Functions make code self-describing.

Example 1 (complex):

```js
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }
    alert(i);
  }
}
```

Example 2 (cleaner):

```js
function showPrimes(n) {
  for (let i = 2; i < n; i++) {
    if (!isPrime(i)) continue;
    alert(i);
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if (n % i == 0) return false;
  }
  return true;
}
```

✅ Easier to read.

---

## 📌 Summary

* Functions are declared with `function name(params) { ... }`.
* Parameters are local variables; arguments are values passed.
* Functions may access outer variables but not vice versa.
* `return` gives back results; no `return` = `undefined`.
* Always use clear, descriptive names.
* One function = one action.

---

## 📝 Tasks

### 1. Is `else` required?

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  } else {
    return confirm('Did parents allow you?');
  }
}
```

Compare with:

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  }
  return confirm('Did parents allow you?');
}
```

---

### 2. Rewrite using `?` or `||`

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  } else {
    return confirm('Did parents allow you?');
  }
}
```

---

### 3. Function `min(a, b)`

Return the smaller of two numbers.

```js
min(2, 5) == 2
min(3, -1) == -1
min(1, 1) == 1
```

---

### 4. Function `pow(x, n)`

Return `x` raised to the power `n`.

```js
pow(3, 2) = 9
pow(3, 3) = 27
pow(1, 100) = 1
```

👉 Build a webpage that prompts for `x` and `n` and shows result.

---
