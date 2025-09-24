
# 📘 Chapter 8: Loops in JavaScript (Mastering Repetition)

👉 *Goal of this chapter*: By the end, you’ll fully understand **all types of loops in JavaScript** (`while`, `do…while`, `for`, `for…in`, `for…of`) and know how to apply them in real projects.

---

## 🧠 1. Why Do We Need Loops?

Imagine you want to print numbers `1 to 100`.
Without loops, you’d need to write:

```js
console.log(1);
console.log(2);
console.log(3);
// ... up to 100
```

This is boring ❌, repetitive ❌, and unscalable ❌.
Instead, we use **loops** → code that repeats automatically until a condition is met ✅.

---

## 🔄 2. The `while` Loop

👉 Syntax:

```js
while (condition) {
  // loop body
}
```

* Runs **as long as** the condition is true.
* If the condition becomes false → loop stops.

### Example:

```js
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

✅ Prints → 0, 1, 2, 3, 4

⚠️ If you forget `i++`, the loop will run **forever** (infinite loop).

---

## 🔂 3. The `do…while` Loop

👉 Syntax:

```js
do {
  // loop body
} while (condition);
```

* **Runs the code at least once**, then checks condition.

### Example:

```js
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 3);
```

✅ Prints → 0, 1, 2
Even if `i` was already `5`, the loop body runs once.

---

## 🔁 4. The `for` Loop

👉 Syntax:

```js
for (begin; condition; step) {
  // loop body
}
```

* `begin` → runs once at start.
* `condition` → checked before every iteration.
* `step` → runs after each iteration.

### Example:

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

✅ Prints → 0, 1, 2, 3, 4

---

### Variations of `for`

* Omit `begin`:

```js
let i = 0;
for (; i < 3; i++) console.log(i);
```

* Omit `step`:

```js
let i = 0;
for (; i < 3;) {
  console.log(i++);
}
```

* Infinite loop:

```js
for (;;) {
  // runs forever until break
}
```

---

## ⚡ 5. Control Flow in Loops

### `break`

Stops loop immediately.

```js
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i);
}
// Output: 0,1,2,3,4
```

### `continue`

Skips current iteration and goes to next one.

```js
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue;
  console.log(i);
}
// Output: 1,3,5,7,9
```

---

## 🎯 6. Advanced: Labels with Loops

Normally `break` only exits **one loop**.
But with **labels**, you can exit multiple loops.

```js
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) break outer;
    console.log(`i=${i}, j=${j}`);
  }
}
```

✅ Exits both loops when `i=1, j=1`.

---

## 📦 7. Looping Over Objects and Arrays

### `for…in` → loop over **object properties**

```js
let person = { name: "Ali", age: 25, city: "Lahore" };
for (let key in person) {
  console.log(key, ":", person[key]);
}
```

✅ Output:

```
name : Ali
age : 25
city : Lahore
```

---

### `for…of` → loop over **iterables** (arrays, strings, etc.)

```js
let numbers = [10, 20, 30];
for (let num of numbers) {
  console.log(num);
}
```

✅ Output:

```
10
20
30
```

Works with strings too:

```js
for (let ch of "JS") console.log(ch);
// Output: J, S
```

---

## 🛠️ 8. Mini Projects with Loops

### 🔢 1. Countdown Timer

```js
for (let i = 10; i >= 1; i--) {
  console.log(i);
}
console.log("Happy New Year!");
```

### 📊 2. Multiplication Table

```js
let num = 5;
for (let i = 1; i <= 10; i++) {
  console.log(`${num} x ${i} = ${num * i}`);
}
```

### ✅ 3. Login Simulator

```js
let correctPassword = "1234";
let input;

do {
  input = prompt("Enter password:");
} while (input !== correctPassword);

alert("Access Granted!");
```

---

## 🏋️ 9. Practice Tasks

1. Print numbers **1–20**, skipping multiples of 3.
2. Find the sum of numbers from **1–100**.
3. Print all even numbers from **2 to 50**.
4. Write a loop that keeps asking the user for a number > 100 until they enter it.
5. Print all prime numbers up to `n`.

---

## 📌 10. Key Takeaways

* Use **`while`** when you don’t know how many times to loop.
* Use **`do…while`** if the loop must run **at least once**.
* Use **`for`** for counting iterations.
* Use **`for…in`** for object properties.
* Use **`for…of`** for arrays and strings.
* Master `break`, `continue`, and **labels** for control.

---

✅ Now you’re a **Loop Master in JavaScript**!
Next, we’ll use loops to power real-world apps like **shopping carts, pagination, and animations**.
