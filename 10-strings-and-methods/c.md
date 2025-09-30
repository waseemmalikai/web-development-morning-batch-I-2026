# 📘 Chapter 10: Strings & Useful Methods in JavaScript

Strings are one of the most **fundamental data types** in JavaScript. They allow us to work with text — from user input to web content, filenames, URLs, and more.

In this chapter, we’ll explore **everything about strings**, their properties, and the most useful methods to manipulate them effectively.

---

## 🔹 1. What is a String?

A **string** is a sequence of characters enclosed in:

* Single quotes `'...'`
* Double quotes `"..."`
* Backticks `` `...` `` (template literals)

```js
let str1 = "Hello";
let str2 = 'World';
let str3 = `Hello, ${str1}!`; // Template literal with interpolation
```

---

## 🔹 2. String Basics

### 📏 Length of a String

Every string has a `.length` property.

```js
let name = "JavaScript";
console.log(name.length); // 10
```

### 🎯 Accessing Characters

You can access characters using **indexing** (like arrays).

```js
let word = "Hello";
console.log(word[0]); // 'H'
console.log(word.charAt(1)); // 'e'
console.log(word.at(-1)); // 'o' (ES2022)
```

### 🚫 Strings are Immutable

You **cannot** change characters directly.

```js
let text = "Hi";
text[0] = "M"; 
console.log(text); // "Hi" (unchanged)
```

---

## 🔹 3. Creating Strings with Special Characters

```js
let str = "Line1\nLine2";  // newline
let quote = "He said: \"JavaScript is fun!\"";
let backslash = "This is a backslash: \\";
```

| Escape Sequence | Meaning   |
| --------------- | --------- |
| `\n`            | New line  |
| `\t`            | Tab       |
| `\\`            | Backslash |
| `\"` / `\'`     | Quotes    |

---

## 🔹 4. Useful String Methods

### 📌 A. Basic Methods

```js
let str = "   JavaScript is Awesome!   ";

// Case conversion
console.log(str.toUpperCase()); // JAVASCRIPT IS AWESOME!
console.log(str.toLowerCase()); // javascript is awesome!

// Trimming whitespace
console.log(str.trim());      // "JavaScript is Awesome!"
console.log(str.trimStart()); // "JavaScript is Awesome!   "
console.log(str.trimEnd());   // "   JavaScript is Awesome!"

// Searching
console.log(str.includes("Script")); // true
console.log(str.startsWith("Java")); // true
console.log(str.endsWith("!"));      // true

// Finding index
console.log(str.indexOf("is"));      // 14
console.log(str.lastIndexOf("a"));   // 19
```

---

### 📌 B. Extracting & Slicing

```js
let phrase = "Learning JavaScript";

// slice(start, end)
console.log(phrase.slice(0, 8));  // "Learning"
console.log(phrase.slice(-10));   // "JavaScript"

// substring(start, end)
console.log(phrase.substring(0, 8)); // "Learning"

// Difference: substring() swaps negative/greater indexes to 0
console.log(phrase.substring(-3, 5)); // "Learn"
```

---

### 📌 C. Modifying & Splitting

```js
let sentence = "I love JavaScript";

// replace
console.log(sentence.replace("love", "enjoy")); // "I enjoy JavaScript"

// replaceAll
console.log("apple, apple".replaceAll("apple", "orange")); // "orange, orange"

// split
console.log(sentence.split(" ")); // ["I", "love", "JavaScript"]

// concat
let str1 = "Hello";
let str2 = "World";
console.log(str1.concat(" ", str2)); // "Hello World"

// repeat
console.log("Ha!".repeat(3)); // "Ha!Ha!Ha!"
```

---

### 📌 D. Padding

```js
let num = "5";
console.log(num.padStart(3, "0")); // "005"
console.log(num.padEnd(5, "."));   // "5...."
```

---

### 📌 E. Advanced Methods

```js
let text = "Hello World!";

// charAt / charCodeAt
console.log(text.charAt(0));    // 'H'
console.log(text.charCodeAt(0)); // 72

// codePointAt (handles emojis too)
let emoji = "😀";
console.log(emoji.codePointAt(0)); // 128512

// fromCharCode / fromCodePoint
console.log(String.fromCharCode(65));     // "A"
console.log(String.fromCodePoint(128512)); // "😀"

// match & search (regex)
let msg = "Hello Hello World";
console.log(msg.match(/Hello/g)); // ["Hello", "Hello"]
console.log(msg.search(/World/)); // 12

// localeCompare
console.log("apple".localeCompare("banana")); // -1
```

---

## 🔹 5. Comparing Strings

```js
console.log("a" > "Z"); // true (lowercase > uppercase in Unicode)
console.log("2" > "12"); // true ("2" comes after "1")
```

👉 To compare strings properly for locale/language:

```js
console.log("Österreich".localeCompare("Zealand")); // -1, 0, or 1
```

---

## 🔹 6. Template Literals (Backticks)

```js
let name = "Waseem";
let age = 25;

console.log(`Hello, my name is ${name} and I am ${age} years old.`);

// Multi-line
let poem = `Roses are red
Violets are blue
JavaScript is awesome
And so are you!`;
```

---

## 🎯 7. Practice Tasks

1. **Word Capitalizer**
   Write a function that capitalizes the first letter of every word in a sentence.

2. **Spam Checker**
   Check if a string contains banned words like "free", "offer", "buy now".

3. **Truncate Text**
   Write a function that shortens text to a certain length and adds `...`.

4. **Extract Currency**
   From the string `"$120"`, extract the number `120`.

5. **Palindrome Checker**
   Check if a word reads the same backward and forward.

---

## 🚀 8. Mini Projects

1. **Username Formatter**

   * Input: `"   Waseem Malik   "`
   * Output: `"waseem_malik"`

2. **Word Frequency Counter**
   Count how many times each word appears in a sentence.
   → Uses `split`, `toLowerCase`, `trim`.

3. **Password Strength Checker**

   * Must include uppercase, lowercase, number, and special character.
   * Uses regex + string methods.

---

## ✅ Summary

* Strings are immutable sequences of characters.
* Use `.length` to check size, and `[index]` / `.at()` to access chars.
* Core methods: `trim`, `toUpperCase`, `slice`, `split`, `replace`, `includes`, `startsWith`, `endsWith`.
* Advanced methods: regex (`match`, `search`), Unicode (`codePointAt`, `fromCodePoint`).
* Template literals make string building easy.
* Real-world projects help apply string methods effectively.

Strings are everywhere in programming — **master them and you’ll unlock powerful text manipulation skills** for any project.
