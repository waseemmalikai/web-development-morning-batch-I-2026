# Chapter 10: Strings: The Immutable Textual Data Structure & Essential Methods 📝

Strings are a **fundamental data type** in JavaScript, representing ordered **sequences of characters**. They form the basis for handling all textual information in web development, from simple user names to complex JSON data.

## 1\. String Creation and Syntax

Strings can be created using three primary methods in JavaScript:

| Quote Type | Character | Key Features | Primary Use Case |
| :--- | :--- | :--- | :--- |
| **Single/Double Quotes** | `' '` or `" "` | The standard way to define a string. They are interchangeable. Requires **escaping** (`\`) to include the same quote type inside. | Simple, single-line text and string literals. |
| **Template Literals** (ES6+) | `` ` ` `` | Defined using **backticks**. Allows **multiline strings** and **expression interpolation** via `${...}`. | Dynamic content, HTML templates, and complex formatting. |

### Expression Interpolation

Template literals simplify combining variables and strings, replacing the cumbersome concatenation operator (`+`) and the explicit **`str.concat()`** method.

```javascript
const name = 'Alex';
const count = 3;

// Concatenation: 'Hello, Alex. You have 3 items.'
const oldMsg = 'Hello, ' + name + '. You have ' + count + ' items.';

// Interpolation: 'Hello, Alex. You have 3 items.'
const newMsg = `Hello, ${name}. You have ${count} items.`; 
```

### ⚠️ Note on the `String` Constructor

Using `new String('text')` creates a **String Object** instead of a primitive **String value**. This is highly discouraged as objects behave differently in comparisons, often leading to unexpected results (e.g., `'hello' === new String('hello')` returns `false`).

-----

## 2\. The Core Concept: Immutability 🧱

The most important concept for strings is **immutability**.

> **Immutability:** Once a string is created, its sequence of characters in memory **cannot be changed**.

  * Every method or operation that appears to "modify" a string (e.g., `toUpperCase()`, `replace()`, or combining strings with `+`) returns a **brand new string**.
  * The original string remains in memory, unmodified. If you want to keep the change, you must reassign the variable: `myStr = myStr.toUpperCase();`.

<!-- end list -->

```javascript
let original = "world";

// This attempts to change the first character but fails silently.
original[0] = "W"; 
console.log(original); // Output: "world" (Original is unchanged)

// This creates a NEW string "Hello world" and reassigns the variable.
let newString = "Hello " + original;
console.log(newString); // Output: "Hello world" 
```

-----

## 3\. Accessing and Handling Characters (Unicode)

JavaScript uses **UTF-16** encoding, which impacts how characters are accessed, especially those outside the Basic Multilingual Plane (like emojis).

| Method/Property | Purpose | Returns | Notes |
| :--- | :--- | :--- | :--- |
| **`str.length`** | The number of characters/code units in the string. (Property) | `Number` | Counts surrogate pairs as two characters. |
| **`str[index]`** | Accesses the character at a zero-based index. (Preferred) | `String` | Works like an array access. |
| **`str.at(index)`** | Accesses a character. **Supports negative indices** (counting from the end). | `String` | Modern equivalent to array access. |
| **`str.charAt(index)`** | Returns the character at a specific index (Legacy). | `String` | |
| **`str.charCodeAt(index)`** | Returns the **16-bit code unit** at the index (ASCII value for basic characters). | `Number` | **Will only return half** of the code for emojis (surrogate pair). |
| **`str.codePointAt(index)`** | Returns the full **Unicode code point** at the index, handling multi-unit characters correctly. | `Number` | **Recommended** for correct Unicode handling (e.g., emojis). |
| **`String.fromCharCode(...)`** | Creates a string from a sequence of **16-bit code units**. | `String` | Legacy method for basic character creation. |

-----

## 4\. Searching and Checking Substrings

These methods are essential for finding content within a string. All are **case-sensitive**.

| Method | Purpose | Returns | Notes |
| :--- | :--- | :--- | :--- |
| **`str.indexOf(sub, pos)`** | Finds the **first** index of a substring. | Index position (`0` or greater), or **`-1`** if not found. | |
| **`str.lastIndexOf(sub, pos)`** | Finds the **last** index of a substring. | Index position, or `-1`. | Searches backward from the end. |
| **`str.includes(sub, pos)`** | Checks for the **presence** of a substring. | `true` or `false`. | Simpler for existence checks than `indexOf()`. |
| **`str.startsWith(sub, pos)`** | Checks if the string begins with the substring (optional start position). | `true` or `false`. | |
| **`str.endsWith(sub, len)`** | Checks if the string ends with the substring (optional check length). | `true` or `false`. | |
| **`str.search(regexp)`** | Finds the **index** of the **first match** using a **Regular Expression**. | Index position, or `-1`. | The only search method that requires a RegExp object. |

-----

## 5\. Substring Extraction Methods

These methods return a **new string** containing the extracted portion.

| Method | Syntax | Key Difference | Example |
| :--- | :--- | :--- | :--- |
| **`str.slice(start, end)`** | `str.slice(-6, -1)` | **Supports negative indices** (counts from the end). | `'JavaScript'.slice(-6)` $\rightarrow$ `'Script'` |
| **`str.substring(start, end)`** | `str.substring(4, 1)` | **Does NOT support negative indices** (treats them as 0). Swaps `start`/`end` if `start > end`. | `'JavaScript'.substring(4, 1)` $\rightarrow$ `'ava'` |

-----

## 6\. Transformation and Formatting

### Case and Whitespace Manipulation

| Method | Purpose | Example |
| :--- | :--- | :--- |
| **`str.toLowerCase()`** | Converts the string to all lowercase. | `'TEXT'.toLowerCase()` $\rightarrow$ `'text'` |
| **`str.toUpperCase()`** | Converts the string to all uppercase. | `'text'.toUpperCase()` $\rightarrow$ `'TEXT'` |
| **`str.trim()`** | Removes whitespace (spaces, tabs, newlines) from **both ends**. | `'  text  '.trim()` $\rightarrow$ `'text'` |
| **`str.trimStart()`** | Removes whitespace from the **beginning** only. | `'  text  '.trimStart()` $\rightarrow$ `'text  '` |
| **`str.trimEnd()`** | Removes whitespace from the **end** only. | `'  text  '.trimEnd()` $\rightarrow$ `'  text'` |

### Padding and Repetition

| Method | Purpose | Example |
| :--- | :--- | :--- |
| **`str.repeat(n)`** | Returns a new string repeated $n$ times. | `'ha'.repeat(3)` $\rightarrow$ `'hahaha'` |
| **`str.padStart(len, char)`** | Pads the **start (left)** of the string until it reaches $len$ length. | `'5'.padStart(3, '0')` $\rightarrow$ `'005'` |
| **`str.padEnd(len, char)`** | Pads the **end (right)** of the string until it reaches $len$ length. | `'John'.padEnd(10, '.')` $\rightarrow$ `'John......'` |

-----

## 7\. Advanced Manipulation: Replacement and Arrays

### Replacement Methods

| Method | Purpose | Notes | Example |
| :--- | :--- | :--- | :--- |
| **`str.replace(val, new)`** | Replaces the **first** occurrence of `val`. | `val` can be a string or a **Regular Expression**. | `'dog, dog'.replace('dog', 'cat')` $\rightarrow$ `'cat, dog'` |
| **`str.replaceAll(val, new)`** | Replaces **all** occurrences of `val`. | `val` can be a string or a **Regular Expression**. (ES2021+) | `'dog, dog'.replaceAll('dog', 'cat')` $\rightarrow$ `'cat, cat'` |
| **`str.match(regexp)`** | Retrieves all matches of a **Regular Expression**. | Returns an **Array** of matches (or `null`). Requires the global flag (`/g`) to find all occurrences. | `'A B A'.match(/A/g)` $\rightarrow$ `['A', 'A']` |

### Array-String Conversion: The Split/Join Bridge 🌉

These two methods are crucial for data processing, as they allow conversion between strings and arrays.

| Method | Direction | Purpose | Example |
| :--- | :--- | :--- | :--- |
| **`str.split(separator, limit)`** | String $\rightarrow$ Array | Divides a string into an array of substrings using a specified separator. If the separator is `""`, it splits into individual characters. | `'A,B,C'.split(',')` $\rightarrow$ `['A', 'B', 'C']` |
| **`arr.join(separator)`** | Array $\rightarrow$ String | Concatenates all elements of an array into a single string using the specified separator. | `['A', 'B', 'C'].join('-')` $\rightarrow$ `'A-B-C'` |

-----

## 8\. String Comparison

For most cases, the strict equality operator (`===`) is sufficient. However, for sorting or linguistic checks, special methods are required.

  * **Code Point Comparison (Default):** Standard operators (`<`, `>`) compare strings based on their internal UTF-16 code unit values. This often leads to linguistically incorrect sorting (e.g., `'Zebra' < 'apple'` is `false` because the uppercase 'Z' has a lower code value than the lowercase 'a').

  * **Locale-Sensitive Comparison:**

    **`str.localeCompare(str2)`**

    This method compares two strings based on the current locale's rules (language-specific conventions for sorting).

      * Returns **a negative number** (e.g., `-1`) if $str$ comes *before* $str2$.
      * Returns **a positive number** (e.g., `1`) if $str$ comes *after* $str2$.
      * Returns **$0$** if they are equivalent.

<!-- end list -->

```javascript
// Default comparison is incorrect for sorting based on a dictionary
console.log('Österreich' > 'Zealand'); // true (Incorrect based on most language rules)

// Locale-aware comparison
console.log('Österreich'.localeCompare('Zealand', 'de')); // -1 (Correct: Ö comes before Z in German sorting)
```