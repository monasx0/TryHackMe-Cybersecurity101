# JavaScript Essentials
## Task 1 - Introduction

**JavaScript** (**JS**) is a popular scripting language that allows **web developers** to add interactive features to **websites** containing **HTML** and **CSS**. It enables functionalities like validation, onClick actions, animations, and more. **JS** scripts are primarily used with **HTML** and are essential for creating dynamic **web** pages.  

---
## Task 2 - Essential Concepts
### Variables

**Variables** in **JS** are containers for storing data values and are declared using:

- **`var`** – **function-scoped**; can be redeclared and updated.  
- **`let`** – **block-scoped**; can be updated but not redeclared in the same block.  
- **`const`** – **block-scoped and constant**; cannot be updated or redeclared.

**Example:**
```
let name = "Alice";
const age = 25;
var score = 100;
```

### Functions
A **function** is a reusable block of code that performs a specific task.

**Example**:
```
function PrintResult(rollNum) {
    alert("Username with roll number " + rollNum + " has passed the exam");
}

const rollNumbers = [101, 102, 103];
for (let i = 0; i < 3; i++) {
    PrintResult(rollNumbers[i]);

}
```
### Loops
**Loops** allow code repetition based on a condition (for, while, do...while).

**Example**:
```
for (let i = 0; i < 100; i++) {
    PrintResult(rollNumbers[i]);
}
```
### Request-Response Cycle
The **request-response cycle** occurs when a browser (**client**) sends a request to a server, which then returns a **webpage**, **data**, or other resources.

## Task 3 - JavaScript Overview
**JS** is **interpreted** (executed directly in the browser).

**Example**:
```
console.log("Hello, World!");

let age = 25;
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}

function greet(name) {
    console.log("Hello, " + name + "!");
}
greet("Bob");
```
### Chrome Console

- Open with **Ctrl+Shift+I** → Console tab.
- **Paste** and run **JS code** directly.

#### Example – Adding Numbers
```
let x = 5;
let y = 10;
let result = x + y;
console.log("The result is: " + result);
```
## Task 4 - Integrating JS in HTML
### Internal JS
**JS** code is embedded directly within **HTML** using **<script>** tags.

**Example**:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Internal JS</title>
</head>
<body>
    <h1>Addition of Two Numbers</h1>
    <p id="result"></p>

    <script>
        let x = 5;
        let y = 10;
        let result = x + y;
        document.getElementById("result").innerHTML = "The result is: " + result;
    </script>
</body>
</html>
```
### External JS
**JS code** is placed in a separate `.js` file and linked using `src`.

#### **Example** – `script.js`:
```
let x = 5;
let y = 10;
let result = x + y;
document.getElementById("result").innerHTML = "The result is: " + result;
```
#### Example – `external.html`:
```
<script src="script.js"></script>
```
## Task 5 - Abusing Dialogue Functions
**JS** dialogue functions can be abused if not handled securely.
- **alert** – Displays a message with "OK".
- **prompt** – Asks user input and returns the value.
- **confirm** – Asks for confirmation; returns true/false.

#### Malicious Example – Alert Spam:
```
<script>
for (let i = 0; i < 500; i++) {
    alert("Hacked");
}
</script>
```

## Task 6 - Control Flow Statements
**JS** **executes** code in a defined order using conditional statements:
- **if-else** – Execute blocks based on conditions.
- **switch** – Execute based on multiple possible values.
- **Loops** – Repeat actions (for, while, do...while).

#### Example – Age Verification
```
<script>
age = prompt("What is your age")
if (age >= 18) {
    document.getElementById("message").innerHTML = "You are an adult.";
} else {
    document.getElementById("message").innerHTML = "You are a minor.";
}
</script>
```

### Bypassing Login Forms
**JS-based** login forms can be **bypassed** if **credentials** are visible in the **source code**.
## Task 7 - Minification & Obfuscation
### Minification:
**Minification** removes unnecessary spaces, comments, and shortens **variable** names to reduce file size and improve loading speed.

### Obfuscation:
**Obfuscation** makes the code difficult to read for humans while keeping it fully functional, making **reverse engineering** more challenging.

## Task 8 - Conclusion
**JavaScript** is a powerful scripting language used to make websites interactive and dynamic. In this module, we covered **variables**, **data types**, **functions**, **loops**, **control flow**, **dialogue functions**, and **JS integration** with **HTML**. We also explored **minified** and **obfuscated JS** and learned best practices to write secure and **maintainable code**. Mastering these basics lays the foundation for building **web applications** and understanding potential **security risks**.
### What I Learned
- **JS** basics and syntax
- **Functions**, **loops**, and **variables**
- **Integrating JS** in **HTML** (**internal & external**)
- **Interactive elements** (**alert, prompt, confirm**)
- **Control flow statements** and **login form bypass**
- **Minified** and **obfuscated JS**
