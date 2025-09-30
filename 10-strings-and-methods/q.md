# 📘 **Chapter 10: Strings in JavaScript — Text as Data**

> **“Strings are the voice of your program—how it speaks to users, logs data, and shapes the web.”**

---

## 🌟 **1. What Is a String?**

In JavaScript, a **string** is an **immutable sequence of characters** used to represent text. Whether it’s a user’s name, an error message, or HTML content—strings are everywhere.

### 🔑 Key Characteristics:
- **Immutable**: Once created, a string **cannot be changed**. Any “modification” creates a **new string**.
- **UTF-16 encoded**: Supports **emojis**, **accents**, and **global scripts** (e.g., Arabic, Chinese).
- **Primitive type**: `typeof "hello"` returns `"string"` (not `"object"`).

> 💡 **Analogy**: Think of a string like a **read-only document**. You can’t edit it—you can only make a new copy with changes.

### ✅ String Primitive vs. String Object
```js
const primitive = "Hello";           // ✅ Preferred
const object = new String("Hello");  // 🚫 Avoid!

console.log(typeof primitive); // "string"
console.log(typeof object);    // "object" → breaks comparisons!
```
> 🚫 **Never use `new String()`**—it creates an object that behaves unexpectedly.

---

## 🔤 **2. Creating Strings: 3 Ways**

### 1. **Single or Double Quotes**
```js
const single = 'Hello';
const double = "World";
```
- Functionally identical.
- Escape inner quotes:  
  ```js
  'I\'m here'   // → I'm here
  "He said \"Hi\"" // → He said "Hi"
  ```

### 2. **Template Literals (ES6+) → Best Choice!**
Backticks (`` ` ``) enable:
- **Multiline strings**
- **Expression interpolation** with `${...}`

```js
const name = "Ali";
const message = `Hello, ${name}!`; // "Hello, Ali!"

const poem = `
  Roses are red,
  Violets are blue.
`; // Preserves line breaks!
```

✅ **Use template literals for**:
- Dynamic messages
- HTML templates
- Multiline text
- Complex expressions: `` `2 + 3 = ${2 + 3}` ``

### 3. **String Constructor → Avoid!**
```js
const bad = new String("Hello"); // Creates an object
console.log(bad == "Hello");  // true (loose equality)
console.log(bad === "Hello"); // false (strict equality) → 🐞 Bug!
```

---

## 🔍 **3. Essential String Methods at a Glance**

| **Task** | **Method** | **Example** | **Output** |
|--------|----------|-----------|----------|
| Get character | `str.at(-1)` | `"Hi".at(-1)` | `"i"` |
| Check substring | `str.includes("hi")` | `"Hi".includes("hi")` | `false` |
| Find position | `str.indexOf("i")` | `"Hi".indexOf("i")` | `1` |
| Starts/ends with? | `str.startsWith("H")` | `"Hi".startsWith("H")` | `true` |
| Extract part | `str.slice(1, 4)` | `"Hello".slice(1, 4)` | `"ell"` |
| Change case | `str.toLowerCase()` | `"HELLO".toLowerCase()` | `"hello"` |
| Remove whitespace | `str.trim()` | `" hi ".trim()` | `"hi"` |
| Replace all | `str.replaceAll("a", "o")` | `"banana".replaceAll("a", "o")` | `"bonono"` |
| Split into array | `str.split(" ")` | `"a b".split(" ")` | `["a", "b"]` |
| Pad with zeros | `"5".padStart(3, "0")` | — | `"005"` |

> 💡 **Print this table**—it’s your string survival kit!

---

## 🧱 **4. Deep Dive: Core Methods**

### A. **Accessing Characters**
```js
const str = "Hello";

str[0];        // "H" → but str[-1] = undefined ❌
str.charAt(0); // "H" → same as [0]
str.at(-1);    // "o" → ✅ supports negative indexes!
```
> ✅ **Prefer `at()`** for safe access to last characters.

---

### B. **Searching & Checking**
#### `includes()`, `startsWith()`, `endsWith()`
```js
const file = "report.pdf";

file.includes(".pdf");     // true
file.startsWith("report"); // true
file.endsWith(".pdf");     // true
```
→ Return **booleans**—perfect for `if` conditions.

#### `indexOf()` & `lastIndexOf()`
```js
const text = "apple banana apple";

text.indexOf("apple");     // 0 (first)
text.lastIndexOf("apple"); // 14 (last)
```
> ⚠️ **Pitfall**: `indexOf` returns `0` for matches at start → **falsy in `if`!**  
> ✅ **Fix**: Use `includes()` for boolean checks.

---

### C. **Extracting Substrings**
#### `slice(start, end)` → **Best Choice!**
- Supports **negative indexes** (count from end)
- Does **not modify** original string

```js
"stringify".slice(0, 5);   // "strin"
"stringify".slice(-4, -1); // "gif" (last 4 to last 1)
"stringify".slice(2);      // "ringify" (from index 2 to end)
```

#### ❌ Avoid `substring()` and `substr()`
- `substring()`: Swaps args if `start > end`; **no negative support**
- `substr()`: **Deprecated** (not in core spec)—avoid!

> ✅ **Rule**: **Always use `slice()`** for substring extraction.

---

### D. **Modifying Strings**
#### `replace()` vs `replaceAll()`
```js
const text = "apple apple";

text.replace("apple", "orange");     // "orange apple"  (first only)
text.replaceAll("apple", "orange");  // "orange orange" (all matches)
```
> ✅ **Prefer `replaceAll()`**—no regex needed for global replacement!

#### `split()` + `join()` → The Dynamic Duo
```js
// Split into words
"Hello world".split(" "); // ["Hello", "world"]

// Split into characters
"Hi".split(""); // ["H", "i"]

// Reverse a string
"hello".split("").reverse().join(""); // "olleh"
```

---

### E. **Formatting & Padding**
#### `trim()`, `trimStart()`, `trimEnd()`
```js
"  hi  ".trim();      // "hi"
"  hi  ".trimStart(); // "hi  "
"  hi  ".trimEnd();   // "  hi"
```
✅ **Always trim user input** to avoid whitespace bugs.

#### `padStart()` / `padEnd()`
Perfect for **data alignment**:
```js
"5".padStart(3, "0");    // "005" (zero-fill numbers)
"Ali".padEnd(10, ".");   // "Ali......." (align columns)
```

#### `repeat(n)`
```js
"Ha".repeat(3); // "HaHaHa"
```

---

## 🌍 **5. Unicode & Emojis: Beyond ASCII**

JavaScript uses **UTF-16**, so:
- Basic letters: 1 code unit
- Emojis (e.g., 😀): 2 code units (**surrogate pair**)

### ✅ Correct Iteration
```js
// ❌ Broken: for loop with [i]
for (let i = 0; i < "😀".length; i++) {
  console.log("😀"[i]); //   (garbage!)
}

// ✅ Safe: for...of or spread
for (let char of "😀") console.log(char); // 😀
[..."😀"]; // ["😀"]
```

### Working with Code Points
```js
"😀".codePointAt(0);        // 128512
String.fromCodePoint(128512); // "😀"
```

> 💡 **Rule**: Use `for...of` or `[...str]` to iterate strings safely.

---

## 🔎 **6. Comparing Strings**

### Case-Insensitive Comparison
```js
const input = "HELLO";
input.toLowerCase() === "hello"; // true
```

### Language-Aware Sorting
```js
// ❌ Wrong (ASCII order)
["Österreich", "Zealand"].sort(); 
// ["Zealand", "Österreich"]

// ✅ Correct (dictionary order)
["Österreich", "Zealand"].sort((a, b) => a.localeCompare(b)); 
// ["Österreich", "Zealand"]
```

> ✅ **Always use `localeCompare()`** for user-facing sorting.

---

## ⚠️ **7. Common Pitfalls & How to Avoid Them**

### 🚨 Pitfall 1: `replace()` Only Replaces First Match
```js
"aaa".replace("a", "b"); // "baa" → not "bbb"!
// ✅ Fix: use replaceAll() or regex: "aaa".replace(/a/g, "b")
```

### 🚨 Pitfall 2: String-Number Coercion
```js
5 + "10"; // "510" → not 15!
// ✅ Fix: convert explicitly: 5 + Number("10")
```

### 🚨 Pitfall 3: `indexOf` in Conditionals
```js
if ("Hello".indexOf("H")) { /* never runs! */ }
// Because indexOf returns 0 → falsy!
// ✅ Fix: if ("Hello".includes("H"))
```

### 🚨 Pitfall 4: Forgetting Immutability
```js
let str = "Hello";
str[0] = "h"; // Silent failure! str is still "Hello"
// ✅ Fix: str = "h" + str.slice(1);
```

---

## 🛠️ **8. Real-World Use Cases**

### A. **Input Validation**
```js
function isValidEmail(email) {
  return email.includes("@") && 
         (email.endsWith(".com") || email.endsWith(".org"));
}
```

### B. **Capitalizing Names**
```js
function capitalize(str) {
  return str.split(" ")
    .map(word => word.at(0).toUpperCase() + word.slice(1).toLowerCase())
    .join(" ");
}
capitalize("jOHN dOE"); // "John Doe"
```

### C. **Truncate with Ellipsis**
```js
function truncate(str, max) {
  return str.length > max ? str.slice(0, max - 1) + "…" : str;
}
truncate("What I'd like to tell...", 20); // "What I'd like to te…"
```

### D. **Extract Currency**
```js
function extractCurrencyValue(str) {
  return +str.slice(1); // +"120" → 120
}
extractCurrencyValue("$120"); // 120
```

---

## 🧪 **9. Practice Challenges**

### 🔹 Level 1: Uppercase First Letter
Write `ucFirst("john")` → `"John"`
```js
// Solution:
const ucFirst = str => str.at(0).toUpperCase() + str.slice(1);
```

### 🔹 Level 2: Spam Checker
`checkSpam("Buy VIAGRA now")` → `true` (case-insensitive)
```js
// Solution:
const checkSpam = str => 
  str.toLowerCase().includes("viagra") || 
  str.toLowerCase().includes("xxx");
```

### 🔹 Level 3: Safe HTML Escaping
Prevent XSS by escaping HTML:
```js
function escapeHtml(str) {
  return str
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;");
}
escapeHtml("<script>"); // "&lt;script&gt;"
```

---

## ✅ **10. Summary: Best Practices**

| **Do** | **Don’t** |
|------|----------|
| Use **template literals** for dynamic strings | Use `new String()` |
| Prefer **`slice()`** for substring extraction | Use `substr()` (deprecated) |
| Use **`replaceAll()`** for global replacement | Assume `replace()` replaces all |
| **Trim user input** with `trim()` | Forget whitespace in comparisons |
| Iterate with **`for...of`** for Unicode safety | Use `for` loop with `[i]` for emojis |
| Compare with **`localeCompare()`** for sorting | Rely on `<` or `>` for text |

> 💬 **Final Thought**:  
> “Master strings, and you master communication in code.”

---

## 📎 **Appendix: Quick Reference**

```js
// Creation
const msg = `Hello ${name}!`;

// Search
str.includes("text");
str.startsWith("Hi");
str.indexOf("e");

// Extract
str.slice(1, 4);
str.slice(-3);

// Modify
str.replaceAll("old", "new");
str.split(" ").join("-");

// Format
"5".padStart(3, "0"); // "005"
str.trim();

// Unicode
for (let char of str) { }
str.codePointAt(0);
```

