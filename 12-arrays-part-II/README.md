
# 🟩 Chapter 12- JavaScript Array Part-2

**(map, filter, reduce, find, forEach – Beginner Friendly)**

---
> Note: before we learn about the methods let's learn about spread operator. 


## Spread Operator

The JavaScript spread operator `...` is used to expand or spread out elements of an iterable, such as an array, string, or object.

This makes it incredibly useful for tasks like combining arrays, passing elements to functions as separate arguments, or even copying arrays.

Here's a quick example of the spread statement.

```js
let numbers = [1, 2, 3];

// equivalent to
// console.log(numbers[0], numbers[1], numbers[2])
console.log(...numbers);
```
```js
// Output: 1 2 3
```

Here, we used the spread operator `...` inside console.log() to expand the numbers array into individual elements.

## Inside Arrays

We can also use the spread operator inside arrays to expand the elements of another array. 
```js
let fruits = ["Apple", "Banana", "Cherry"];

// add fruits array to moreFruits1
// without using the ... operator
let moreFruits1 = ["Dragonfruit", fruits, "Elderberry"];

// spread fruits array within moreFruits2 array
let moreFruits2 = ["Dragonfruit", ...fruits, "Elderberry"];

console.log(moreFruits1);
console.log(moreFruits2);
```
```js

[ 'Dragonfruit', [ 'Apple', 'Banana', 'Cherry' ], 'Elderberry' ]
[ 'Dragonfruit', 'Apple', 'Banana', 'Cherry', 'Elderberry' ]
```
> Here, `...fruits` expands the fruits array inside the moreFruits2 array, which results in moreFruits2 consisting only of individual string elements and no inner arrays.


On the other hand, the moreFruits1 array consists of an inner array because we didn't expand the fruits array inside it.

> Note: Since the spread operator was introduced in ES6, some browsers may not support its use. To learn more, visit JavaScript Spread Operator support.

## 🧠 1. What are Array Methods?

**Array methods** are built-in functions that allow you to work with arrays easily.

They help you:

* Transform data
* Filter values
* Loop efficiently
* Perform calculations

📌 These are **must-know** for real projects and interviews.

---

## 📋 2. Our Focus in Part 1

| Method      | Purpose                           |
| ----------- | --------------------------------- |
| `forEach()` | Loop through each item            |
| `map()`     | Transform each item               |
| `filter()`  | Select items based on a rule      |
| `reduce()`  | Combine array into a single value |
| `find()`    | Get the first match in array      |

---

## 🔁 3. `forEach()` – Loop Through Arrays

```js
let students = ["Ali", "Sara", "Zain"];

students.forEach(function(name, index) {
  console.log(index + 1 + ": " + name);
});
```

✅ Use when you want to do something **with each item**, but don’t want to return anything.

---

## 🪄 4. `map()` – Transform Each Element

```js
let numbers = [1, 2, 3];

let doubled = numbers.map(function(num) {
  return num * 2;
});

console.log(doubled); // [2, 4, 6]
```

✅ Use when you want to **create a new array** with modified values.

---

## 🔍 5. `filter()` – Filter Out Items

```js
let ages = [12, 17, 20, 25];

let adults = ages.filter(function(age) {
  return age >= 18;
});

console.log(adults); // [20, 25]
```

✅ Use when you want to **remove unwanted values** based on a condition.

---

## ➕ 6. `reduce()` – Combine All Values

```js
let prices = [100, 200, 300];

let total = prices.reduce(function(acc, price) {
  return acc + price;
}, 0);

console.log(total); // 600
```

✅ Use when you want to **sum up** or **merge** array values into one result.

---

## 🔍 7. `find()` – Get First Match

```js
let users = [
  { name: "Ali", age: 18 },
  { name: "Sara", age: 22 },
  { name: "Zain", age: 16 }
];

let adult = users.find(function(user) {
  return user.age >= 18;
});

console.log(adult); // { name: "Ali", age: 18 }
```
✅ Use when you need the **first item** that matches a rule.




## 🔍 2. `some()` – Does At Least One Pass?

```js
let scores = [85, 40, 92, 60];

let hasFail = scores.some(score => score < 50);

console.log(hasFail); // true
```

✅ Use when checking if **at least one item** meets a condition.

---

## ✅ 3. `every()` – Do All Pass?

```js
let scores = [85, 60, 92, 70];

let allPassed = scores.every(score => score >= 50);

console.log(allPassed); // true
```

✅ Use when checking if **all items** meet a rule.

---

## 🔎 4. `includes()` – Does It Exist?

```js
let fruits = ["apple", "banana", "mango"];

console.log(fruits.includes("banana")); // true
console.log(fruits.includes("grape")); // false
```

✅ Use when checking if **a specific value exists** in array.

---

## 🔀 5. `sort()` – Sort Your Array

### ❗ Caution: It changes the original array.

```js
let marks = [90, 50, 100, 70];

marks.sort(); 
console.log(marks); // [100, 50, 70, 90] – WRONG

// Correct way
marks.sort((a, b) => a - b); 
console.log(marks); // [50, 70, 90, 100]
```

✅ Use with comparator functions for **numbers**, **dates**, etc.

---

## 🔁 6. `reverse()` – Reverse an Array

```js
let names = ["Ali", "Zain", "Sara"];

names.reverse();
console.log(names); // ["Sara", "Zain", "Ali"]
```

✅ Use when displaying **recent-first** items like chat, comments, or history.

---

## 🧱 Multi-Dimensional Arrays (2D Arrays)

A multi-dimensional array is an array inside another array:

```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matrix[0][2]); // 3
console.log(matrix[2][1]); // 8
```
> 📌 Useful for tables, game grids, student marks, etc.


---

## 👨‍💻 8. Mini Project: Student Management

### ✅ Data:

```js
let students = [
  { name: "Ali", marks: 75 },
  { name: "Sara", marks: 88 },
  { name: "Zain", marks: 59 },
  { name: "Ahmed", marks: 92 }
];
```

### 🔹 1. Get Names of All Students

```js
let names = students.map(s => s.name);
console.log(names); // ["Ali", "Sara", "Zain", "Ahmed"]
```

### 🔹 2. Filter Students Who Passed

```js
let passed = students.filter(s => s.marks >= 60);
console.log(passed); // Only students with marks >= 60
```

### 🔹 3. Get Average Marks

```js
let total = students.reduce((acc, s) => acc + s.marks, 0);
let avg = total / students.length;
console.log(avg);
```

### 🔹 4. Find First Topper (> 90)

```js
let topper = students.find(s => s.marks > 90);
console.log(topper);
```

---

## 🛠 Practice Exercises

1. Create an array of product prices and use `reduce()` to get total
2. Use `map()` to convert array of Celsius to Fahrenheit
3. Use `filter()` to remove users below age 18
4. Use `find()` to get a specific student by name
5. Use `forEach()` to print names with index

---

## 💡 Best Practices

* Use `map()` when you need a new array
* Use `filter()` to reduce your dataset
* Use `reduce()` carefully — it's powerful but tricky
* Don’t use `forEach()` when you need a return
* Use arrow functions for cleaner code
* Never modify the original array (use `.slice()` if needed)

---

## 🎓 Homework Challenge

Create a student grading app:

* Input: Array of student names and scores
* Output:

  * `map()` to assign grades (A/B/C)
  * `filter()` to get failed students
  * `reduce()` to calculate class average
  * `find()` to get top performer

---



## 🔗 7. Method Chaining – Combine Multiple Methods

```js
let marks = [40, 65, 80, 95, 30];

let topScorers = marks
  .filter(m => m >= 60)
  .sort((a, b) => b - a)
  .map(m => "Score: " + m);

console.log(topScorers);
// ["Score: 95", "Score: 80", "Score: 65"]
```

✅ This is called **method chaining** and is used heavily in real-world coding!

---

## 👨‍💻 Mini Project: Top Products Dashboard

### ✅ Data:

```js
let products = [
  { name: "Laptop", price: 1200 },
  { name: "Phone", price: 800 },
  { name: "Tablet", price: 400 },
  { name: "Mouse", price: 20 },
  { name: "Keyboard", price: 50 }
];
```

### 🔹 1. Check if Any Product is Under 100

```js
let cheapExists = products.some(p => p.price < 100);
console.log(cheapExists); // true
```

### 🔹 2. Check if All Products Are Affordable (under 1500)

```js
let allAffordable = products.every(p => p.price < 1500);
console.log(allAffordable); // true
```

### 🔹 3. Sort Products by Price (Low to High)

```js
let sorted = products.sort((a, b) => a.price - b.price);
console.log(sorted);
```

### 🔹 4. Create Sorted Names List in Uppercase

```js
let sortedNames = products
  .sort((a, b) => a.price - b.price)
  .map(p => p.name.toUpperCase());

console.log(sortedNames);
```

---

## 🛠 Practice Exercises

1. Check if any user is under 18 using `some()`
2. Check if all passwords are 8+ characters using `every()`
3. Sort a list of expenses from high to low
4. Use `includes()` to check for a banned word in a comment
5. Chain `filter + map + sort` for a list of student scores

---

## 🔥 Real-World Use Cases

| Scenario                                | Method(s) Used     |
| --------------------------------------- | ------------------ |
| Chat messages in reverse order          | `reverse()`        |
| Check if someone failed a test          | `some()`           |
| Validate all users have verified emails | `every()`          |
| Show top 3 trending items               | `sort() + slice()` |
| Detect banned words in comments         | `includes()`       |

---

## 🎓 Homework Challenge

**Create a To-Do App Analyzer:**

```js
let todos = [
  { task: "HTML Practice", completed: true },
  { task: "CSS Practice", completed: false },
  { task: "JavaScript Project", completed: false }
];
```

👉 What to build:

1. Show number of completed and pending tasks
2. Check if any task is incomplete
3. Check if all tasks are completed
4. Sort tasks by status
5. Create a summary using chaining




## 📋 Common & Useful Array Methods

| Method        | Description                               | Example                      |
| ------------- | ----------------------------------------- | ---------------------------- |
| `.push()`     | Adds item to end                          | `arr.push("item")`           |
| `.pop()`      | Removes last item                         | `arr.pop()`                  |
| `.unshift()`  | Adds item to start                        | `arr.unshift("first")`       |
| `.shift()`    | Removes first item                        | `arr.shift()`                |
| `.length`     | Counts total items                        | `arr.length`                 |
| `.indexOf()`  | Finds index of an item                    | `arr.indexOf("Ali")`         |
| `.includes()` | Checks if item exists                     | `arr.includes("JavaScript")` |
| `.splice()`   | Removes/Replace items at specific index   | `arr.splice(1, 2)`           |
| `.join()`     | Converts array to a string with separator | `arr.join(", ")`             |

---

## 📦 Code Examples

### 🔹 `.push()` and `.pop()`

```js
let fruits = ["Apple", "Banana"];
fruits.push("Mango"); // ["Apple", "Banana", "Mango"]
fruits.pop();          // ["Apple", "Banana"]
```

### 🔹 `.splice()`

```js
let tasks = ["HTML", "CSS", "JS"];
tasks.splice(1, 1); // Removes "CSS"
console.log(tasks); // ["HTML", "JS"]
```

---

## 🔥 Project 1: Random Name Picker App

Let’s say you have a list of students — pick one randomly!

### 🧠 Logic:

* Store names in an array
* Use `Math.random()` to select a name

### ✅ Code:

```js
let students = ["Ali", "Ayesha", "Zara", "Usman", "Bilal"];
let randomIndex = Math.floor(Math.random() * students.length);
let winner = students[randomIndex];

console.log("🎉 Selected Student: " + winner);
```

> 💬 Urdu Tip: `Math.random()` ek number deta hai 0 aur 1 ke beech, jisse hum array ka index nikalte hain.

---

## 🔥 Project 2: To-Do List with Remove Feature

### 🧠 Features:

* Add task with `.push()`
* Show all tasks using loop
* Remove specific task with `.splice()`

### ✅ Code:

```js
let todoList = [];

let taskCount = prompt("How many tasks do you want to add?");
for (let i = 0; i < taskCount; i++) {
  let task = prompt("Enter task " + (i + 1));
  todoList.push(task);
}

console.log("📝 Your Tasks:");
for (let i = 0; i < todoList.length; i++) {
  console.log(i + ": " + todoList[i]);
}

let removeIndex = prompt("Enter the index of task you want to remove:");
todoList.splice(removeIndex, 1);

console.log("✅ Updated Tasks:");
for (let i = 0; i < todoList.length; i++) {
  console.log(i + ": " + todoList[i]);
}
```

---

## 💡 Tips to Teach Students

* Compare `.push()` with adding items to a shopping cart
* Visualize `.splice()` as removing an item from a plate
* Show how `.join()` turns arrays into readable messages

---

## 🧠 Student Practice

### ✅ Tasks:

1. Create a list of your 5 favorite foods and remove the 3rd item
2. Create a movie list and check if "Avengers" exists using `.includes()`
3. Ask a user to add names of their 3 friends and display them using `.join(", ")`

---

## ❌ Common Mistakes

| Mistake                        | Fix                                          |
| ------------------------------ | -------------------------------------------- |
| Forgetting `()` in methods     | Always use like `.push("item")` not `.push`  |
| Wrong index in `.splice()`     | Remember index starts from 0                 |
| Overwriting array accidentally | Use `.push()` to add instead of re-assigning |

---


## 🏡 Homework

**Build a Contact Book Manager**

1. Ask user how many contacts to add
2. Take name inputs, store in an array
3. Allow user to remove a contact by name (use `.indexOf()` + `.splice()`)
4. Show updated contact list

**(Mini Project: Daily Planner App)**



## 🧪 Try This: Print Your Daily Routine

```js
let dayTasks = ["Wake Up", "Pray", "Study", "Practice Coding", "Sleep"];

for (let i = 0; i < dayTasks.length; i++) {
  console.log("✅ " + dayTasks[i]);
}
```

---

## 🔥 Project: Daily Planner App 🗓️

### Goal:

Let the user add multiple tasks, store them in an array, and then display all tasks with numbering.

---

### 🔧 Step-by-Step Example:

```js
let numberOfTasks = prompt("How many tasks do you want to add?");
numberOfTasks = Number(numberOfTasks);

let tasks = [];

for (let i = 0; i < numberOfTasks; i++) {
  let task = prompt("Enter Task " + (i + 1));
  tasks.push(task);
}

document.write("<h2>📋 Your Daily Planner:</h2>");

for (let i = 0; i < tasks.length; i++) {
  document.write((i + 1) + ". " + tasks[i] + "<br>");
}
```

---

### 🛠 Breakdown:

| Step               | What it does                    |
| ------------------ | ------------------------------- |
| `prompt()`         | Takes number of tasks from user |
| `tasks.push(task)` | Adds task to the array          |
| `for loop`         | Prints each task with numbering |

---
* Array ka matlab: ek box mein kai cheezein
* For loop ka matlab: repeat karna jab tak condition true ho
* Daily Planner App: har din ke kaam list karna

---

## 🧠 Practice Task for Students

Create your own planner for:

1. **Weekly Planner** → 7 Days + Tasks
2. Ask user for name, show greeting + their tasks
3. Use different array methods: `.push()`, `.pop()`, `.length`

---

## 🔎 Bonus: `while` Loop Example

```js
let i = 0;
while (i < 3) {
  console.log("Loop run: " + i);
  i++;
}
```

---

## ❌ Common Mistakes

| Mistake                               | Fix                                    |
| ------------------------------------- | -------------------------------------- |
| Accessing wrong index                 | Arrays start from index `0`            |
| Using `length()` instead of `.length` | It's a property, not a function        |
| Forgetting to increment `i++`         | Loop will run forever (infinite loop!) |





## 🚀 Project 1: Guest List App

Let’s build a simple **Guest List App**.

### 🧩 Code:

```js
let guests = [];

let name1 = prompt("Enter first guest name:");
guests.push(name1);

let name2 = prompt("Enter second guest name:");
guests.push(name2);

let name3 = prompt("Enter third guest name:");
guests.push(name3);

console.log("Guest List:");
for (let i = 0; i < guests.length; i++) {
  console.log((i + 1) + ". " + guests[i]);
}
```

> ✅ Try it on [Replit](https://replit.com/) or [PlayCode.io](https://playcode.io/)

---

## 🚀 Project 2: Basic To-Do List

```js
let todos = [];

let task1 = prompt("Enter your first task:");
todos.push(task1);

let task2 = prompt("Enter your second task:");
todos.push(task2);

console.log("Your To-Do List:");
for (let i = 0; i < todos.length; i++) {
  console.log((i + 1) + ". " + todos[i]);
}
```

---

## 🧪 Practice Task for Students

### 📝 Create a Shopping List App

1. Ask the user to enter 3 shopping items using `prompt()`
2. Push all items into an array
3. Display the full list using `document.write()` and `console.log()`

---

## 💡 Bonus: Dynamic Input with Loop

Instead of repeating prompts, use a loop:

```js
let items = [];
for (let i = 0; i < 5; i++) {
  let item = prompt("Enter item " + (i + 1) + ":");
  items.push(item);
}

console.log("You added: " + items.join(", "));
```

---

## ❌ Common Mistakes

| Mistake                       | Issue                                  |
| ----------------------------- | -------------------------------------- |
| Accessing wrong index         | `array[5]` when array has only 3 items |
| Forgetting `.length` in loop  | May cause infinite loop                |
| Typing `array.push = "value"` | Use `push("value")`, not assignment    |


---

## 🏡 Homework

✅ Create an app that:

1. Asks user for 5 favorite YouTubers
2. Stores them in an array
3. Shows the complete list using `console.log()` and `document.write()`
4. Bonus: Let user remove 1 item using `.pop()`



**(Creation, Accessing, Updating, Looping, and Powerful Built-in Methods)**



## 🔥 Project 1: Random Name Picker App

Let’s say you have a list of students — pick one randomly!

### 🧠 Logic:

* Store names in an array
* Use `Math.random()` to select a name

### ✅ Code:

```js
let students = ["Ali", "Ayesha", "Zara", "Usman", "Bilal"];
let randomIndex = Math.floor(Math.random() * students.length);
let winner = students[randomIndex];

console.log("🎉 Selected Student: " + winner);
```

> 💬 Urdu Tip: `Math.random()` ek number deta hai 0 aur 1 ke beech, jisse hum array ka index nikalte hain.

---

## 🔥 Project 2: To-Do List with Remove Feature

### 🧠 Features:

* Add task with `.push()`
* Show all tasks using loop
* Remove specific task with `.splice()`

### ✅ Code:

```js
let todoList = [];

let taskCount = prompt("How many tasks do you want to add?");
for (let i = 0; i < taskCount; i++) {
  let task = prompt("Enter task " + (i + 1));
  todoList.push(task);
}

console.log("📝 Your Tasks:");
for (let i = 0; i < todoList.length; i++) {
  console.log(i + ": " + todoList[i]);
}

let removeIndex = prompt("Enter the index of task you want to remove:");
todoList.splice(removeIndex, 1);

console.log("✅ Updated Tasks:");
for (let i = 0; i < todoList.length; i++) {
  console.log(i + ": " + todoList[i]);
}
```


---

## 🔁 5. Looping Through Arrays

### 🔹 For Loop:

```js
for (let i = 0; i < cities.length; i++) {
  console.log(cities[i]);
}
```

### 🔹 For...of Loop (Simpler):

```js
for (let city of cities) {
  console.log(city);
}
```

---

## 🛠 6. Array Built-in Methods

| Method       | Description                         | Example                 |
| ------------ | ----------------------------------- | ----------------------- |
| `push()`     | Add item to **end**                 | `arr.push("item")`      |
| `pop()`      | Remove last item                    | `arr.pop()`             |
| `unshift()`  | Add item to **start**               | `arr.unshift("item")`   |
| `shift()`    | Remove first item                   | `arr.shift()`           |
| `slice()`    | Extract a portion (non-destructive) | `arr.slice(1, 3)`       |
| `splice()`   | Remove/add items (destructive)      | `arr.splice(2, 1)`      |
| `indexOf()`  | Find index of a value               | `arr.indexOf("banana")` |
| `includes()` | Check if item exists                | `arr.includes("apple")` |

---

## ⚡ 7. Modern Array Methods (ES6+)

### ✅ `map()`

Returns a **new array** after applying a function to each element.

```js
let nums = [1, 2, 3];
let doubled = nums.map(n => n * 2); // [2, 4, 6]
```

### ✅ `filter()`

Returns a **new array** of elements that pass a condition.

```js
let ages = [15, 22, 18, 30];
let adults = ages.filter(age => age >= 18); // [22, 18, 30]
```

### ✅ `forEach()`

Executes a function for each element — used for **side effects**.

```js
let items = ["pen", "pencil", "eraser"];
items.forEach(item => console.log(item.toUpperCase()));
```

---

## 💡 Real-World Examples

### 📌 1. Student Marks and Results

```js
let marks = [80, 90, 65, 70];
let total = 0;

for (let mark of marks) {
  total += mark;
}

console.log("Total:", total);
console.log("Average:", total / marks.length);
```

### 📌 2. Filter Even Numbers

```js
let numbers = [1, 2, 3, 4, 5, 6];
let even = numbers.filter(num => num % 2 === 0);
console.log(even); // [2, 4, 6]
```

### 📌 3. Shopping Cart Total

```js
let prices = [200, 150, 50];
let total = prices.reduce((sum, price) => sum + price, 0);
console.log("Cart Total:", total);
```

---

## 🎯 Mini Project Ideas

1. **To-Do List App** using an array of strings
2. **Number Guessing Game** — track guesses in an array
3. **Contact List Manager** — add, remove, and search names

---

## 💻 Practice in Online Editors

* [Replit](https://replit.com/)
* [JSFiddle](https://jsfiddle.net/)
* [PlayCode.io](https://playcode.io/)


---

## 🧠 Homework / Practice

1. Create an array of your 5 favorite movies and print each
2. Write a program that filters out all numbers above 50
3. Make a list of items, then remove the first and last
4. Build a small grocery list and use `map()` to add prices


