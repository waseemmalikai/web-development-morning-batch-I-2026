# ✅ Chapter 11: JavaScript Arrays — Part 1

📁 **Project-Based Learning:** Build a Console-Based **To-Do List App**

---

## 🧠 What is an Array?

An **array** is a container that stores **multiple values** in a **single variable**.

> 🧺 "Array aik dabba hota hai jismein aap bohat si cheezein aik saath rakh saktay hain!"

### 💡 Real-World Example:

Without an array:

```js
let task1 = "Buy milk";
let task2 = "Do homework";
let task3 = "Call friend";
```

With an array:

```js
let tasks = ["Buy milk", "Do homework", "Call friend"];
```

✅ Easier to **store**, **loop**, and **manage**.

---

## 🏗️ How to Create an Array

```js
let fruits = ["Apple", "Mango", "Banana"];
```

Arrays can store:

* Strings: `["Ali", "Sara"]`
* Numbers: `[10, 20, 30]`
* Booleans: `[true, false]`
* Mixed Types: `["Ali", 21, true]`

---

## 🔍 Accessing Items in an Array

```js
console.log(fruits[0]); // Apple
console.log(fruits[2]); // Banana
```

> 📌 Arrays are **zero-indexed** — the first item is at position `0`.

---

## ✏️ Modifying Array Elements

```js
fruits[1] = "Orange";
console.log(fruits); // ["Apple", "Orange", "Banana"]
```

---

## ➕ Add or Remove Items from Array

| Action            | Code                     | Result                   |
| ----------------- | ------------------------ | ------------------------ |
| Add to end        | `array.push("item")`     | Adds item at end         |
| Remove from end   | `array.pop()`            | Removes last item        |
| Add to start      | `array.unshift("item")`  | Adds item at beginning   |
| Remove from start | `array.shift()`          | Removes first item       |
| Remove at index   | `array.splice(index, 1)` | Removes item at position |

### 🔧 Example:

```js
let fruits = ["Apple", "Banana"];

fruits.push("Mango");
fruits.pop();
fruits.unshift("Lemon");
fruits.shift();

console.log(fruits); // ["Banana"]
```

---

## 📏 Get Array Length

```js
console.log(fruits.length); // Total number of items
```

---

## 🔁 Looping Through Arrays

```js
let tasks = ["Eat", "Sleep", "Code"];

for (let i = 0; i < tasks.length; i++) {
  console.log(tasks[i]);
}
```

---

## 🚀 Mini Project: Console-Based To-Do List App

We'll build a simple app using arrays:

### ✅ Features:

1. View all tasks
2. Add new task
3. Delete task
4. Repeat until user exits

---

### 💻 Code Template:

```js
let todos = [];

while (true) {
  let action = prompt("Choose: view | add | delete | exit");

  if (action === "view") {
    console.log("📝 Your To-Do List:");
    for (let i = 0; i < todos.length; i++) {
      console.log(`${i + 1}: ${todos[i]}`);
    }

  } else if (action === "add") {
    let newTask = prompt("Enter new task:");
    todos.push(newTask);
    alert("✅ Task added!");

  } else if (action === "delete") {
    let index = prompt("Enter task number to delete:");
    todos.splice(index - 1, 1);
    alert("❌ Task deleted!");

  } else if (action === "exit") {
    alert("👋 Goodbye!");
    break;

  } else {
    alert("Invalid command. Try again.");
  }
}
```

---

### 🔎 Sample Output:

```
Choose: view | add | delete | exit  
→ add  
Enter your new task: Buy milk  
✅ Task added!

Choose: view  
1: Buy milk  

Choose: delete  
Enter the task number to delete: 1  
❌ Task deleted!
```

---

## 🧠 Summary of Important Methods

| Method         | What it Does             |
| -------------- | ------------------------ |
| `.push()`      | Add item to end          |
| `.pop()`       | Remove item from end     |
| `.unshift()`   | Add item at beginning    |
| `.shift()`     | Remove item from start   |
| `.splice(i,1)` | Remove item at index `i` |
| `.length`      | Get number of items      |

---

## 📚 Q\&A Time

> ❓ **Can arrays store different data types?**
> ✅ Yes: `["Ali", 30, true]`

> ❓ **What if I delete from an empty array?**
> ✅ It won’t crash. It just does nothing.

> ❓ **Can I use `prompt()` in a loop?**
> ✅ Yes, it’s a great way to make interactive console apps!

---

## 🧠 Homework / Practice Challenges

### ✅ 1. **Favorite Movies App**

* Ask user to input 5 favorite movies
* Store them in an array
* Print all with their index (1, 2, 3…)

---

### ✅ 2. **Marks Analyzer**

* Ask user for 3 subject marks
* Store in array
* Calculate and print total and average

---

### ✅ 3. **Simple Shopping Cart**

* Let the user:

  * Add item
  * Delete item
  * View cart
* Store all items in an array
