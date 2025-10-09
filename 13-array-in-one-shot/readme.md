# 🧠 JavaScript Arrays — From Scratch to Advanced

**Instructor:** Waseem Malik
**Course:** JavaScript Mastery Bootcamp
**Chapter:** Arrays

---

## 🌱 Part 1 — Array Fundamentals

---

### 1. **What is an Array?**

An **array** is a special type of object in JavaScript used to store **multiple values in a single variable**.
Each value inside the array is called an **element**, and every element has an **index** (starting from `0`).

#### Example:

```js
let fruits = ["apple", "banana", "mango"];
console.log(fruits[0]); // Output: apple
```

---

### 2. **Creating Arrays**

There are two main ways to create arrays:

#### (a) Using Array Literals (Recommended)

```js
let colors = ["red", "green", "blue"];
```

#### (b) Using Array Constructor

```js
let numbers = new Array(10, 20, 30);
```

✅ **Note:** Using literals is preferred for cleaner, faster, and safer code.

---

### 3. **Accessing and Modifying Elements**

Each array element is accessed by its **index number**.

```js
let fruits = ["apple", "banana", "mango"];
console.log(fruits[1]); // banana

fruits[2] = "grape"; // modify element
console.log(fruits); // ["apple", "banana", "grape"]
```

---

### 4. **Array Length Property**

The `.length` property returns the **number of elements** in the array.

```js
let fruits = ["apple", "banana", "mango"];
console.log(fruits.length); // 3
```

To access the **last element** dynamically:

```js
console.log(fruits[fruits.length - 1]);
```

---

### 5. **Basic Array Operations**

#### 5.1 Adding and Removing Elements

| Operation         | Method      | Example                    |
| ----------------- | ----------- | -------------------------- |
| Add to end        | `push()`    | `fruits.push("kiwi");`     |
| Remove from end   | `pop()`     | `fruits.pop();`            |
| Add to start      | `unshift()` | `fruits.unshift("berry");` |
| Remove from start | `shift()`   | `fruits.shift();`          |

```js
let fruits = ["apple", "banana"];
fruits.push("orange"); // ["apple","banana","orange"]
fruits.pop();          // ["apple","banana"]
```

---

### 6. **Searching Elements**

#### (a) `indexOf()`

Finds the index of an element.
Returns `-1` if not found.

```js
let fruits = ["apple", "banana", "mango"];
console.log(fruits.indexOf("banana")); // 1
```

#### (b) `includes()`

Checks if an element exists in the array.

```js
console.log(fruits.includes("apple")); // true
```

---

### 7. **Looping Through Arrays**

#### (a) Using `for` Loop

```js
let fruits = ["apple", "banana", "mango"];
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

#### (b) Using `for...of`

```js
for (let fruit of fruits) {
  console.log(fruit);
}
```

#### (c) Using `forEach()`

```js
fruits.forEach((fruit, index) => {
  console.log(index, fruit);
});
```

---

### 8. **Multidimensional Arrays**

An array inside another array.

```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6]
];
console.log(matrix[1][2]); // Output: 6
```

---

## 🚀 Part 2 — Advanced Array Concepts

---

### 9. **Transforming Arrays**

#### (a) `map()`

Creates a **new array** by applying a function to each element.

**Syntax:**

```js
array.map(callback(currentValue, index, array))
```

**Example:**

```js
let numbers = [1, 2, 3];
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
```

**Explanation:**
`map()` does not change the original array — it creates a new one.

---

#### (b) `filter()`

Creates a **new array** with elements that **pass a condition**.

**Example:**

```js
let numbers = [1, 2, 3, 4, 5];
let evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]
```

---

#### (c) `reduce()`

Reduces an array to a **single value** (e.g., sum, average).

**Example:**

```js
let numbers = [10, 20, 30];
let sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 60
```

---

#### (d) `find()` and `findIndex()`

Find the **first element** that matches a condition.

```js
let users = [{id: 1, name: "Ali"}, {id: 2, name: "Sara"}];
let user = users.find(u => u.id === 2);
console.log(user); // {id: 2, name: "Sara"}
```

---

#### (e) `some()` and `every()`

* `some()` → returns `true` if **at least one** element matches.
* `every()` → returns `true` if **all** elements match.

```js
let numbers = [1, 2, 3, 4];
console.log(numbers.some(n => n > 3)); // true
console.log(numbers.every(n => n > 0)); // true
```

---

### 10. **Sorting and Reversing**

#### (a) `sort()`

Sorts elements alphabetically by default.

```js
let fruits = ["banana", "apple", "mango"];
fruits.sort(); // ["apple", "banana", "mango"]
```

For numbers:

```js
let nums = [5, 2, 10];
nums.sort((a, b) => a - b); // [2, 5, 10]
```

#### (b) `reverse()`

Reverses the array order.

```js
nums.reverse(); // [10, 5, 2]
```

---

### 11. **Splice, Slice, and Concat**

#### (a) `slice(start, end)`

Copies a portion of an array.

```js
let fruits = ["apple", "banana", "mango", "orange"];
let tropical = fruits.slice(1, 3);
console.log(tropical); // ["banana", "mango"]
```

#### (b) `splice(start, deleteCount, ...items)`

Removes or replaces elements.

```js
fruits.splice(2, 1, "grape");
console.log(fruits); // ["apple","banana","grape","orange"]
```

#### (c) `concat()`

Merges arrays.

```js
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged = arr1.concat(arr2);
console.log(merged); // [1,2,3,4]
```

---

### 12. **Array Destructuring**

Extract values from arrays into variables easily.

```js
let [a, b, c] = [10, 20, 30];
console.log(a, b, c); // 10 20 30
```

#### Skipping values:

```js
let [first, , third] = ["A", "B", "C"];
```

#### Default values:

```js
let [x=5, y=10] = [2];
console.log(x, y); // 2 10
```

#### Swapping variables:

```js
let a = 1, b = 2;
[a, b] = [b, a];
console.log(a, b); // 2 1
```

---

### 13. **Spread and Rest Operators**

#### Spread:

Expands array elements.

```js
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged = [...arr1, ...arr2];
console.log(merged); // [1,2,3,4]
```

#### Rest:

Collects remaining values.

```js
let [first, ...rest] = [10, 20, 30, 40];
console.log(rest); // [20, 30, 40]
```

---

### 14. **Array Utility Methods**

| Method            | Description                   | Example                                         |
| ----------------- | ----------------------------- | ----------------------------------------------- |
| `Array.isArray()` | Checks if a value is an array | `Array.isArray([1,2])`                          |
| `Array.from()`    | Converts iterable to array    | `Array.from("hello")` → `['h','e','l','l','o']` |
| `Array.of()`      | Creates array from arguments  | `Array.of(1,2,3)` → `[1,2,3]`                   |
| `flat()`          | Flattens nested arrays        | `[1,[2,[3]]].flat(2)` → `[1,2,3]`               |

---

### 15. **Chaining Methods**

You can combine multiple array methods in one line.

```js
let numbers = [1, 2, 3, 4, 5];
let result = numbers
  .filter(n => n > 2)
  .map(n => n * 3)
  .reduce((a, b) => a + b);
console.log(result); // 27
```

---

### 16. **Performance Tips**

* Avoid mutating original arrays (use spread or `map`)
* Use `for` loops for performance-heavy operations
* Prefer `map`, `filter`, `reduce` for clean, functional code

---

### 17. **Mini Project: Student Grades Analyzer**

**Goal:**
Create an array of student marks and:

* Calculate total marks
* Find average
* Identify top scorer
* Use `map()`, `filter()`, `reduce()`

---

### 18. **Bonus: Typed Arrays**

Used for performance and binary data:

```js
let bytes = new Int8Array([10, 20, 30]);
```

---

## ✅ Summary

You’ve learned:

* Basics of arrays
* Core array methods
* Data transformations
* Destructuring, spread & rest
* Real-world use cases
* Optimization techniques

