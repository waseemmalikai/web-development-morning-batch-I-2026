# 🎬 Chapter 04: Data Types & Structures in JavaScript

### 🎯 Objective

By the end of this chapter, you will understand **all the data types in JavaScript**, how they work in memory, when to use them, and common mistakes to avoid.

---

## 🧠 What is a Data Type?

Imagine you walk into a supermarket 🛒.
There are different **sections**: fruits 🍎, dairy 🥛, bakery 🥖, frozen food ❄️.

Each section stores a **different type of item**.

👉 In the same way, **JavaScript needs to know what type of data you’re working with** — numbers, text, true/false values, lists, or collections.

Without data types, everything would be a big mess!

---

## 🔍 Why Data Types Are Important

1. They tell JavaScript **what kind of operations are possible**.

   * You can **add numbers** ➝ `5 + 10`
   * But you can’t **add names** ➝ `"Ali" + "Sara"` gives `"AliSara"` (string concatenation).

2. They help manage **memory** efficiently.

   * A number takes less memory than a big list of students.

3. They prevent **bugs** in your program.

---

## 🟩 Primitive Data Types (7 in total)

Primitive = simple, single value.
They are **immutable** (unchangeable once created).

📌 Think of primitives like “pages in a book.” If you want to change the content, you don’t erase — you create a **new page**.

---

### ✅ Type Checking with `typeof`

```js
console.log(typeof "Hello");   // string
console.log(typeof 99);        // number
console.log(typeof true);      // boolean
console.log(typeof null);      // object ❗ (weird bug in JS)
console.log(typeof []);        // object
```

---

### 1. **String** – Text values

Strings are like sentences, names, or messages.

```js
let name = "Alice";
let greeting = 'Hello!';
```

📌 Use quotes ("" or '').
📌 You can join strings with `+`.

---

### 2. **Number** – Integers & Decimals

```js
let age = 25;
let price = 19.99;
```

👉 JavaScript has **only one type** for all numbers.

---

### 3. **Boolean** – True/False

Used in decisions (yes/no, on/off).

```js
let isStudent = true;
let isMarried = false;
```

---

### 4. **Undefined** – Declared but not assigned

```js
let email;
console.log(email); // undefined
```

---

### 5. **Null** – Intentionally empty

```js
let accountBalance = null;
```

👉 Means: “I know this is empty.”

---

### 6. **Symbol** – Unique identifier (ES6)

```js
const id1 = Symbol("userId");
const id2 = Symbol("userId");

console.log(id1 === id2); // false
```

👉 Even if description is same, each Symbol is unique.

---

### 7. **BigInt** – Very large integers (ES2020)

```js
let bigNum = 123456789123456789123456789n;
```

👉 Add `n` at the end.

---

## 🧠 Recap Table

| Type      | Example     | Meaning          |
| --------- | ----------- | ---------------- |
| String    | `"Ali"`     | Text             |
| Number    | `42, 19.99` | Numbers          |
| Boolean   | `true`      | Yes/No           |
| Undefined | `let x;`    | Not assigned     |
| Null      | `null`      | Empty on purpose |
| Symbol    | `Symbol()`  | Unique token     |
| BigInt    | `123n`      | Big numbers      |

---

## 🟦 Non-Primitive (Reference) Data Types

Non-primitive = collections or objects.
They are **mutable** (can be changed).

📌 Think of them like “folders” — you can keep adding, removing, or editing inside.

---

### 1. **Object** – Key-value pairs

```js
let person = {
  name: "Sara",
  age: 21
};
```

---

### 2. **Array** – Ordered list

```js
let fruits = ["apple", "banana", "mango"];
console.log(fruits[0]); // apple
```

📌 Index starts at `0`.

---

### 3. **Function** – Reusable block

```js
function greet(name) {
  return "Hello " + name;
}

console.log(greet("Ali")); // Hello Ali
```

👉 Functions are also objects in JS.

---

### 4. **Date Object**

```js
let today = new Date();
console.log(today);
```

---

### 5. **Regular Expressions (RegExp)**

```js
let pattern = /hello/i;
console.log(pattern.test("Hello World")); // true
```

👉 Used for **pattern matching**.

---

## ⚙️ JavaScript is Dynamically Typed

```js
let x = 5;       // number
x = "Hello";     // now string
x = [1, 2, 3];   // now array
```

📌 The type belongs to the **value**, not the variable.

---

## ⚠️ Weird JavaScript Facts

* `typeof null` → `object` (bug, but kept for legacy reasons).
* `NaN` is a number → `typeof NaN` gives `number`.
* Strings behave like objects temporarily.

```js
let name = "Ali";
console.log(name.length); // 3
```

---

## 🧠 Null vs Undefined

| Feature | Undefined          | Null             |
| ------- | ------------------ | ---------------- |
| Meaning | Declared, no value | Empty on purpose |
| Set by  | JavaScript         | Developer        |
| Type    | undefined          | object (bug)     |

---

## 🧪 Practice

1. Create variables for all primitive types.
2. Create an object for your profile.
3. Use `typeof` on each one.
4. Test: `typeof null` → ?

---

## 🎯 Mini Project – User Profile Card

```js
let fullName = "Ali Khan";
let age = 22;
let isStudent = true;
let hobbies = ["coding", "reading"];
let contact = { email: "ali@gmail.com", phone: "123456" };

console.log(fullName, age, isStudent, hobbies, contact);
```

---

## 📚 Homework

1. Create a **shopping cart array** with 5 items.
2. Create an object for a **book** (title, author, price).
3. Create a function that greets a user with their name.
4. Try adding a `BigInt` value.

---

✅ And that’s all for **Chapter 04: Data Types & Structures**.
