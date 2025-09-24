# 📘 Chapter: Loops in JavaScript — Repeat with Purpose

> **“Computers excel at doing boring things over and over. Loops let us harness that power.”**

---

## 🌟 1. Why Do We Need Loops?

Imagine you’re teaching a robot to walk 5 steps east:

```js
console.log("Step 1");
console.log("Step 2");
console.log("Step 3");
console.log("Step 4");
console.log("Step 5");
```

That works—but what if you need **100 steps**? Or **1 million**?

Enter **loops**: a way to repeat code **as long as a condition is true**.

✅ **Benefits of loops**:
- Avoid repetitive code
- Reduce errors
- Scale effortlessly
- Make programs dynamic

---

## 🔁 2. The Loop Family: 5 Types in JavaScript

| Loop Type        | Best Used For                          | Key Feature |
|------------------|----------------------------------------|-------------|
| `for`            | Known number of iterations (e.g., arrays) | Most flexible |
| `while`          | Unknown iterations, check **before**   | Simple & clean |
| `do...while`     | Must run **at least once**             | Check **after** |
| `for...in`       | Loop over **object keys**              | ❌ Not for arrays! |
| `for...of`       | Loop over **values** (arrays, strings, etc.) | ✅ Safe & modern |
| `for await...of` | Iterating over async iterable objects	 | Used inside async functions to loop over asynchronous data, awaiting each result before proceeding.
 |
| `forEach`       | Loop over **values** (mosthly for arrays) | 	Doesn't return a new array, cannot break |
| `map`       | Loop over **values** (mosthly for arrays) | Returns a new array with transformed elements
|
| `filter`       | Loop over **values** (mosthly for arrays) | Returns a new array with elements that pass a test
 |
| `reduce()`       | Loop over **values** (mosthly for arrays) | Returns a single value by accumulating results
| `Recursion`       | Problems that can be broken into similar sub-problems	 | A function that calls itself until a "base case" is met. Can be more elegant but carries a risk of "stack overflow".|
| `Labeled statements` | Controlling nested loops| A way to name a loop or code block so break or continue can exit or jump to a specific labeled block.|



> 💡 **Rule of thumb**:  
> - Use `for` or `for...of` for **arrays**  
> - Use `for...in` only for **plain objects**  
> - Use `while`/`do...while` for **user input or unknown counts**

---

## 🧱 3. The `for` Loop — The Workhorse

### 🔤 Syntax
```js
for (initialization; condition; afterthought) {
  // loop body
}
```

### 🔄 How It Runs (Step-by-Step)
1. Run `initialization` → **once**, at the start  
2. Check `condition` → if **false**, **stop**  
3. Run the **loop body**  
4. Run `afterthought` (e.g., `i++`)  
5. Go back to Step 2

### ✅ Example
```js
for (let i = 0; i < 3; i++) {
  console.log(i); // Output: 0, 1, 2
}
```

### 🔍 Visual Trace
| Step | `i` | Condition (`i < 3`) | Action |
|------|-----|----------------------|--------|
| 1    | 0   | true                 | log 0 → i++ → i=1 |
| 2    | 1   | true                 | log 1 → i++ → i=2 |
| 3    | 2   | true                 | log 2 → i++ → i=3 |
| 4    | 3   | **false**            | **loop ends** |

### 🚨 Common Pitfall: Off-by-One Error
```js
const fruits = ["apple", "banana", "cherry"];
for (let i = 0; i <= fruits.length; i++) {
  console.log(fruits[i]); // Logs: apple, banana, cherry, **undefined**!
}
```
✅ **Fix**: Use `i < fruits.length` (not `<=`)

> 💡 **Pro Tip**: The variable (`i`) is **block-scoped**—it vanishes after the loop!

---

## 🔄 4. `while` vs `do...while`

### `while`: Check **Before** Running
```js
let count = 0;
while (count < 3) {
  console.log(count); // 0, 1, 2
  count++;
}
```
→ If condition is **false at start**, loop **never runs**.

### `do...while`: Run **Once**, Then Check
```js
let tries = 10;
do {
  console.log("Attempt:", tries); // Logs "Attempt: 10" **once**
  tries++;
} while (tries < 5);
```
→ **Always runs at least once**, even if condition is false.

### ✅ When to Use `do...while`?
- Input validation (e.g., “Enter a number > 100”)
- Game turns (“Roll dice at least once”)

---

## 🧩 5. `for...in` vs `for...of` — Know the Difference!

| Feature          | `for...in`                     | `for...of`                     |
|------------------|-------------------------------|-------------------------------|
| **Loops over**   | **Keys** (property names)     | **Values**                    |
| **Best for**     | Plain objects                 | Arrays, Strings, Maps, Sets   |
| **Array-safe?**  | ❌ **No!**                    | ✅ **Yes!**                   |
| **Order**        | Not guaranteed for arrays     | Guaranteed                    |

### ❌ Dangerous: `for...in` on Arrays
```js
const nums = [10, 20, 30];
Array.prototype.hack = "oops"; // (Some library might do this!)

for (let key in nums) {
  console.log(key); // "0", "1", "2", **"hack"** → 🚨 Bug!
}
```

### ✅ Safe: `for...of` on Arrays
```js
for (let value of nums) {
  console.log(value); // 10, 20, 30 → **only values!**
}
```

### 💡 Bonus: Loop Over Object Entries
```js
const user = { name: "Ali", age: 25 };

for (const [key, value] of Object.entries(user)) {
  console.log(`${key}: ${value}`);
}
// Output:
// name: Ali
// age: 25
```

> 🚫 **Golden Rule**: **Never use `for...in` on arrays.** Use `for...of` or classic `for`.

---

## ⚡ 6. Control Flow: `break` and `continue`

### `break` → **Exit** the loop immediately
```js
for (let i = 1; i <= 10; i++) {
  if (i === 5) break;
  console.log(i); // 1, 2, 3, 4
}
```

### `continue` → **Skip** to next iteration
```js
for (let i = 0; i < 6; i++) {
  if (i % 2 === 0) continue; // skip even numbers
  console.log(i); // 1, 3, 5
}
```

> 💡 **Why use `continue`?** It reduces nesting and keeps code flat:
> ```js
> // Instead of:
> if (condition) {
>   // 10 lines of code
> }
>
> // Do:
> if (!condition) continue;
> // 10 lines of code (no extra indent!)
> ```

---

## 🏷️ 7. Labeled Loops (Advanced)

Need to break out of **nested loops**? Use **labels**.

### Example: Coordinate Input
```js
outer: for (let x = 0; x < 3; x++) {
  for (let y = 0; y < 3; y++) {
    const input = prompt(`Enter value for (${x}, ${y})`);
    if (input === null) break outer; // Exit **both** loops!
  }
}
console.log("Done!");
```

> 🔐 **Note**:  
> - `break label` jumps **out** of the labeled loop  
> - `continue label` jumps to **next iteration** of the labeled loop  
> - Labels are rare—but **essential** for complex control flow

---

## 🛠️ 8. Modern Alternatives (Preview)

For arrays, JavaScript offers **functional methods** that often replace loops:

```js
const numbers = [1, 2, 3, 4];

// Instead of for...of
numbers.forEach(n => console.log(n));

// Transform
const doubled = numbers.map(n => n * 2); // [2, 4, 6, 8]

// Filter
const evens = numbers.filter(n => n % 2 === 0); // [2, 4]
```

> We’ll explore these in the **Arrays & Functional Programming** chapter!

---

## 🧪 9. Practice Challenges

### 🔹 Level 1: Fix the Loop
Make this print `0` to `4` (not `0` to `5`):
```js
for (let i = 0; i <= 5; i++) {
  console.log(i);
}
```
✅ **Solution**: Change `<=` to `<`

---

### 🔹 Level 2: Rewrite with `while`
Convert this `for` loop to `while`:
```js
for (let i = 10; i > 0; i--) {
  console.log(i);
}
```
✅ **Solution**:
```js
let i = 10;
while (i > 0) {
  console.log(i);
  i--;
}
```

---

### 🔹 Level 3: Input Validator
Keep asking the user for a number **greater than 100** until they comply or cancel.
```js
// Your code here
```
✅ **Solution**:
```js
let num;
do {
  num = +prompt("Enter a number > 100:", "");
} while (num <= 100 && num);
```

---

### 🔹 Level 4 (Hard): Prime Numbers
Write a program that prints all **prime numbers** from `2` to `n`.

> A prime number is only divisible by `1` and itself.

✅ **Hint**: Use a nested loop to check divisibility.

---

## ✅ 10. Summary Cheat Sheet

| Loop | Use When… | Example |
|------|----------|--------|
| `for` | You know how many times to loop | `for (let i = 0; i < arr.length; i++)` |
| `while` | Loop until condition becomes false | `while (userInput !== "quit")` |
| `do...while` | Must run at least once | Input prompts |
| `for...in` | Loop over **object keys** | `for (let key in obj)` |
| `for...of` | Loop over **array values** | `for (let item of arr)` |

### 🚫 Never Do This:
- Use `for...in` on arrays
- Forget to update loop counters (→ infinite loop!)
- Use `i <= arr.length` (→ `undefined`)

### ✅ Always Do This:
- Prefer `for...of` for arrays
- Use `break` for early exit
- Use `continue` to reduce nesting

---

> 💬 **Final Thought**:  
> “Loops are the heartbeat of programs—steady, reliable, and powerful. Master them, and you master repetition.”

---

## 📎 Appendix: Quick Reference

```js
// Classic for
for (let i = 0; i < 5; i++) { }

// While
let i = 0;
while (i < 5) { i++; }

// Do...while
let i = 0;
do { i++; } while (i < 5);

// For...in (objects only!)
for (let key in obj) { }

// For...of (arrays, strings, etc.)
for (let value of iterable) { }

// Break & continue
if (skip) continue;
if (done) break;

// Labeled loop
label: for (;;) { break label; }
```


Happy coding  🎓💻