# **Chapter 10: Mastering Strings and Their Methods in JavaScript**

---

## **1. Introduction to Strings**
### **What Are Strings?**
- **Definition**: Strings are **immutable sequences of Unicode characters** used to represent textual data in JavaScript.
- **Encoding**: JavaScript uses **UTF-16**, which supports:
  - Standard characters (A-Z, a-z, 0-9)
  - Special symbols (`@`, `#`, `$`)
  - Emojis (`😊`, `🚀`)
  - Multilingual text (Chinese, Arabic, etc.)
- **Immutability**: Once created, strings **cannot be modified**. All string methods return **new strings**.

### **Why Strings Matter**
- **Ubiquity**: Used in **user input**, **DOM manipulation**, **API responses**, and **data processing**.
- **Versatility**: Essential for **text manipulation**, **form validation**, and **dynamic content generation**.

---

## **2. Creating Strings**
### **A. String Literals**
1. **Single Quotes**
   ```javascript
   const singleQuoted = 'Hello, World!';
   ```
2. **Double Quotes**
   ```javascript
   const doubleQuoted = "Hello, World!";
   ```
3. **Template Literals (Backticks)**
   - **Multi-line strings**:
     ```javascript
     const poem = `
       Roses are red,
       Violets are blue.
     `;
     ```
   - **Embedded expressions**:
     ```javascript
     const name = "Alice";
     const greeting = `Hello, ${name}!`; // "Hello, Alice!"
     ```
   - **Tagged Templates** (Advanced):
     ```javascript
     function highlight(strings, ...values) {
       return strings.reduce((result, str, i) =>
         result + str + (values[i] ? `<mark>${values[i]}</mark>` : ''), '');
     }
     const user = "Bob";
     console.log(highlight`Welcome, ${user}!`); // "Welcome, <mark>Bob</mark>!"
     ```

### **B. String Constructor (Avoid When Possible)**
- Creates a **string object** (not a primitive):
  ```javascript
  const strObj = new String("Hello");
  console.log(typeof strObj); // "object"
  ```
- **When to use**: Rarely needed; prefer primitives (`"Hello"`) for performance.

### **C. Escaping Characters**
| Character | Escape Sequence | Example                     |
|-----------|-----------------|-----------------------------|
| Single Quote | `\'`            | `'It\'s a string'`          |
| Double Quote | `\"`            | `"She said, \"Hi!\""`       |
| Backtick   | `` \` ``        | `` `Backtick: \` ``         |
| Newline    | `\n`            | `"Line 1\nLine 2"`          |
| Tab        | `\t`            | `"Column1\tColumn2"`        |
| Backslash  | `\\`            | `"Path: C:\\\\Program Files"` |

---

## **3. Core String Properties**
### **A. Length**
```javascript
const str = "Hello";
console.log(str.length); // 5
```

### **B. Accessing Characters**
1. **Bracket Notation** (`str[index]`):
   ```javascript
   console.log(str[0]); // "H"
   console.log(str[str.length - 1]); // "o" (last character)
   ```
2. **`.at(index)`** (Supports negative indices):
   ```javascript
   console.log(str.at(-1)); // "o" (last character)
   console.log(str.at(-2)); // "l" (second last character)
   ```

---

## **4. Basic String Methods**
### **A. Case Conversion**
| Method          | Example                     | Output         |
|-----------------|-----------------------------|----------------|
| `.toUpperCase()`| `"hello".toUpperCase()`      | `"HELLO"`      |
| `.toLowerCase()`| `"HELLO".toLowerCase()`      | `"hello"`      |

### **B. Trimming Whitespace**
| Method         | Example                          | Output              |
|----------------|----------------------------------|---------------------|
| `.trim()`      | `"  Hello  ".trim()`             | `"Hello"`           |
| `.trimStart()` | `"  Hello  ".trimStart()`        | `"Hello  "`         |
| `.trimEnd()`   | `"  Hello  ".trimEnd()`          | `"  Hello"`         |

### **C. Searching Within Strings**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.includes(substr)`  | Checks if `substr` exists.                   | `"Hello".includes("e")` → `true`  |
| `.startsWith(substr)`| Checks if string starts with `substr`.       | `"Hello".startsWith("He")` → `true` |
| `.endsWith(substr)`  | Checks if string ends with `substr`.         | `"Hello".endsWith("lo")` → `true` |
| `.indexOf(substr)`   | Returns first index of `substr` or `-1`.     | `"Hello".indexOf("e")` → `1`      |
| `.lastIndexOf(substr)`| Returns last index of `substr` or `-1`.    | `"Hello".lastIndexOf("l")` → `3`  |

### **D. Extracting Substrings**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.slice(start, end)` | Extracts from `start` to `end` (exclusive). Supports **negative indices**. | `"Hello".slice(1, 4)` → `"ell"` |
| `.substring(start, end)` | Similar to `slice`, but **no negative indices**. | `"Hello".substring(1, 4)` → `"ell"` |
| `.substr(start, length)` | **Deprecated**. Use `slice` instead.       | `"Hello".substr(1, 3)` → `"ell"` |

---

## **5. Intermediate String Methods**
### **A. Concatenation**
1. **`+` Operator**:
   ```javascript
   const greeting = "Hello, " + "world!"; // "Hello, world!"
   ```
2. **`.concat()`**:
   ```javascript
   const str1 = "Hello";
   const str2 = "world";
   console.log(str1.concat(", ", str2, "!")); // "Hello, world!"
   ```

### **B. Replacing Substrings**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.replace(search, replacement)` | Replaces **first occurrence** of `search`. | `"Hello".replace("e", "a")` → `"Hallo"` |
| `.replaceAll(search, replacement)` | Replaces **all occurrences**.              | `"Hello".replaceAll("l", "x")` → `"Hexxo"` |

### **C. Splitting and Joining**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.split(separator)`  | Splits string into an array.                | `"a,b,c".split(",")` → `["a", "b", "c"]` |
| `.join(delimiter)`   | Joins array into a string.                  | `["a", "b", "c"].join("-")` → `"a-b-c"` |

### **D. Repeating Strings**
```javascript
console.log("Ha".repeat(3)); // "HaHaHa"
```

### **E. Padding Strings**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.padStart(length, char)` | Pads start to `length` with `char`.    | `"5".padStart(3, "0")` → `"005"` |
| `.padEnd(length, char)`   | Pads end to `length` with `char`.      | `"5".padEnd(3, "0")` → `"500"`   |

---

## **6. Advanced String Methods**
### **A. Regular Expressions**
| Method       | Description                                  | Example                          |
|--------------|----------------------------------------------|----------------------------------|
| `.match(regex)` | Returns regex matches as an array.          | `"cat".match(/[a-z]/g)` → `["c", "a", "t"]` |
| `.search(regex)` | Returns index of first regex match.         | `"cat".search(/a/)` → `1`        |
| `.replace(regex, replacement)` | Replaces regex matches.                  | `"cat".replace(/a/, "o")` → `"cot"` |

### **B. Unicode Methods**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `String.fromCharCode(code1, code2)` | Creates string from Unicode values. | `String.fromCharCode(72, 101)` → `"He"` |
| `.codePointAt(index)`| Returns Unicode value at `index`.           | `"A".codePointAt(0)` → `65`       |

### **C. Character Methods**
| Method               | Description                                  | Example                          |
|----------------------|----------------------------------------------|----------------------------------|
| `.charAt(index)`     | Returns character at `index`.                | `"Hello".charAt(1)` → `"e"`      |
| `.charCodeAt(index)` | Returns Unicode value at `index`.           | `"Hello".charCodeAt(0)` → `72`   |

---

## **7. Practical Use Cases**
### **A. Form Validation**
```javascript
function isValidEmail(email) {
  return email.includes("@") && email.endsWith(".com");
}
console.log(isValidEmail("user@example.com")); // true
```

### **B. Text Truncation**
```javascript
function truncate(str, maxLength) {
  return str.length > maxLength ? str.slice(0, maxLength - 1) + "…" : str;
}
console.log(truncate("Hello, world!", 8)); // "Hello,…"
```

### **C. Extracting Numbers from Strings**
```javascript
function extractNumber(str) {
  return Number(str.slice(1));
}
console.log(extractNumber("$120")); // 120
```

### **D. Palindrome Checker**
```javascript
function isPalindrome(str) {
  const reversed = str.split("").reverse().join("");
  return str === reversed;
}
console.log(isPalindrome("madam")); // true
```

### **E. Counting Vowels**
```javascript
function countVowels(str) {
  const vowels = str.match(/[aeiou]/gi);
  return vowels ? vowels.length : 0;
}
console.log(countVowels("hello")); // 2
```

---

## **8. Common Pitfalls and Best Practices**
### **A. String vs. Number Coercion**
```javascript
console.log(5 + "10"); // "510" (string concatenation)
console.log(5 + Number("10")); // 15 (numeric addition)
```

### **B. Whitespace Issues**
```javascript
console.log("Hello" + " World"); // "Hello World" (no space)
console.log("Hello" + " " + "World"); // "Hello World" (explicit space)
```

### **C. Special Characters**
```javascript
console.log('He said, "Hi!"'); // Error (unclosed quote)
console.log('He said, \"Hi!\"'); // Correct (escaped quote)
```

### **D. Immutability**
```javascript
let str = "Hi";
str[0] = "h"; // No effect (strings are immutable)
str = "h" + str[1]; // "hi" (create a new string)
```

---

## **9. Exercises**
1. **Reverse a String**:
   ```javascript
   function reverseString(str) {
     return str.split("").reverse().join("");
   }
   console.log(reverseString("hello")); // "olleh"
   ```

2. **Capitalize Words**:
   ```javascript
   function capitalizeWords(str) {
     return str.split(" ").map(word =>
       word.charAt(0).toUpperCase() + word.slice(1)
     ).join(" ");
   }
   console.log(capitalizeWords("hello world")); // "Hello World"
   ```

3. **Extract Domain from Email**:
   ```javascript
   function extractDomain(email) {
     return email.split("@")[1];
   }
   console.log(extractDomain("user@example.com")); // "example.com"
   ```

4. **Format Phone Number**:
   ```javascript
   function formatPhoneNumber(num) {
     return num.replace(/(\d{3})(\d{3})(\d{4})/, "($1) $2-$3");
   }
   console.log(formatPhoneNumber("1234567890")); // "(123) 456-7890"
   ```

---

## **10. Summary Table**
| Category          | Methods/Properties                     | Example                          |
|-------------------|----------------------------------------|----------------------------------|
| **Quotes**        | `` ` ``, `' '`, `" "`                  | `` `Hello ${name}` ``            |
| **Length**        | `.length`                              | `"Hello".length` → `5`           |
| **Case**          | `.toUpperCase()`, `.toLowerCase()`      | `"Hello".toLowerCase()` → `"hello"` |
| **Search**        | `.indexOf()`, `.includes()`             | `"Hello".includes("e")` → `true` |
| **Extract**       | `.slice()`, `.substring()`             | `"Hello".slice(1, 4)` → `"ell"`  |
| **Modify**        | `.replace()`, `.split()`, `.join()`     | `"a,b".split(",")` → `["a", "b"]` |
| **Compare**       | `.localeCompare()`                     | `"a".localeCompare("b")` → `-1` |



