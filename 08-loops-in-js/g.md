Welcome to the **Loops in JavaScript** chapter\! 🔁

As a developer and your guide, my goal is to help you master one of the most fundamental concepts in programming: repeating actions. Loops are your superpower for automating repetitive tasks, saving you from writing the same code over and over again.

Imagine you have a list of names and you need to print each one. Without a loop, you'd have to write `console.log()` for every single name. What if you have a thousand names? That's where loops come in. They let you write a single block of code that runs repeatedly, handling any number of items with ease.

Let's dive in\!

-----

## 1\. The Big Three: Standard JavaScript Loops

These three loops are the building blocks of repetitive tasks. They offer different ways to control when a loop starts and stops.

### **The `for` Loop: The "Known Quantity" Loop**

This is the most common loop. Use it when you know exactly how many times you want the code to run. Think of it as telling a friend to "take **exactly** 5 steps."

A `for` loop has three key parts, separated by semicolons, inside its parentheses:

```javascript
for (initialization; condition; afterthought) {
  // code to be executed
}
```

  * **`initialization`**: This runs only **once** at the very beginning. It's usually where you create a counter variable (e.g., `let i = 0`).
  * **`condition`**: This is checked **before every iteration**. If it's `true`, the loop continues. If `false`, the loop stops.
  * **`afterthought`**: This runs **after every iteration**. It's typically used to increment or decrement your counter (e.g., `i++`).

**Example: Counting from 0 to 4**

```javascript
for (let i = 0; i < 5; i++) {
  console.log("Step:", i);
}

// Output:
// Step: 0
// Step: 1
// Step: 2
// Step: 3
// Step: 4
```

### **The `while` Loop: The "Conditional" Loop**

This loop runs as long as a specified condition is `true`. Use it when you don't know exactly how many times the loop will run, but you have a condition that will eventually become `false`. Think of it as "keep going **while** the light is green."

The `while` loop syntax is simpler:

```javascript
while (condition) {
  // code to be executed
}
```

**Example: Doubling a number until it's over 100**

```javascript
let number = 5;

while (number < 100) {
  console.log(number);
  number *= 2; // shorthand for number = number * 2
}

// Output:
// 5
// 10
// 20
// 40
// 80
```

Notice how we don't know in advance that the loop will run five times. It just keeps going until the condition `number < 100` is no longer met.

### **The `do...while` Loop: The "At Least Once" Loop**

This loop is a variation of the `while` loop. The key difference is that the code block is executed **at least once** before the condition is even checked.

```javascript
do {
  // code to be executed
} while (condition);
```

**Example: A number that starts greater than 100**

In this example, the code will run once, even though the condition is immediately `false`.

```javascript
let i = 150;

do {
  console.log("This will run at least once:", i);
  i++;
} while (i < 100);

// Output:
// This will run at least once: 150
```

-----

## 2\. Modern Iteration: `for...of` and `for...in`

These loops are designed for working with data collections like arrays and objects.

### **The `for...of` Loop: The "Iterate Over Values" Loop**

This is the **most common and preferred way** to loop through arrays and other **iterable** objects (like strings, `Maps`, and `Sets`). It's clean, simple, and safe.

Think of it as "for **each item of** this list, do something."

```javascript
for (variable of iterable) {
  // code
}
```

**Example: Looping through an array**

```javascript
const fruits = ["apple", "banana", "cherry"];

for (const fruit of fruits) {
  console.log(fruit);
}

// Output:
// apple
// banana
// cherry
```

### **The `for...in` Loop: The "Iterate Over Keys" Loop**

This loop is specifically for iterating over the **enumerable properties (keys)** of an object. **Do not use it for arrays\!**

Think of it as "for **each key in** this object, do something."

```javascript
for (key in object) {
  // code
}
```

**Example: Looping through an object's properties**

```javascript
const person = {
  name: "Alice",
  age: 30,
  city: "New York"
};

for (const key in person) {
  console.log(`${key}: ${person[key]}`);
}

// Output:
// name: Alice
// age: 30
// city: New York
```

**Why NOT to use `for...in` for arrays:** It can loop over unexpected properties or in an unpredictable order, especially if the `Array` prototype has been modified. Using `for...of` is the standard, reliable approach for arrays.

-----

## 3\. Loop Control: `break` and `continue`

Sometimes you need more control over your loops. These two keywords let you modify their default behavior.

### **`break`: The "Emergency Exit"** 🛑

The `break` statement immediately and permanently exits the current loop, regardless of its condition.

**Example: Finding a specific number**

```javascript
const numbers = [10, 20, 30, 40, 50];

for (const number of numbers) {
  if (number === 40) {
    console.log("Found it! Breaking the loop.");
    break;
  }
  console.log("Current number:", number);
}

// Output:
// Current number: 10
// Current number: 20
// Current number: 30
// Found it! Breaking the loop.
```

### **`continue`: The "Skip This One"** ➡️

The `continue` statement skips the rest of the current iteration and jumps to the next one.

**Example: Skipping odd numbers**

```javascript
for (let i = 0; i < 5; i++) {
  if (i % 2 !== 0) { // If the number is odd...
    console.log("Skipping odd number:", i);
    continue; // ...skip the rest of this iteration
  }
  console.log("Processing even number:", i);
}

// Output:
// Processing even number: 0
// Skipping odd number: 1
// Processing even number: 2
// Skipping odd number: 3
// Processing even number: 4
```

-----

## 4\. Common Pitfalls and Best Practices

### **The Off-by-One Error**

A common mistake with `for` loops is setting the wrong condition, which can lead to errors. An array with 5 elements has indexes from 0 to 4. Using `<= 5` would try to access a non-existent index `5`.

**Correct way:**

```javascript
const myArray = [1, 2, 3, 4, 5];
for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}
```

**Incorrect way (accessing an undefined value):**

```javascript
const myArray = [1, 2, 3, 4, 5];
for (let i = 0; i <= myArray.length; i++) {
  console.log(myArray[i]); // The last log will be 'undefined'
}
```

### **Infinite Loops**

An **infinite loop** is a loop that never stops because its condition never becomes `false`. This can crash your program or browser.

**Example of an infinite loop:**

```javascript
let i = 0;
while (i < 5) {
  // No incrementer! 'i' is always 0, so the loop runs forever.
  console.log(i);
}
```

### **Using `while(true)` with `break`**

This is a powerful and common pattern for building loops where the exit condition is complex or checked in the middle of the loop.

**Example: Repeating a prompt until the user provides valid input**

```javascript
let number;

while (true) {
  number = prompt("Enter a number greater than 100:");
  
  if (number > 100 || number === null || number === "") {
    break; // Exit the loop if the input is valid or cancelled
  }
}
```

This loop will keep asking for a number until the user provides a number greater than 100 or cancels the prompt.