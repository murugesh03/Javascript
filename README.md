# 📘 JavaScript — Complete Concepts Guide

> A comprehensive, beginner-to-advanced reference covering every core JavaScript concept with detailed explanations, syntax, and real code examples.

---

## 📚 Table of Contents

1. [Introduction to JavaScript](#1-introduction-to-javascript)
2. [Variables & Data Types](#2-variables--data-types)
3. [Operators](#3-operators)
4. [Control Flow](#4-control-flow)
5. [Functions](#5-functions)
6. [Arrays](#6-arrays)
7. [Objects](#7-objects)
8. [Strings](#8-strings)
9. [Numbers & Math](#9-numbers--math)
10. [Date & Time](#10-date--time)
11. [Scope & Closures](#11-scope--closures)
12. [Hoisting](#12-hoisting)
13. [The `this` Keyword](#13-the-this-keyword)
14. [Prototypes & Inheritance](#14-prototypes--inheritance)
15. [Classes](#15-classes)
16. [Error Handling](#16-error-handling)
17. [Asynchronous JavaScript](#17-asynchronous-javascript)
18. [Promises](#18-promises)
19. [Async / Await](#19-async--await)
20. [ES6+ Modern Features](#20-es6-modern-features)
21. [Destructuring](#21-destructuring)
22. [Spread & Rest Operators](#22-spread--rest-operators)
23. [Modules](#23-modules)
24. [DOM Manipulation](#24-dom-manipulation)
25. [Events](#25-events)
26. [Fetch API & AJAX](#26-fetch-api--ajax)
27. [Local Storage & Session Storage](#27-local-storage--session-storage)
28. [Regular Expressions](#28-regular-expressions)
29. [Iterators & Generators](#29-iterators--generators)
30. [Symbol, Map, Set, WeakMap, WeakSet](#30-symbol-map-set-weakmap-weakset)
31. [Proxy & Reflect](#31-proxy--reflect)
32. [Memory Management & Garbage Collection](#32-memory-management--garbage-collection)
33. [Design Patterns in JavaScript](#33-design-patterns-in-javascript)
34. [Functional Programming Concepts](#34-functional-programming-concepts)
35. [Performance Best Practices](#35-performance-best-practices)

---

## 1. Introduction to JavaScript

### What is JavaScript?

JavaScript is a **lightweight, interpreted, dynamically-typed** programming language that is one of the three core technologies of the World Wide Web, alongside HTML and CSS.

- **Created by:** Brendan Eich in 1995 (in just 10 days!)
- **Standardized as:** ECMAScript (ES)
- **Runs in:** Browsers (client-side) and servers (Node.js)
- **Paradigm:** Multi-paradigm: object-oriented, functional, event-driven

### How JavaScript Runs

```
Source Code (.js file)
       ↓
  JavaScript Engine (e.g., V8 in Chrome, SpiderMonkey in Firefox)
       ↓
   Parsing (builds Abstract Syntax Tree)
       ↓
   Compilation (Just-In-Time — JIT)
       ↓
   Execution (machine code runs)
```

### Your First JavaScript Program

```javascript
// This is a single-line comment

/*
  This is a
  multi-line comment
*/

// Print to console
console.log("Hello, World!");

// Alert in browser
alert("Hello!");

// Get input from user (browser only)
let name = prompt("What is your name?");
console.log("Hello, " + name);
```

### Where to Write JavaScript

```html
<!-- 1. Inline in HTML -->
<button onclick="alert('Clicked!')">Click Me</button>

<!-- 2. Internal script tag -->
<script>
  console.log("Internal JS");
</script>

<!-- 3. External file (BEST PRACTICE) -->
<script src="app.js" defer></script>
```

---

## 2. Variables & Data Types

### Declaring Variables

JavaScript has three ways to declare variables:

```javascript
// var — old way, function-scoped, avoid in modern JS
var oldVariable = "I am var";

// let — modern, block-scoped, can be reassigned
let age = 25;
age = 26; // ✅ allowed

// const — modern, block-scoped, cannot be reassigned
const PI = 3.14159;
// PI = 3; // ❌ TypeError: Assignment to constant variable
```

### Comparison Table

| Feature | `var` | `let` | `const` |
|---|---|---|---|
| Scope | Function | Block | Block |
| Hoisting | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |
| Re-declare | Yes | No | No |
| Re-assign | Yes | Yes | No |
| Global object property | Yes | No | No |

### Primitive Data Types

JavaScript has **8 data types** — 7 primitives + 1 object type:

```javascript
// 1. Number — integers and floats
let integer = 42;
let float   = 3.14;
let negative = -100;
let bigNum  = 1_000_000; // underscores for readability

// 2. BigInt — for very large integers
let bigInteger = 9007199254740991n; // add 'n' at the end
let huge = BigInt("9007199254740992");

// 3. String — text
let single = 'Hello';
let double = "World";
let template = `Hello, ${single} ${double}!`; // template literal

// 4. Boolean — true or false
let isLoggedIn = true;
let hasError   = false;

// 5. undefined — variable declared but not assigned
let notAssigned;
console.log(notAssigned); // undefined

// 6. null — intentional absence of value
let emptyValue = null;

// 7. Symbol — unique identifier
let sym1 = Symbol("id");
let sym2 = Symbol("id");
console.log(sym1 === sym2); // false — always unique!

// 8. Object — collection of key-value pairs (non-primitive)
let person = { name: "Alice", age: 30 };
```

### Checking Data Types

```javascript
// typeof operator
console.log(typeof 42);          // "number"
console.log(typeof "hello");     // "string"
console.log(typeof true);        // "boolean"
console.log(typeof undefined);   // "undefined"
console.log(typeof null);        // "object" ← famous bug in JS!
console.log(typeof {});          // "object"
console.log(typeof []);          // "object" ← arrays are objects!
console.log(typeof function(){}); // "function"
console.log(typeof Symbol());    // "symbol"
console.log(typeof 42n);         // "bigint"

// Better array check:
console.log(Array.isArray([]));  // true ✅
console.log(Array.isArray({}));  // false ✅
```

### Type Conversion

```javascript
// Implicit (Type Coercion) — JS does it automatically
console.log("5" + 3);   // "53"  ← + triggers string concat
console.log("5" - 3);   // 2     ← - forces number conversion
console.log(true + 1);  // 2     ← true becomes 1
console.log(false + 1); // 1     ← false becomes 0
console.log("" + null); // "null"

// Explicit (Type Casting) — you do it intentionally
// To Number:
Number("42");       // 42
Number("3.14");     // 3.14
Number("");         // 0
Number("hello");    // NaN
Number(true);       // 1
Number(false);      // 0
Number(null);       // 0
Number(undefined);  // NaN
parseInt("42px");   // 42 ← stops at non-numeric
parseFloat("3.14abc"); // 3.14

// To String:
String(42);         // "42"
String(true);       // "true"
String(null);       // "null"
(42).toString();    // "42"
(255).toString(16); // "ff" ← hexadecimal
(8).toString(2);    // "1000" ← binary

// To Boolean:
Boolean(0);         // false
Boolean("");        // false
Boolean(null);      // false
Boolean(undefined); // false
Boolean(NaN);       // false
Boolean(false);     // false
// Everything else is TRUE:
Boolean(1);         // true
Boolean("hello");   // true
Boolean([]);        // true ← empty array is truthy!
Boolean({});        // true ← empty object is truthy!
```

### Falsy vs Truthy Values

```javascript
// FALSY values (evaluate to false in boolean context):
false
0
-0
0n           // BigInt zero
""           // empty string
''           // empty string
``           // empty template literal
null
undefined
NaN

// TRUTHY values (everything else):
true
1
-1
"hello"
"0"          // string "0" is truthy!
[]           // empty array is truthy!
{}           // empty object is truthy!
function(){} // functions are truthy
```

### Special Number Values

```javascript
// NaN — Not a Number
console.log(0 / 0);          // NaN
console.log("hello" * 2);    // NaN
console.log(NaN === NaN);    // false! (NaN is not equal to itself)
console.log(isNaN("hello")); // true
console.log(Number.isNaN("hello")); // false (more strict)
console.log(Number.isNaN(NaN));     // true

// Infinity
console.log(1 / 0);          // Infinity
console.log(-1 / 0);         // -Infinity
console.log(isFinite(100));  // true
console.log(isFinite(Infinity)); // false

// Safe integer limits
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
console.log(Number.MIN_SAFE_INTEGER); // -9007199254740991
console.log(Number.MAX_VALUE);        // 1.7976931348623157e+308
```

---

## 3. Operators

### Arithmetic Operators

```javascript
let a = 10, b = 3;

console.log(a + b);  // 13  — addition
console.log(a - b);  // 7   — subtraction
console.log(a * b);  // 30  — multiplication
console.log(a / b);  // 3.333... — division
console.log(a % b);  // 1   — modulo (remainder)
console.log(a ** b); // 1000 — exponentiation (10³)

// Increment / Decrement
let x = 5;
console.log(x++); // 5 — returns THEN increments
console.log(x);   // 6
console.log(++x); // 7 — increments THEN returns
console.log(x--); // 7 — returns THEN decrements
console.log(x);   // 6
```

### Assignment Operators

```javascript
let n = 10;

n += 5;   // n = n + 5  → 15
n -= 3;   // n = n - 3  → 12
n *= 2;   // n = n * 2  → 24
n /= 4;   // n = n / 4  → 6
n %= 4;   // n = n % 4  → 2
n **= 3;  // n = n ** 3 → 8

// Logical assignment (ES2021)
let a = null;
a ??= "default";   // assign if null or undefined → "default"

let b = 0;
b ||= 42;          // assign if falsy → 42

let c = 1;
c &&= 99;          // assign if truthy → 99
```

### Comparison Operators

```javascript
// == (loose equality — converts types)
console.log(5 == "5");    // true  ← type coercion!
console.log(0 == false);  // true
console.log(null == undefined); // true
console.log(null == 0);   // false (null only == undefined)

// === (strict equality — NO type conversion)
console.log(5 === "5");   // false ← different types
console.log(5 === 5);     // true
console.log(null === undefined); // false

// Relational
console.log(10 > 5);     // true
console.log(10 >= 10);   // true
console.log(5 < 3);      // false
console.log(5 <= 5);     // true

// != and !==
console.log(5 != "5");   // false ← coerces, they're "equal"
console.log(5 !== "5");  // true  ← strict, different types

// RULE: Always use === and !== to avoid bugs!
```

### Logical Operators

```javascript
// AND (&&) — true only if BOTH are truthy
console.log(true && true);   // true
console.log(true && false);  // false
console.log(false && true);  // false

// Short-circuit: stops at first falsy
console.log(0 && "hello");   // 0 (stopped, returned falsy)
console.log(1 && "hello");   // "hello" (returned last truthy)
console.log(1 && 2 && 3);    // 3

// OR (||) — true if AT LEAST ONE is truthy
console.log(true || false);  // true
console.log(false || false); // false

// Short-circuit: stops at first truthy
console.log(0 || "hello");   // "hello"
console.log("" || null || "default"); // "default"
console.log(1 || "hello");   // 1 (stopped at first truthy)

// NOT (!) — inverts boolean
console.log(!true);   // false
console.log(!false);  // true
console.log(!0);      // true
console.log(!"");     // true
console.log(!!"hello"); // true (double NOT → boolean cast)

// Nullish Coalescing (??) — only null/undefined triggers fallback
console.log(null ?? "default");      // "default"
console.log(undefined ?? "default"); // "default"
console.log(0 ?? "default");         // 0 ← 0 is NOT null/undefined!
console.log("" ?? "default");        // "" ← empty string is NOT nullish!
```

### Ternary Operator

```javascript
// Syntax: condition ? valueIfTrue : valueIfFalse

let age = 20;
let status = age >= 18 ? "adult" : "minor";
console.log(status); // "adult"

// Can be chained (but avoid deep nesting — hard to read)
let score = 75;
let grade = score >= 90 ? "A"
          : score >= 80 ? "B"
          : score >= 70 ? "C"
          : score >= 60 ? "D"
          : "F";
console.log(grade); // "C"
```

### Optional Chaining (?.)

```javascript
// Without optional chaining — can throw errors
let user = null;
// console.log(user.address.city); // ❌ TypeError!

// With optional chaining — safely returns undefined
console.log(user?.address?.city);    // undefined ✅
console.log(user?.getName?.());      // undefined ✅ (method call)
console.log(user?.hobbies?.[0]);     // undefined ✅ (array access)

// Practical example
let config = {
  database: {
    host: "localhost",
    port: 5432
  }
};
console.log(config?.database?.host);   // "localhost"
console.log(config?.cache?.host);      // undefined (no error!)
```

### Bitwise Operators

```javascript
// Works on 32-bit binary representations
let a = 5;  // binary: 0101
let b = 3;  // binary: 0011

console.log(a & b);   // 1  — AND:  0101 & 0011 = 0001
console.log(a | b);   // 7  — OR:   0101 | 0011 = 0111
console.log(a ^ b);   // 6  — XOR:  0101 ^ 0011 = 0110
console.log(~a);       // -6 — NOT:  ~0101 = -(5+1)
console.log(a << 1);  // 10 — Left shift:  0101 → 1010
console.log(a >> 1);  // 2  — Right shift: 0101 → 0010

// Common trick: ~~x is a fast Math.floor for positive numbers
console.log(~~3.7);   // 3
console.log(~~-3.7);  // -3 (not same as Math.floor for negatives!)
```

---

## 4. Control Flow

### if / else if / else

```javascript
// Syntax:
if (condition) {
  // runs if condition is truthy
} else if (anotherCondition) {
  // runs if anotherCondition is truthy
} else {
  // runs if none of the above
}

// Example:
let temperature = 28;

if (temperature > 35) {
  console.log("It's very hot!");
} else if (temperature > 25) {
  console.log("It's warm");       // ← this runs
} else if (temperature > 15) {
  console.log("It's cool");
} else {
  console.log("It's cold!");
}
```

### Switch Statement

```javascript
// Syntax:
switch (expression) {
  case value1:
    // code
    break;   // IMPORTANT: prevents fall-through!
  case value2:
    // code
    break;
  default:
    // runs if no case matches
}

// Example:
let day = "Monday";

switch (day) {
  case "Monday":
  case "Tuesday":
  case "Wednesday":
  case "Thursday":
  case "Friday":
    console.log("Weekday");  // ← runs
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend");
    break;
  default:
    console.log("Invalid day");
}

// Modern alternative using object lookup:
const messages = {
  Monday: "Start of the week",
  Friday: "Almost weekend!",
  Saturday: "Weekend!",
  Sunday: "Weekend!"
};
console.log(messages[day] ?? "Unknown day");
```

### for Loop

```javascript
// Syntax:
for (initialization; condition; update) {
  // body
}

// Basic example — count up:
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

// Count down:
for (let i = 5; i >= 1; i--) {
  console.log(i); // 5, 4, 3, 2, 1
}

// Iterate over array:
const fruits = ["apple", "banana", "cherry"];
for (let i = 0; i < fruits.length; i++) {
  console.log(i, fruits[i]);
}

// Nested loops:
for (let row = 1; row <= 3; row++) {
  for (let col = 1; col <= 3; col++) {
    process.stdout.write(`(${row},${col}) `);
  }
  console.log(); // newline
}
// (1,1) (1,2) (1,3)
// (2,1) (2,2) (2,3)
// (3,1) (3,2) (3,3)
```

### while Loop

```javascript
// Syntax:
while (condition) {
  // runs as long as condition is truthy
}

// Example:
let count = 0;
while (count < 5) {
  console.log(count); // 0, 1, 2, 3, 4
  count++;
}

// Infinite loop (use break to exit):
let attempts = 0;
while (true) {
  attempts++;
  if (attempts >= 3) {
    console.log("Stopping after 3 attempts");
    break;
  }
}
```

### do...while Loop

```javascript
// Syntax: runs body AT LEAST ONCE, then checks condition
do {
  // body (always runs at least once)
} while (condition);

// Example:
let input = 0;
do {
  console.log("Running:", input);
  input++;
} while (input < 3);
// Running: 0
// Running: 1
// Running: 2

// Use case: menu that must show at least once
let choice;
do {
  choice = prompt("Enter 1 to continue or 0 to exit:");
} while (choice !== "0");
```

### for...of Loop (ES6)

```javascript
// Iterates over ITERABLE values (arrays, strings, Maps, Sets, etc.)

// Arrays:
const colors = ["red", "green", "blue"];
for (const color of colors) {
  console.log(color); // red, green, blue
}

// With index (using entries()):
for (const [index, color] of colors.entries()) {
  console.log(index, color); // 0 red, 1 green, 2 blue
}

// Strings:
for (const char of "Hello") {
  console.log(char); // H, e, l, l, o
}

// Maps:
const map = new Map([["a", 1], ["b", 2]]);
for (const [key, value] of map) {
  console.log(key, value); // a 1, b 2
}

// Sets:
const set = new Set([1, 2, 3]);
for (const value of set) {
  console.log(value); // 1, 2, 3
}
```

### for...in Loop

```javascript
// Iterates over ENUMERABLE PROPERTY KEYS of an object
// ⚠️ Use for...of for arrays — for...in also gets prototype properties!

const person = { name: "Alice", age: 30, city: "NYC" };

for (const key in person) {
  console.log(key, ":", person[key]);
}
// name : Alice
// age : 30
// city : NYC

// Check own properties (exclude inherited):
for (const key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(key);
  }
}
```

### break and continue

```javascript
// break — exits the loop entirely
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i); // 0, 1, 2, 3, 4
}

// continue — skips current iteration, goes to next
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue; // skip even numbers
  console.log(i); // 1, 3, 5, 7, 9
}

// Labeled break — exit outer loop from inner loop
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (j === 1) break outer; // exits BOTH loops
    console.log(i, j);
  }
}
// 0 0  ← only this runs before outer break
```

---

## 5. Functions

### Function Declaration

```javascript
// Syntax:
function functionName(parameter1, parameter2) {
  // function body
  return value; // optional
}

// Example:
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Alice")); // "Hello, Alice!"
console.log(greet());        // "Hello, undefined!" ← missing param

// Hoisted — can be called BEFORE declaration:
sayHello(); // works!
function sayHello() {
  console.log("Hello!");
}
```

### Function Expression

```javascript
// Syntax: function stored in a variable
const functionName = function(params) {
  return value;
};

// Named function expression (useful for debugging & recursion):
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
};

console.log(factorial(5)); // 120

// NOT hoisted — cannot call before declaration:
// greet(); // ❌ ReferenceError
const greet = function(name) {
  return `Hi, ${name}!`;
};
```

### Arrow Functions (ES6)

```javascript
// Syntax: compact function notation
const functionName = (params) => expression; // implicit return
const functionName2 = (params) => { return expression; }; // explicit return

// Examples:
const add = (a, b) => a + b;
console.log(add(3, 4)); // 7

// Single param — parentheses optional:
const double = n => n * 2;
console.log(double(5)); // 10

// No params — parentheses required:
const greet = () => "Hello!";

// Multi-line — use curly braces + return:
const multiply = (a, b) => {
  const result = a * b;
  return result;
};

// Return object literal — wrap in parentheses:
const makeUser = (name, age) => ({ name, age });
console.log(makeUser("Alice", 30)); // {name: "Alice", age: 30}

// Arrow functions DON'T have their own 'this':
const obj = {
  name: "Alice",
  greet: function() {
    const inner = () => {
      console.log(this.name); // "Alice" — uses outer 'this'
    };
    inner();
  }
};
obj.greet();
```

### Default Parameters

```javascript
// Syntax:
function functionName(param = defaultValue) { }

// Examples:
function greet(name = "World", punctuation = "!") {
  return `Hello, ${name}${punctuation}`;
}

console.log(greet());              // "Hello, World!"
console.log(greet("Alice"));      // "Hello, Alice!"
console.log(greet("Bob", "..."))  // "Hello, Bob..."

// Default can be an expression or function call:
function makeId(prefix, id = Date.now()) {
  return `${prefix}-${id}`;
}

// Default can reference earlier parameters:
function range(start, end = start + 10) {
  return [start, end];
}
console.log(range(5));    // [5, 15]
console.log(range(5, 8)); // [5, 8]
```

### Rest Parameters

```javascript
// Syntax: ...paramName collects remaining arguments into an array
function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sum(1, 2));        // 3
console.log(sum(1, 2, 3, 4)); // 10

// Rest must be the LAST parameter:
function log(level, ...messages) {
  messages.forEach(msg => console.log(`[${level}] ${msg}`));
}

log("INFO", "Server started", "Listening on port 3000");
// [INFO] Server started
// [INFO] Listening on port 3000
```

### Higher-Order Functions

```javascript
// A function that takes a function as argument OR returns a function

// 1. Function as argument:
function doTwice(fn, value) {
  return fn(fn(value));
}

const addTen = x => x + 10;
console.log(doTwice(addTen, 5)); // 25 (5 → 15 → 25)

// 2. Function that returns a function (function factory):
function makeMultiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const triple = makeMultiplier(3);
const quadruple = makeMultiplier(4);
console.log(triple(5));    // 15
console.log(quadruple(5)); // 20

// 3. Common built-in HOFs:
const numbers = [1, 2, 3, 4, 5];
const doubled  = numbers.map(n => n * 2);       // [2, 4, 6, 8, 10]
const evens    = numbers.filter(n => n % 2 === 0); // [2, 4]
const total    = numbers.reduce((acc, n) => acc + n, 0); // 15
```

### Immediately Invoked Function Expression (IIFE)

```javascript
// Syntax: wrap function in () then immediately call it with ()
(function() {
  // code runs immediately
  console.log("IIFE executed!");
})();

// With arrow function:
(() => {
  console.log("Arrow IIFE!");
})();

// With parameters:
(function(name) {
  console.log(`Hello, ${name}!`);
})("Alice");

// Use case: create private scope to avoid polluting global:
const counter = (function() {
  let count = 0; // private variable!
  return {
    increment() { count++; },
    decrement() { count--; },
    getCount()  { return count; }
  };
})();

counter.increment();
counter.increment();
console.log(counter.getCount()); // 2
console.log(counter.count);      // undefined ← private!
```

### Function Properties & Methods

```javascript
function greet(greeting, punctuation) {
  return `${greeting}, ${this.name}${punctuation}`;
}

// .length — number of declared parameters
console.log(greet.length); // 2

// .name — function name
console.log(greet.name);   // "greet"

// .call(thisArg, arg1, arg2, ...) — call with specific 'this'
const person = { name: "Alice" };
console.log(greet.call(person, "Hello", "!")); // "Hello, Alice!"

// .apply(thisArg, [args]) — like call but args in array
console.log(greet.apply(person, ["Hi", "?"])); // "Hi, Alice?"

// .bind(thisArg, args) — returns NEW function with bound 'this'
const greetAlice = greet.bind(person, "Hey");
console.log(greetAlice(".")); // "Hey, Alice."
```

---

## 6. Arrays

### Creating Arrays

```javascript
// Array literal (preferred):
const empty = [];
const fruits = ["apple", "banana", "cherry"];
const mixed = [1, "hello", true, null, { x: 1 }, [2, 3]];

// Array constructor:
const arr1 = new Array(3);            // [empty × 3] — 3 empty slots
const arr2 = new Array(1, 2, 3);     // [1, 2, 3]

// Array.from():
Array.from("hello");                  // ["h","e","l","l","o"]
Array.from({length: 5}, (_, i) => i); // [0, 1, 2, 3, 4]
Array.from(new Set([1, 2, 2, 3]));    // [1, 2, 3]

// Array.of():
Array.of(1, 2, 3);  // [1, 2, 3]
Array.of(7);        // [7] (vs new Array(7) = 7 empty slots!)
```

### Accessing & Modifying

```javascript
const fruits = ["apple", "banana", "cherry"];

// Access by index (0-based):
console.log(fruits[0]);         // "apple"
console.log(fruits[2]);         // "cherry"
console.log(fruits[fruits.length - 1]); // "cherry" (last element)
console.log(fruits.at(-1));     // "cherry" ← ES2022 .at() method

// Modify:
fruits[1] = "blueberry";
console.log(fruits); // ["apple", "blueberry", "cherry"]

// Length:
console.log(fruits.length); // 3
fruits.length = 2;           // truncates array!
console.log(fruits);        // ["apple", "blueberry"]
```

### Array Methods — Adding & Removing

```javascript
const arr = [1, 2, 3];

// Add to END:
arr.push(4, 5);       // returns new length; arr = [1,2,3,4,5]

// Remove from END:
const last = arr.pop();       // returns removed element; arr = [1,2,3,4]

// Add to BEGINNING:
arr.unshift(0);       // returns new length; arr = [0,1,2,3,4]

// Remove from BEGINNING:
const first = arr.shift();    // returns removed element; arr = [1,2,3,4]

// splice(start, deleteCount, ...itemsToInsert):
arr.splice(1, 2);             // removes 2 elements from index 1; arr = [1,4]
arr.splice(1, 0, 10, 11);    // inserts 10,11 at index 1; arr = [1,10,11,4]
arr.splice(2, 1, 99);         // replaces 1 element at index 2; arr = [1,10,99,4]

// slice(start, end) — returns new array, NON-MUTATING:
const nums = [0, 1, 2, 3, 4, 5];
console.log(nums.slice(1, 4));  // [1, 2, 3] (end is exclusive)
console.log(nums.slice(-2));    // [4, 5] (last 2)
console.log(nums.slice());      // shallow copy of entire array
```

### Array Methods — Searching

```javascript
const fruits = ["apple", "banana", "cherry", "banana"];

// indexOf — first occurrence index (-1 if not found):
console.log(fruits.indexOf("banana"));    // 1
console.log(fruits.indexOf("grape"));     // -1
console.log(fruits.lastIndexOf("banana")); // 3

// includes — boolean check:
console.log(fruits.includes("cherry")); // true
console.log(fruits.includes("grape"));  // false

// find — returns first matching ELEMENT:
const nums = [5, 12, 8, 130, 44];
console.log(nums.find(n => n > 10));    // 12

// findIndex — returns first matching INDEX:
console.log(nums.findIndex(n => n > 10)); // 1

// findLast / findLastIndex (ES2023):
console.log(nums.findLast(n => n > 10));      // 44
console.log(nums.findLastIndex(n => n > 10)); // 4

// some — true if AT LEAST ONE matches:
console.log(nums.some(n => n > 100));  // true

// every — true if ALL match:
console.log(nums.every(n => n > 0));   // true
console.log(nums.every(n => n > 10));  // false
```

### Array Methods — Transforming

```javascript
const numbers = [1, 2, 3, 4, 5];

// map — transforms each element, returns new array:
const doubled = numbers.map(n => n * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter — keeps elements where callback returns true:
const evens = numbers.filter(n => n % 2 === 0);
console.log(evens); // [2, 4]

// reduce — accumulates a single value:
const sum = numbers.reduce((accumulator, current) => accumulator + current, 0);
console.log(sum); // 15

// reduceRight — same but right-to-left:
const flattened = [[1,2],[3,4],[5,6]].reduceRight((acc, arr) => acc.concat(arr), []);
console.log(flattened); // [5, 6, 3, 4, 1, 2]

// flat — flattens nested arrays:
const nested = [1, [2, 3], [4, [5, 6]]];
console.log(nested.flat());    // [1, 2, 3, 4, [5, 6]] (depth 1)
console.log(nested.flat(2));   // [1, 2, 3, 4, 5, 6]   (depth 2)
console.log(nested.flat(Infinity)); // fully flatten any depth

// flatMap — map then flat(1):
const sentences = ["Hello World", "Foo Bar"];
const words = sentences.flatMap(s => s.split(" "));
console.log(words); // ["Hello", "World", "Foo", "Bar"]

// forEach — iterates, returns undefined (no chaining):
numbers.forEach((num, index) => {
  console.log(`Index ${index}: ${num}`);
});
```

### Array Methods — Sorting & Ordering

```javascript
// sort — sorts IN PLACE (mutates original!):
const letters = ["c", "a", "b"];
letters.sort();
console.log(letters); // ["a", "b", "c"]

// sort with comparator for numbers:
const nums = [10, 1, 5, 2, 100];
nums.sort((a, b) => a - b);  // ascending
console.log(nums); // [1, 2, 5, 10, 100]

nums.sort((a, b) => b - a);  // descending
console.log(nums); // [100, 10, 5, 2, 1]

// Sort objects by property:
const people = [
  { name: "Charlie", age: 25 },
  { name: "Alice", age: 30 },
  { name: "Bob", age: 20 }
];
people.sort((a, b) => a.age - b.age);
// [{Bob, 20}, {Charlie, 25}, {Alice, 30}]

// toSorted — returns NEW sorted array (non-mutating, ES2023):
const original = [3, 1, 2];
const sorted = original.toSorted((a, b) => a - b);
console.log(original); // [3, 1, 2] ← unchanged
console.log(sorted);   // [1, 2, 3]

// reverse — reverses IN PLACE:
[1, 2, 3].reverse(); // [3, 2, 1]

// toReversed — non-mutating version (ES2023):
const rev = [1, 2, 3].toReversed(); // [3, 2, 1]
```

### Array Methods — Joining & Combining

```javascript
// concat — combines arrays (non-mutating):
const a = [1, 2];
const b = [3, 4];
const c = a.concat(b, [5, 6]);
console.log(c); // [1, 2, 3, 4, 5, 6]

// join — converts to string:
console.log([1, 2, 3].join());      // "1,2,3"
console.log([1, 2, 3].join(" - ")); // "1 - 2 - 3"
console.log([1, 2, 3].join(""));    // "123"

// fill — fills slots with a value:
new Array(5).fill(0);       // [0, 0, 0, 0, 0]
[1,2,3,4,5].fill(0, 2, 4); // [1, 2, 0, 0, 5]

// copyWithin — copies part of array to another position:
[1, 2, 3, 4, 5].copyWithin(0, 3); // [4, 5, 3, 4, 5]
```

---

## 7. Objects

### Creating Objects

```javascript
// Object literal:
const person = {
  name: "Alice",
  age: 30,
  "full name": "Alice Smith", // quoted key for special chars
  greet() {                    // method shorthand
    return `Hi, I'm ${this.name}`;
  }
};

// Constructor function:
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    return `Hi, I'm ${this.name}`;
  };
}
const alice = new Person("Alice", 30);

// Object.create() — creates with prototype:
const proto = { greet() { return `Hi, I'm ${this.name}`; } };
const bob = Object.create(proto);
bob.name = "Bob";

// Factory function:
function createPerson(name, age) {
  return { name, age, greet() { return `Hi, I'm ${name}`; } };
}
```

### Accessing Properties

```javascript
const car = {
  brand: "Toyota",
  model: "Camry",
  year: 2023,
  "engine-type": "V6"
};

// Dot notation (preferred when key is valid identifier):
console.log(car.brand);   // "Toyota"
console.log(car.year);    // 2023

// Bracket notation (required for dynamic keys or special chars):
console.log(car["model"]);        // "Camry"
console.log(car["engine-type"]);  // "V6"

const key = "brand";
console.log(car[key]); // "Toyota" ← dynamic key access

// Optional chaining:
console.log(car?.features?.sunroof); // undefined (no error)
```

### Object Methods

```javascript
const obj = { a: 1, b: 2, c: 3 };

// Get keys, values, entries:
Object.keys(obj);    // ["a", "b", "c"]
Object.values(obj);  // [1, 2, 3]
Object.entries(obj); // [["a",1], ["b",2], ["c",3]]

// From entries:
const entries = [["x", 10], ["y", 20]];
Object.fromEntries(entries); // {x: 10, y: 20}

// Merge objects (assign):
const target = { a: 1 };
const source = { b: 2, c: 3 };
Object.assign(target, source); // mutates target: {a:1, b:2, c:3}

// Spread (non-mutating, preferred):
const merged = { ...target, ...source };

// Freeze — prevents modification:
const frozen = Object.freeze({ x: 1, y: 2 });
frozen.x = 99; // silently fails (or throws in strict mode)
console.log(frozen.x); // 1 ← unchanged

// Seal — allows modification but no add/delete:
const sealed = Object.seal({ x: 1 });
sealed.x = 99;   // ✅ allowed
sealed.z = 100;  // ❌ silently fails

// Check properties:
console.log("a" in obj);                  // true
console.log(obj.hasOwnProperty("a"));     // true
console.log(Object.hasOwn(obj, "a"));     // true (ES2022 — preferred)

// Property descriptors:
Object.defineProperty(obj, "id", {
  value: 42,
  writable: false,    // cannot change
  enumerable: false,  // won't show in loops
  configurable: false // cannot delete
});
```

### Property Shorthand & Computed Properties

```javascript
// Shorthand (ES6): when key name === variable name
const name = "Alice";
const age  = 30;

// Old way:
const person1 = { name: name, age: age };

// Shorthand:
const person2 = { name, age };

// Computed property names:
const prefix = "get";
const obj = {
  [prefix + "Name"]() { return this.name; }, // method: getName()
  [`${prefix}Age`]()  { return this.age; },  // method: getAge()
  ["key_" + 1]: "value1"
};
```

### Getters and Setters

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",

  // Getter — accessed like a property, not a method
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },

  // Setter — intercepts assignment
  set fullName(value) {
    const parts = value.split(" ");
    this.firstName = parts[0];
    this.lastName  = parts[1];
  }
};

console.log(person.fullName);        // "John Doe" ← no ()
person.fullName = "Jane Smith";      // calls setter
console.log(person.firstName);       // "Jane"
console.log(person.lastName);        // "Smith"
```

### Destructuring Objects

```javascript
const user = { name: "Alice", age: 30, city: "NYC", role: "admin" };

// Basic destructuring:
const { name, age } = user;
console.log(name, age); // "Alice" 30

// Rename while destructuring:
const { name: userName, city: location } = user;
console.log(userName, location); // "Alice" "NYC"

// Default values:
const { name: n, country = "USA" } = user;
console.log(country); // "USA" ← default (user has no country)

// Nested destructuring:
const data = { user: { profile: { email: "alice@mail.com" } } };
const { user: { profile: { email } } } = data;
console.log(email); // "alice@mail.com"

// Rest in destructuring:
const { name: nm, ...rest } = user;
console.log(nm);   // "Alice"
console.log(rest); // {age: 30, city: "NYC", role: "admin"}
```

---

## 8. Strings

### String Creation & Basics

```javascript
// Single, double, or template literals:
const s1 = 'hello';
const s2 = "world";
const s3 = `Hello, ${s2}!`; // template literal

// Escape characters:
"She said \"hi\""  // She said "hi"
'It\'s fine'       // It's fine
"Line1\nLine2"     // newline
"Tab\there"        // tab
"Back\\slash"      // backslash

// String length:
console.log("hello".length); // 5

// Strings are immutable — individual chars can't be changed:
let str = "hello";
str[0] = "H"; // silently ignored
console.log(str); // "hello" ← unchanged
str = "Hello";   // ✅ reassign the whole string
```

### String Methods

```javascript
const str = "  Hello, World!  ";

// Case:
str.toUpperCase();   // "  HELLO, WORLD!  "
str.toLowerCase();   // "  hello, world!  "

// Trimming:
str.trim();          // "Hello, World!"
str.trimStart();     // "Hello, World!  "
str.trimEnd();       // "  Hello, World!"

// Searching:
"Hello World".includes("World");     // true
"Hello World".startsWith("Hello");   // true
"Hello World".endsWith("World");     // true
"Hello World".indexOf("o");          // 4 (first)
"Hello World".lastIndexOf("o");      // 7 (last)
"Hello World".search(/World/);       // 6 (regex)

// Extracting:
"Hello World".slice(6);       // "World"
"Hello World".slice(6, 10);   // "Worl"
"Hello World".slice(-5);      // "World" (from end)
"Hello World".substring(6, 11); // "World" (like slice, no negatives)
"Hello World".at(0);          // "H"
"Hello World".at(-1);         // "d"
"Hello World".charAt(4);      // "o"
"Hello World".charCodeAt(0);  // 72 (char code of H)

// Replace:
"Hello World".replace("World", "JS");        // "Hello JS" (first only)
"aabba".replaceAll("a", "x");                // "xxbbx" (all)
"Hello World".replace(/[aeiou]/gi, "*");     // "H*ll* W*rld" (regex)

// Split & Join:
"a,b,c".split(",");          // ["a","b","c"]
"hello".split("");           // ["h","e","l","l","o"]
["a","b","c"].join("-");     // "a-b-c"

// Padding:
"5".padStart(3, "0");        // "005"
"hi".padEnd(5, ".");         // "hi..."

// Repeat:
"abc".repeat(3);             // "abcabcabc"

// Template literals — multiline:
const multiline = `
  Line 1
  Line 2
  Line 3
`;

// Tagged templates:
function highlight(strings, ...values) {
  return strings.reduce((result, str, i) =>
    result + str + (values[i] ? `<b>${values[i]}</b>` : ""), "");
}
const name = "Alice", age = 30;
console.log(highlight`Name: ${name}, Age: ${age}`);
// "Name: <b>Alice</b>, Age: <b>30</b>"
```

---

## 9. Numbers & Math

### Number Methods

```javascript
const num = 3.14159;

// Rounding:
num.toFixed(2);          // "3.14" (string!)
num.toPrecision(4);      // "3.142" (string!)
Math.round(3.5);         // 4
Math.floor(3.9);         // 3
Math.ceil(3.1);          // 4
Math.trunc(3.9);         // 3 (removes decimal, no rounding)
Math.trunc(-3.9);        // -3 (vs Math.floor(-3.9) = -4)

// Conversion:
(255).toString(16);      // "ff" (hex)
(10).toString(2);        // "1010" (binary)
parseInt("ff", 16);      // 255 (parse hex)
parseInt("1010", 2);     // 10 (parse binary)
Number.isInteger(3);     // true
Number.isInteger(3.1);   // false
Number.isFinite(Infinity); // false
Number.isNaN(NaN);       // true
```

### Math Object

```javascript
// Constants:
Math.PI;          // 3.14159265358979...
Math.E;           // 2.71828... (Euler's number)
Math.LN2;         // 0.693... (natural log of 2)
Math.SQRT2;       // 1.414...

// Basic:
Math.abs(-5);     // 5 (absolute value)
Math.pow(2, 10);  // 1024 (same as 2 ** 10)
Math.sqrt(16);    // 4
Math.cbrt(27);    // 3 (cube root)

// Min / Max:
Math.min(3, 1, 4, 1, 5, 9); // 1
Math.max(3, 1, 4, 1, 5, 9); // 9
Math.min(...[3, 1, 4]);      // 1 (spread array)

// Random:
Math.random();              // [0, 1) — random float
Math.floor(Math.random() * 10);     // 0-9
Math.floor(Math.random() * 10) + 1; // 1-10

// Random integer in range [min, max]:
function randomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(randomInt(1, 100)); // e.g., 47

// Logarithms:
Math.log(Math.E); // 1 (natural log)
Math.log2(8);     // 3
Math.log10(1000); // 3

// Trigonometry (in radians):
Math.sin(Math.PI / 2); // 1
Math.cos(0);            // 1
Math.tan(Math.PI / 4);  // 1

// Hypot:
Math.hypot(3, 4);  // 5 (√(3²+4²))
Math.hypot(1, 1, 1); // √3
```

---

## 10. Date & Time

### Creating Dates

```javascript
// Current date and time:
const now = new Date();
console.log(now); // e.g., 2024-01-15T10:30:00.000Z

// Specific date:
new Date("2024-01-15");             // from string
new Date("2024-01-15T10:30:00");    // with time
new Date(2024, 0, 15);              // year, month(0-indexed!), day
new Date(2024, 0, 15, 10, 30, 0);  // + hours, minutes, seconds
new Date(1705312200000);            // from Unix timestamp (ms)

// Timestamp:
Date.now(); // current Unix timestamp in milliseconds
```

### Date Methods

```javascript
const date = new Date("2024-03-15T14:30:45");

// Getters:
date.getFullYear();    // 2024
date.getMonth();       // 2 (0=Jan, 11=Dec — 0-indexed!)
date.getDate();        // 15 (day of month)
date.getDay();         // 5 (0=Sun, 6=Sat)
date.getHours();       // 14
date.getMinutes();     // 30
date.getSeconds();     // 45
date.getMilliseconds(); // 0
date.getTime();        // Unix timestamp in ms

// Setters (mutate the date):
date.setFullYear(2025);
date.setMonth(11); // December
date.setDate(25);
date.setHours(0, 0, 0, 0); // midnight

// Formatting:
date.toISOString();       // "2024-03-15T14:30:45.000Z"
date.toLocaleDateString(); // "3/15/2024" (locale-dependent)
date.toLocaleTimeString(); // "2:30:45 PM"
date.toLocaleString();    // "3/15/2024, 2:30:45 PM"
date.toString();           // long format string

// Intl.DateTimeFormat for advanced formatting:
const formatter = new Intl.DateTimeFormat("en-US", {
  year: "numeric",
  month: "long",
  day: "numeric",
  weekday: "long"
});
console.log(formatter.format(date)); // "Friday, March 15, 2024"

// Calculate difference:
const start = new Date("2024-01-01");
const end   = new Date("2024-12-31");
const diffMs   = end - start;
const diffDays = Math.floor(diffMs / (1000 * 60 * 60 * 24));
console.log(diffDays); // 365
```

---

## 11. Scope & Closures

### Scope Types

```javascript
// 1. Global Scope — accessible everywhere
var globalVar  = "I'm global (var)";
let globalLet  = "I'm global (let)";

function showGlobal() {
  console.log(globalVar); // accessible ✅
  console.log(globalLet); // accessible ✅
}

// 2. Function Scope — only inside the function
function outer() {
  var funcVar = "function scoped";
  let funcLet = "also function scoped";
  console.log(funcVar); // ✅

  function inner() {
    console.log(funcVar); // ✅ inner can see outer's vars
  }
}
// console.log(funcVar); // ❌ ReferenceError

// 3. Block Scope (ES6) — only inside {} for let/const
{
  let blockVar = "block scoped";
  const blockConst = "also block";
  var notBlock = "var ignores blocks!";
}
// console.log(blockVar); // ❌ ReferenceError
console.log(notBlock);    // ✅ "var ignores blocks!"

// 4. Lexical Scope — inner functions see outer scope
function makeCounter(start) {
  let count = start; // outer variable
  return function() {
    count++;         // inner function accesses outer variable
    return count;
  };
}
const counter = makeCounter(10);
console.log(counter()); // 11
console.log(counter()); // 12
```

### Closures

```javascript
// A closure is a function that "remembers" its outer scope
// even after the outer function has returned.

function makeAdder(x) {
  // x is "closed over" by the returned function
  return function(y) {
    return x + y; // x from outer scope is still accessible!
  };
}

const add5  = makeAdder(5);
const add10 = makeAdder(10);
console.log(add5(3));  // 8  (5 + 3)
console.log(add10(3)); // 13 (10 + 3)

// Practical: private counter
function createCounter() {
  let count = 0; // private!
  return {
    increment: () => ++count,
    decrement: () => --count,
    reset:     () => { count = 0; },
    getValue:  () => count
  };
}
const c = createCounter();
c.increment(); c.increment(); c.increment();
c.decrement();
console.log(c.getValue()); // 2
console.log(c.count);      // undefined (private!)

// Closure in loops (common gotcha):
// ❌ Problem with var:
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100); // prints 3, 3, 3!
}

// ✅ Solution 1: let (each iteration has own scope):
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100); // 0, 1, 2 ✅
}

// ✅ Solution 2: IIFE to capture value:
for (var i = 0; i < 3; i++) {
  ((j) => setTimeout(() => console.log(j), 100))(i); // 0, 1, 2 ✅
}
```

---

## 12. Hoisting

### Variable Hoisting

```javascript
// var is hoisted and initialized to undefined:
console.log(x); // undefined (NOT ReferenceError)
var x = 5;
console.log(x); // 5

// What JS actually does internally:
// var x;          // declaration hoisted to top
// console.log(x); // undefined
// x = 5;          // assignment stays in place

// let and const are hoisted but NOT initialized (Temporal Dead Zone):
// console.log(y); // ❌ ReferenceError: Cannot access 'y' before initialization
let y = 10;       // TDZ ends here
console.log(y);   // 10 ✅

// The TDZ — Temporal Dead Zone:
{
  // TDZ for 'a' starts here
  console.log(typeof a); // ❌ ReferenceError (let is in TDZ)
  let a = 1;             // TDZ ends
}
```

### Function Hoisting

```javascript
// Function DECLARATIONS are fully hoisted:
sayHi();           // ✅ Works! "Hi!"
function sayHi() {
  console.log("Hi!");
}

// Function EXPRESSIONS are NOT hoisted:
// greet(); // ❌ TypeError: greet is not a function
const greet = function() {
  console.log("Hello!");
};

// Arrow functions are NOT hoisted (same as expressions):
// add(1, 2); // ❌ ReferenceError
const add = (a, b) => a + b;

// Class declarations: hoisted but in TDZ (like let):
// const obj = new MyClass(); // ❌ ReferenceError
class MyClass {
  constructor() { this.x = 1; }
}
const obj = new MyClass(); // ✅ after declaration
```

---

## 13. The `this` Keyword

### What is `this`?

```javascript
// `this` refers to the context in which a function is called.
// Its value depends on HOW the function is called, not where it's defined.

// 1. Global context — `this` = global object (window in browser)
console.log(this); // window (browser) or {} (Node.js module)

// 2. Object method — `this` = the object before the dot
const person = {
  name: "Alice",
  greet() {
    console.log(this.name); // "Alice" ← this = person
  }
};
person.greet(); // "Alice"

// 3. Regular function — `this` = global (non-strict) or undefined (strict)
function showThis() {
  console.log(this); // window (browser) or undefined (strict mode)
}

// 4. Arrow function — `this` = enclosing lexical scope (NO own this!)
const obj = {
  name: "Bob",
  greet: () => {
    console.log(this.name); // undefined! Arrow has no own 'this'
  },
  greetCorrect() {
    const inner = () => {
      console.log(this.name); // "Bob" ← inherited from greetCorrect
    };
    inner();
  }
};

// 5. Constructor function — `this` = new object being created
function Person(name) {
  this.name = name; // this = new empty object
  this.greet = function() {
    console.log(this.name);
  };
}
const alice = new Person("Alice");
alice.greet(); // "Alice"

// 6. Class — `this` = instance
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} speaks`);
  }
}

// 7. Event listeners — `this` = element that received the event
button.addEventListener("click", function() {
  console.log(this); // the button element
});
// Arrow function doesn't work well here:
button.addEventListener("click", () => {
  console.log(this); // window (or outer this) — NOT the button!
});
```

### Binding `this` Explicitly

```javascript
function greet(greeting, punctuation) {
  return `${greeting}, ${this.name}${punctuation}`;
}

const alice = { name: "Alice" };
const bob   = { name: "Bob" };

// call — invoke immediately with specified this:
greet.call(alice, "Hello", "!");    // "Hello, Alice!"
greet.call(bob, "Hi", "?");         // "Hi, Bob?"

// apply — like call but arguments in array:
greet.apply(alice, ["Hey", "."]);   // "Hey, Alice."

// bind — returns a NEW function with bound this:
const greetAlice = greet.bind(alice);
greetAlice("Hello", "!");            // "Hello, Alice!"

// Partial application with bind:
const helloAlice = greet.bind(alice, "Hello");
helloAlice("!");   // "Hello, Alice!"
helloAlice("???"); // "Hello, Alice???"
```

---

## 14. Prototypes & Inheritance

### The Prototype Chain

```javascript
// Every object has a hidden [[Prototype]] link
// Property lookup goes up the chain until found or null

const animal = {
  breathe() { return "breathing..."; }
};

const dog = Object.create(animal); // dog's prototype = animal
dog.bark = function() { return "woof!"; };

console.log(dog.bark());    // "woof!" ← own property
console.log(dog.breathe()); // "breathing..." ← from prototype!
console.log(dog.toString()); // from Object.prototype

// Check prototype:
Object.getPrototypeOf(dog) === animal; // true
dog.__proto__ === animal;               // true (legacy, avoid)

// hasOwnProperty — only own, not inherited:
dog.hasOwnProperty("bark");    // true
dog.hasOwnProperty("breathe"); // false
```

### Constructor Function Prototype

```javascript
function Animal(name) {
  this.name = name; // instance property
}

// Methods on prototype — shared by all instances:
Animal.prototype.breathe = function() {
  return `${this.name} is breathing`;
};

Animal.prototype.toString = function() {
  return `Animal: ${this.name}`;
};

const cat = new Animal("Whiskers");
const dog = new Animal("Rex");

console.log(cat.breathe()); // "Whiskers is breathing"
console.log(dog.breathe()); // "Rex is breathing"

// Both share the SAME breathe function (memory efficient!)
console.log(cat.breathe === dog.breathe); // true

// Prototype inheritance:
function Dog(name, breed) {
  Animal.call(this, name); // call parent constructor
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // fix constructor reference

Dog.prototype.bark = function() {
  return `${this.name} says woof!`;
};

const rex = new Dog("Rex", "German Shepherd");
console.log(rex.breathe()); // inherited from Animal
console.log(rex.bark());    // own method
console.log(rex instanceof Dog);    // true
console.log(rex instanceof Animal); // true
```

---

## 15. Classes

### Class Basics (ES6)

```javascript
// Class declaration:
class Animal {
  // Constructor — runs when 'new Animal()' is called
  constructor(name, sound) {
    this.name  = name;   // public instance property
    this.sound = sound;
    this._id   = Math.random(); // convention: _ means "private"
  }

  // Instance method (on prototype):
  speak() {
    return `${this.name} says ${this.sound}`;
  }

  // Static method (on the class itself, not instances):
  static create(name, sound) {
    return new Animal(name, sound);
  }

  // Static property:
  static count = 0;

  // Getter:
  get info() {
    return `${this.name} (${this.sound})`;
  }

  // Setter:
  set info(value) {
    [this.name, this.sound] = value.split(",").map(s => s.trim());
  }
}

const cat = new Animal("Whiskers", "meow");
console.log(cat.speak()); // "Whiskers says meow"
console.log(cat.info);    // "Whiskers (meow)"
cat.info = "Luna, purr";
console.log(cat.name);    // "Luna"

// Static methods called on class, not instance:
const dog = Animal.create("Rex", "woof");
```

### Class Inheritance

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} makes a noise.`;
  }

  toString() {
    return `[Animal: ${this.name}]`;
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);      // MUST call super() before using 'this'!
    this.breed = breed;
  }

  // Override parent method:
  speak() {
    return `${this.name} barks.`;
  }

  // Call parent method with super:
  fullDescription() {
    return `${super.speak()} (${this.breed})`;
  }
}

class GuideDog extends Dog {
  constructor(name, breed, owner) {
    super(name, breed);
    this.owner = owner;
  }

  speak() {
    return `${super.speak()} (Guide dog for ${this.owner})`;
  }
}

const rex = new GuideDog("Rex", "Lab", "John");
console.log(rex.speak()); // "Rex barks. (Guide dog for John)"
console.log(rex instanceof GuideDog); // true
console.log(rex instanceof Dog);      // true
console.log(rex instanceof Animal);   // true
```

### Private Fields & Methods (ES2022)

```javascript
class BankAccount {
  // Private fields — only accessible inside the class
  #balance = 0;
  #owner;
  #transactionHistory = [];

  constructor(owner, initialDeposit) {
    this.#owner = owner;
    this.#deposit(initialDeposit);
  }

  // Private method:
  #deposit(amount) {
    if (amount <= 0) throw new Error("Invalid amount");
    this.#balance += amount;
    this.#transactionHistory.push({ type: "deposit", amount });
  }

  // Public API:
  deposit(amount) {
    this.#deposit(amount);
    return this;  // for method chaining
  }

  withdraw(amount) {
    if (amount > this.#balance) throw new Error("Insufficient funds");
    this.#balance -= amount;
    this.#transactionHistory.push({ type: "withdrawal", amount });
    return this;
  }

  get balance() {
    return this.#balance;
  }

  get history() {
    return [...this.#transactionHistory]; // return copy
  }
}

const account = new BankAccount("Alice", 1000);
account.deposit(500).withdraw(200); // method chaining
console.log(account.balance);       // 1300
// console.log(account.#balance);   // ❌ SyntaxError: private!
```

### Mixins (Multiple Inheritance Workaround)

```javascript
// JavaScript only supports single inheritance.
// Mixins let you compose behavior from multiple sources.

const Serializable = (Base) => class extends Base {
  serialize() {
    return JSON.stringify(this);
  }
  static deserialize(json) {
    return Object.assign(new this(), JSON.parse(json));
  }
};

const Timestamped = (Base) => class extends Base {
  constructor(...args) {
    super(...args);
    this.createdAt = new Date();
  }
};

const Validatable = (Base) => class extends Base {
  validate() {
    return Object.keys(this).every(key => this[key] !== null);
  }
};

class User {
  constructor(name, email) {
    this.name  = name;
    this.email = email;
  }
}

// Compose mixins:
class EnhancedUser extends Serializable(Timestamped(Validatable(User))) {
  constructor(name, email) {
    super(name, email);
  }
}

const user = new EnhancedUser("Alice", "alice@mail.com");
console.log(user.validate());   // true
console.log(user.serialize());  // JSON string
console.log(user.createdAt);    // Date object
```

---

## 16. Error Handling

### try / catch / finally

```javascript
// Syntax:
try {
  // code that might throw
} catch (error) {
  // handle the error
} finally {
  // ALWAYS runs (cleanup)
}

// Example:
function divide(a, b) {
  if (b === 0) throw new Error("Division by zero!");
  return a / b;
}

try {
  console.log(divide(10, 2)); // 5
  console.log(divide(10, 0)); // throws!
  console.log("This won't run");
} catch (error) {
  console.log("Error caught:", error.message); // "Division by zero!"
  console.log("Type:", error.name);            // "Error"
  console.log("Stack:", error.stack);          // stack trace
} finally {
  console.log("Always runs — good for cleanup");
}
```

### Error Types

```javascript
// Built-in error types:

// Error — generic base class
new Error("Something went wrong");

// TypeError — wrong type
null.property; // TypeError: Cannot read properties of null
undefined();   // TypeError: undefined is not a function

// ReferenceError — variable not defined
console.log(undeclaredVar); // ReferenceError

// SyntaxError — invalid syntax (parse time, can't be caught normally)
// eval("if ("); // SyntaxError

// RangeError — value out of valid range
new Array(-1);           // RangeError
(1.5).toFixed(101);      // RangeError

// URIError — malformed URI
decodeURIComponent("%"); // URIError

// EvalError — eval() related (rarely used)
```

### Custom Errors

```javascript
// Extending Error class:
class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = "ValidationError"; // override name
    this.field = field;
    // Fix instanceof for transpiled code:
    Object.setPrototypeOf(this, ValidationError.prototype);
  }
}

class NetworkError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.name = "NetworkError";
    this.statusCode = statusCode;
  }
}

class NotFoundError extends NetworkError {
  constructor(resource) {
    super(`${resource} not found`, 404);
    this.name = "NotFoundError";
    this.resource = resource;
  }
}

// Using custom errors:
function validateUser(user) {
  if (!user.name) throw new ValidationError("Name is required", "name");
  if (!user.email) throw new ValidationError("Email is required", "email");
  if (!user.email.includes("@")) throw new ValidationError("Invalid email", "email");
}

try {
  validateUser({ name: "Alice", email: "notanemail" });
} catch (error) {
  if (error instanceof ValidationError) {
    console.log(`Validation failed on field '${error.field}': ${error.message}`);
  } else if (error instanceof NetworkError) {
    console.log(`Network error ${error.statusCode}: ${error.message}`);
  } else {
    throw error; // rethrow unknown errors!
  }
}
```

### Error Handling Patterns

```javascript
// 1. Guard clauses (early return):
function processUser(user) {
  if (!user) throw new Error("User is required");
  if (!user.name) throw new ValidationError("Name required", "name");

  // Main logic here — we know user is valid
  return `Processing ${user.name}`;
}

// 2. Optional catch binding (ES2019):
try {
  JSON.parse("invalid json");
} catch {  // no error variable needed if not using it
  console.log("JSON parsing failed");
}

// 3. Error boundaries with async:
async function safeApiCall(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new NetworkError(response.statusText, response.status);
    }
    return await response.json();
  } catch (error) {
    if (error instanceof NetworkError) {
      // handle network issue
      return null;
    }
    throw error; // rethrow unexpected errors
  }
}

// 4. Global error handler (browser):
window.onerror = function(message, source, lineno, colno, error) {
  console.error("Global error:", message);
  return true; // prevent browser default error display
};

window.addEventListener("unhandledrejection", (event) => {
  console.error("Unhandled Promise rejection:", event.reason);
  event.preventDefault();
});
```

---

## 17. Asynchronous JavaScript

### Callbacks

```javascript
// A callback is a function passed as argument to another function
// to be called when an async operation completes.

// Simple callback:
function fetchData(url, onSuccess, onError) {
  setTimeout(() => {
    if (url.includes("error")) {
      onError(new Error("Fetch failed"));
    } else {
      onSuccess({ data: "sample data", url });
    }
  }, 1000);
}

fetchData(
  "https://api.example.com/data",
  (result) => console.log("Success:", result),
  (error)  => console.log("Error:", error.message)
);

// Callback Hell (Pyramid of Doom) — the problem with callbacks:
getData(function(a) {
  getMoreData(a, function(b) {
    getEvenMoreData(b, function(c) {
      getFinalData(c, function(d) {
        // deeply nested — hard to read, maintain, debug!
        console.log(d);
      }, handleError);
    }, handleError);
  }, handleError);
}, handleError);
// Solution: Promises or async/await
```

### setTimeout & setInterval

```javascript
// setTimeout — runs callback ONCE after delay (ms):
const timeoutId = setTimeout(() => {
  console.log("Runs after 2 seconds");
}, 2000);

// Cancel before it fires:
clearTimeout(timeoutId);

// setInterval — runs callback REPEATEDLY every interval:
let count = 0;
const intervalId = setInterval(() => {
  count++;
  console.log(`Tick ${count}`);
  if (count >= 5) {
    clearInterval(intervalId); // stop after 5 ticks
  }
}, 1000);

// requestAnimationFrame — runs before next browser repaint (~60fps):
function animate(timestamp) {
  // update animation
  element.style.left = (timestamp / 10 % 300) + "px";
  requestAnimationFrame(animate); // schedule next frame
}
requestAnimationFrame(animate);
```

---

## 18. Promises

### Creating Promises

```javascript
// A Promise represents a future value — it's either:
// pending → fulfilled (resolved) or rejected

// Syntax:
const promise = new Promise((resolve, reject) => {
  // async work here
  const success = true;
  if (success) {
    resolve("Operation succeeded!"); // fulfill with value
  } else {
    reject(new Error("Operation failed")); // reject with error
  }
});

// Simulating async:
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

function fetchUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id, name: "Alice", email: "alice@example.com" });
      } else {
        reject(new Error("Invalid user ID"));
      }
    }, 1000);
  });
}
```

### Consuming Promises

```javascript
// .then() — handles fulfillment
// .catch() — handles rejection
// .finally() — always runs

fetchUser(1)
  .then(user => {
    console.log("Got user:", user);
    return user.email; // chain — return value passes to next .then()
  })
  .then(email => {
    console.log("Email:", email);
  })
  .catch(error => {
    console.log("Error:", error.message); // catches ANY error in chain
  })
  .finally(() => {
    console.log("Done (always runs)");
  });

// Chain resolves step by step:
Promise.resolve(1)
  .then(n => n + 1)   // 2
  .then(n => n * 3)   // 6
  .then(n => n - 1)   // 5
  .then(console.log); // 5
```

### Promise Static Methods

```javascript
// Promise.resolve / Promise.reject — create already-settled promises:
Promise.resolve("value").then(console.log); // "value"
Promise.reject(new Error("fail")).catch(e => console.log(e.message)); // "fail"

// Promise.all — wait for ALL to resolve (fails if ANY rejects):
const p1 = fetch("/api/users");
const p2 = fetch("/api/posts");
const p3 = fetch("/api/comments");

const [users, posts, comments] = await Promise.all([p1, p2, p3]);
// If any fails, catches the first rejection

// Promise.allSettled — wait for ALL, get results regardless of outcome:
const results = await Promise.allSettled([p1, p2, p3]);
results.forEach(result => {
  if (result.status === "fulfilled") {
    console.log("Value:", result.value);
  } else {
    console.log("Reason:", result.reason);
  }
});

// Promise.race — resolves/rejects with FIRST settled promise:
const timeout = new Promise((_, reject) =>
  setTimeout(() => reject(new Error("Timeout!")), 5000)
);
const data = await Promise.race([fetch("/api/data"), timeout]);

// Promise.any — resolves with FIRST fulfilled (ignores rejections):
const fastest = await Promise.any([
  fetch("/api/server1"),
  fetch("/api/server2"),
  fetch("/api/server3")
]);
// Gets response from whichever server responds first
// Only rejects if ALL reject (AggregateError)
```

---

## 19. Async / Await

### Basics

```javascript
// async function always returns a Promise
// await pauses execution until Promise settles

async function fetchUser(id) {
  // await pauses here until fetch() promise settles
  const response = await fetch(`/api/users/${id}`);

  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`); // rejected promise
  }

  const user = await response.json(); // await again
  return user; // automatically wrapped in Promise.resolve(user)
}

// Consuming:
fetchUser(1)
  .then(user => console.log(user))
  .catch(error => console.log(error));

// Or with await (inside another async function):
async function main() {
  const user = await fetchUser(1);
  console.log(user);
}
```

### Error Handling with Async/Await

```javascript
// try/catch:
async function loadData() {
  try {
    const response = await fetch("/api/data");
    if (!response.ok) throw new Error(`Error: ${response.status}`);
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Failed to load:", error.message);
    return null;
  } finally {
    console.log("Fetch attempt complete");
  }
}

// Helper for cleaner error handling:
async function to(promise) {
  try {
    const result = await promise;
    return [null, result];
  } catch (error) {
    return [error, null];
  }
}

const [error, user] = await to(fetchUser(1));
if (error) {
  console.log("Error:", error.message);
} else {
  console.log("User:", user);
}
```

### Parallel vs Sequential

```javascript
// SEQUENTIAL — waits for each before starting next (slow!):
async function sequential() {
  const user  = await fetchUser(1);    // wait 1s
  const posts = await fetchPosts(1);   // then wait 1s
  const comments = await fetchComments(1); // then wait 1s
  // Total: ~3 seconds!
}

// PARALLEL — all start simultaneously (fast!):
async function parallel() {
  const [user, posts, comments] = await Promise.all([
    fetchUser(1),
    fetchPosts(1),
    fetchComments(1)
  ]);
  // Total: ~1 second (longest individual)
}

// Parallel with error handling per item:
async function parallelSafe() {
  const results = await Promise.allSettled([
    fetchUser(1),
    fetchPosts(1),
    fetchComments(1)
  ]);
  return results
    .filter(r => r.status === "fulfilled")
    .map(r => r.value);
}

// Async iteration (for await...of):
async function processStream(asyncIterable) {
  for await (const chunk of asyncIterable) {
    console.log(chunk);
  }
}
```

---

## 20. ES6+ Modern Features

### Template Literals

```javascript
const name = "Alice";
const age = 30;

// Multi-line:
const html = `
  <div class="user">
    <h1>${name}</h1>
    <p>Age: ${age}</p>
  </div>
`;

// Expressions inside ${}:
console.log(`${2 + 2}`);               // "4"
console.log(`${name.toUpperCase()}`);  // "ALICE"
console.log(`${age >= 18 ? "Adult" : "Minor"}`); // "Adult"

// Tagged template literals:
function sql(strings, ...values) {
  const query = strings.reduce((result, str, i) =>
    result + str + (values[i] !== undefined ? `$${i}` : ""), "");
  return { query, values };
}

const userId = 42;
const result = sql`SELECT * FROM users WHERE id = ${userId}`;
// { query: "SELECT * FROM users WHERE id = $1", values: [42] }
```

### Short-Circuit Evaluation Patterns

```javascript
// Default value pattern (||):
const name = userInput || "Anonymous";

// Nullish coalescing (??) — only for null/undefined:
const name2 = userInput ?? "Anonymous"; // "" would NOT trigger this

// Optional chaining with nullish coalescing:
const city = user?.address?.city ?? "Unknown";

// Short-circuit AND for conditional execution:
isLoggedIn && showDashboard();
// same as: if (isLoggedIn) showDashboard();

// Nullish assignment:
config.timeout ??= 5000; // set only if null/undefined
config.retries ||= 3;    // set if falsy
config.debug   &&= false; // unset if currently truthy
```

### Enhanced Object Literals

```javascript
const x = 10, y = 20;

// Property shorthand:
const point = { x, y }; // { x: 10, y: 20 }

// Method shorthand:
const calculator = {
  value: 0,
  add(n)      { this.value += n; return this; },
  subtract(n) { this.value -= n; return this; },
  multiply(n) { this.value *= n; return this; },
  result()    { return this.value; }
};
calculator.add(5).multiply(3).subtract(2).result(); // 13

// Computed properties:
const prefix = "get";
const obj = {
  [prefix + "Name"]() { return this.name; },
  [`${prefix}Age`]()  { return this.age; }
};

// Dynamic method names:
const actions = ["start", "stop", "reset"];
const controller = actions.reduce((obj, action) => ({
  ...obj,
  [action]() { console.log(action); }
}), {});
controller.start(); // "start"
```

---

## 21. Destructuring

### Array Destructuring

```javascript
// Basic:
const [a, b, c] = [1, 2, 3];
console.log(a, b, c); // 1 2 3

// Skip elements:
const [first, , third] = [10, 20, 30];
console.log(first, third); // 10 30

// Default values:
const [x = 0, y = 0, z = 0] = [1, 2];
console.log(x, y, z); // 1 2 0

// Rest:
const [head, ...tail] = [1, 2, 3, 4, 5];
console.log(head); // 1
console.log(tail); // [2, 3, 4, 5]

// Swap variables:
let p = 1, q = 2;
[p, q] = [q, p];
console.log(p, q); // 2 1

// From function return:
function getCoordinates() {
  return [51.5074, -0.1278]; // London
}
const [lat, lng] = getCoordinates();

// Nested:
const [[a1, a2], [b1, b2]] = [[1, 2], [3, 4]];
```

### Object Destructuring

```javascript
// Basic:
const { name, age, city } = { name: "Alice", age: 30, city: "NYC" };

// Rename:
const { name: userName, city: location } = { name: "Alice", city: "NYC" };

// Default values:
const { name: n = "Anonymous", role = "user" } = { name: "Alice" };
console.log(n, role); // "Alice" "user"

// Nested:
const {
  user: {
    profile: { email, avatar = "default.png" }
  }
} = { user: { profile: { email: "alice@mail.com" } } };
console.log(email, avatar); // "alice@mail.com" "default.png"

// Rest:
const { name: nm, ...otherProps } = { name: "Alice", age: 30, city: "NYC" };
console.log(nm);         // "Alice"
console.log(otherProps); // { age: 30, city: "NYC" }

// In function parameters:
function displayUser({ name, age, role = "user" }) {
  console.log(`${name} (${age}) — ${role}`);
}
displayUser({ name: "Alice", age: 30 }); // "Alice (30) — user"

// Mixed array + object:
const [{ name: first }, { name: second }] = [{ name: "Alice" }, { name: "Bob" }];
```

---

## 22. Spread & Rest Operators

### Spread Operator (...)

```javascript
// Spread in arrays:
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];       // [1,2,3,4,5,6]
const withExtra = [0, ...arr1, 3.5, ...arr2]; // [0,1,2,3,3.5,4,5,6]

// Copy array (shallow):
const original = [1, 2, 3];
const copy = [...original];
copy.push(4);
console.log(original); // [1,2,3] ← unchanged

// Spread in objects:
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };
const merged = { ...obj1, ...obj2 };         // {a:1, b:2, c:3, d:4}
const overridden = { ...obj1, b: 99, ...obj2 }; // {a:1, b:99, c:3, d:4}

// Clone object:
const original2 = { x: 1, y: { z: 2 } };
const shallow = { ...original2 }; // shallow clone
// shallow.y === original2.y ← same nested object reference!

// Spread in function calls:
function add(x, y, z) { return x + y + z; }
const args = [1, 2, 3];
console.log(add(...args)); // 6

// Convert string to array:
const chars = [..."hello"]; // ["h","e","l","l","o"]

// Convert Set to array:
const unique = [...new Set([1, 2, 2, 3, 3])]; // [1, 2, 3]

// Convert NodeList to array:
const elements = [...document.querySelectorAll("div")];
```

### Rest Operator (...)

```javascript
// Rest in function parameters (collects remaining into array):
function sum(first, second, ...rest) {
  console.log(first);  // 1
  console.log(second); // 2
  console.log(rest);   // [3, 4, 5]
  return first + second + rest.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4, 5); // 15

// Rest must be LAST parameter:
// function bad(...rest, last) {} // SyntaxError!

// Rest in destructuring:
const [head, second2, ...tail] = [1, 2, 3, 4, 5];
const { a, b, ...others } = { a: 1, b: 2, c: 3, d: 4 };
console.log(others); // {c: 3, d: 4}

// Difference: spread EXPANDS, rest COLLECTS
// Spread: [...array]        — used when CALLING
// Rest:   function(...args) — used when DEFINING
```

---

## 23. Modules

### ES Modules (ESM) — Modern Standard

```javascript
// ─── math.js (exporting) ───────────────────────────────────

// Named exports — can have multiple:
export const PI = 3.14159;
export function add(a, b)      { return a + b; }
export function subtract(a, b) { return a - b; }

// Export list:
const multiply = (a, b) => a * b;
const divide   = (a, b) => a / b;
export { multiply, divide };

// Rename on export:
export { multiply as mul, divide as div };

// Default export — ONE per file:
export default class Calculator {
  add(a, b)      { return a + b; }
  subtract(a, b) { return a - b; }
}

// ─── app.js (importing) ────────────────────────────────────

// Named imports:
import { PI, add, subtract } from "./math.js";

// Rename on import:
import { multiply as mul } from "./math.js";

// Import all as namespace:
import * as MathUtils from "./math.js";
MathUtils.add(1, 2);
MathUtils.PI;

// Default import (any name you want):
import Calculator from "./math.js";
import Calc       from "./math.js"; // also valid

// Mixed import:
import Calculator, { PI, add } from "./math.js";

// Dynamic import (lazy loading):
const module = await import("./math.js");
module.add(1, 2);

// In HTML:
// <script type="module" src="app.js"></script>
```

### CommonJS (Node.js)

```javascript
// ─── math.js ───────────────────────────────────────────────

// Export:
module.exports = {
  add:      (a, b) => a + b,
  subtract: (a, b) => a - b,
  PI: 3.14159
};

// Or individually:
exports.add = (a, b) => a + b;

// ─── app.js ────────────────────────────────────────────────

// Import:
const math = require("./math");
math.add(1, 2);

// Destructure:
const { add, subtract, PI } = require("./math");
```

---

## 24. DOM Manipulation

### Selecting Elements

```javascript
// Single element selectors:
document.getElementById("myId");
document.querySelector(".myClass");       // first match
document.querySelector("#id .class > p"); // CSS selector

// Multiple elements:
document.getElementsByClassName("myClass"); // HTMLCollection (live)
document.getElementsByTagName("div");        // HTMLCollection (live)
document.querySelectorAll(".myClass");       // NodeList (static)

// Relative selectors:
element.querySelector(".child");
element.closest(".ancestor");     // walk up DOM tree
element.parentElement;
element.children;                 // HTMLCollection of child elements
element.childNodes;               // NodeList including text nodes
element.firstElementChild;
element.lastElementChild;
element.nextElementSibling;
element.previousElementSibling;
```

### Modifying Elements

```javascript
const el = document.querySelector("#myElement");

// Content:
el.textContent = "New text";                   // safe, no HTML parsing
el.innerHTML = "<strong>Bold</strong>";        // parses HTML (XSS risk!)
el.innerText = "Visible text";                 // respects CSS visibility

// Attributes:
el.getAttribute("href");
el.setAttribute("href", "https://example.com");
el.removeAttribute("disabled");
el.hasAttribute("class");

// Data attributes:
// <div data-user-id="42" data-role="admin">
el.dataset.userId; // "42"
el.dataset.role;   // "admin"
el.dataset.newProp = "value"; // adds data-new-prop

// Classes:
el.classList.add("active", "highlight");
el.classList.remove("inactive");
el.classList.toggle("visible");          // add if absent, remove if present
el.classList.contains("active");         // true/false
el.classList.replace("old", "new");
el.className = "class1 class2";          // replaces all

// Styles:
el.style.color = "red";
el.style.backgroundColor = "blue";      // camelCase!
el.style.cssText = "color: red; font-size: 16px;"; // multiple at once
getComputedStyle(el).color;             // get actual computed style
```

### Creating & Inserting Elements

```javascript
// Create:
const div = document.createElement("div");
const text = document.createTextNode("Hello");

// Set properties:
div.textContent = "Hello World";
div.id = "myDiv";
div.classList.add("container");

// Insert:
parent.appendChild(child);            // add to END of parent
parent.prepend(child);               // add to BEGINNING
parent.insertBefore(new, reference); // before reference node
reference.after(element);           // after reference node
reference.before(element);          // before reference node

// insertAdjacentHTML — parse HTML string and insert:
el.insertAdjacentHTML("beforebegin", "<div>Before</div>");
el.insertAdjacentHTML("afterbegin",  "<div>First child</div>");
el.insertAdjacentHTML("beforeend",   "<div>Last child</div>");
el.insertAdjacentHTML("afterend",    "<div>After</div>");

// Remove:
el.remove();                          // remove self
parent.removeChild(child);            // remove child

// Replace:
parent.replaceChild(newChild, oldChild);
el.replaceWith(newElement);

// Clone:
const clone = el.cloneNode(true); // true = deep clone (with children)
```

---

## 25. Events

### Adding Event Listeners

```javascript
// Syntax:
element.addEventListener(event, handler, options);

const button = document.querySelector("#btn");

// Basic:
button.addEventListener("click", function(event) {
  console.log("Clicked!", event);
});

// Arrow function (note: 'this' won't refer to element!):
button.addEventListener("click", (event) => {
  console.log(event.target); // the element that triggered event
});

// Remove event listener (must use same function reference!):
function handleClick(e) {
  console.log("Clicked");
}
button.addEventListener("click", handleClick);
button.removeEventListener("click", handleClick);

// Options:
button.addEventListener("click", handler, {
  once:    true,   // auto-remove after first trigger
  capture: false,  // false=bubble (default), true=capture phase
  passive: true    // hint: won't call preventDefault (performance)
});
```

### The Event Object

```javascript
document.addEventListener("click", function(event) {
  // Target info:
  event.target;          // element that triggered the event
  event.currentTarget;   // element the listener is attached to
  event.type;            // "click"

  // Mouse events:
  event.clientX;         // X relative to viewport
  event.clientY;         // Y relative to viewport
  event.pageX;           // X relative to document
  event.pageY;           // Y relative to document
  event.button;          // 0=left, 1=middle, 2=right

  // Keyboard events:
  event.key;             // "Enter", "a", "ArrowUp"
  event.code;            // "KeyA", "Enter", "ArrowUp"
  event.ctrlKey;         // true if Ctrl held
  event.shiftKey;        // true if Shift held
  event.altKey;          // true if Alt held
  event.metaKey;         // true if Cmd (Mac) / Win key

  // Control:
  event.preventDefault();  // prevent default behavior (e.g., link navigation)
  event.stopPropagation(); // stop bubbling up the DOM
  event.stopImmediatePropagation(); // stop other handlers too
});
```

### Event Delegation

```javascript
// Instead of attaching listeners to each child,
// attach ONE listener to the parent and use event.target:

const list = document.querySelector("#todo-list");

list.addEventListener("click", function(event) {
  // event.target = the actual element clicked
  const item = event.target.closest("li"); // find nearest <li>
  if (!item) return; // clicked outside an li

  if (event.target.classList.contains("delete-btn")) {
    item.remove();
  } else if (event.target.classList.contains("complete-btn")) {
    item.classList.toggle("completed");
  }
});

// Benefits:
// ✅ Works for dynamically added elements
// ✅ Uses less memory (one handler vs many)
// ✅ Less code
```

### Common Events

```javascript
// Mouse:
"click"        // single click
"dblclick"     // double click
"mousedown"    // mouse button pressed
"mouseup"      // mouse button released
"mousemove"    // mouse moved
"mouseenter"   // mouse enters element (no bubbling)
"mouseleave"   // mouse leaves element (no bubbling)
"mouseover"    // mouse over element (bubbles)
"contextmenu"  // right click

// Keyboard:
"keydown"      // key pressed (repeats if held)
"keyup"        // key released
"keypress"     // (deprecated) character key pressed

// Form:
"submit"       // form submitted
"input"        // value changed (real-time)
"change"       // value changed and blurred
"focus"        // element focused
"blur"         // element lost focus
"reset"        // form reset

// Window/Document:
"load"         // page fully loaded
"DOMContentLoaded" // HTML parsed (faster than load)
"resize"       // window resized
"scroll"       // page/element scrolled
"beforeunload" // user about to leave

// Touch:
"touchstart"
"touchmove"
"touchend"
```

---

## 26. Fetch API & AJAX

### Basic Fetch

```javascript
// GET request:
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(response => {
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    return response.json(); // parse JSON body
  })
  .then(user => console.log(user))
  .catch(error => console.error(error));

// With async/await:
async function getUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);
    if (!response.ok) throw new Error(`HTTP ${response.status}: ${response.statusText}`);

    const contentType = response.headers.get("content-type");
    if (!contentType?.includes("application/json")) {
      throw new Error("Response is not JSON");
    }

    return await response.json();
  } catch (error) {
    console.error("Failed to fetch user:", error);
    throw error; // rethrow so caller can handle
  }
}
```

### Fetch Options (POST, PUT, DELETE)

```javascript
// POST — create resource:
async function createUser(userData) {
  const response = await fetch("/api/users", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": `Bearer ${getToken()}`
    },
    body: JSON.stringify(userData)
  });
  return response.json();
}

// PUT — replace resource:
async function updateUser(id, userData) {
  const response = await fetch(`/api/users/${id}`, {
    method: "PUT",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(userData)
  });
  return response.json();
}

// PATCH — partial update:
async function patchUser(id, changes) {
  const response = await fetch(`/api/users/${id}`, {
    method: "PATCH",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(changes)
  });
  return response.json();
}

// DELETE:
async function deleteUser(id) {
  const response = await fetch(`/api/users/${id}`, {
    method: "DELETE"
  });
  return response.status === 204; // 204 No Content = success
}

// Upload file:
async function uploadFile(file) {
  const formData = new FormData();
  formData.append("file", file);
  formData.append("filename", file.name);

  const response = await fetch("/api/upload", {
    method: "POST",
    body: formData // DON'T set Content-Type — browser does it automatically
  });
  return response.json();
}
```

### Abort Controller (Cancel Requests)

```javascript
// Cancel an ongoing fetch:
const controller = new AbortController();
const signal = controller.signal;

// Start fetch:
const fetchPromise = fetch("/api/data", { signal });

// Cancel after 5 seconds:
setTimeout(() => controller.abort(), 5000);

try {
  const data = await fetchPromise;
} catch (error) {
  if (error.name === "AbortError") {
    console.log("Fetch was cancelled");
  } else {
    throw error;
  }
}

// Pattern: cancel previous request when new one starts:
let currentController = null;

async function search(query) {
  // Cancel previous search
  if (currentController) currentController.abort();

  currentController = new AbortController();
  const { signal } = currentController;

  try {
    const response = await fetch(`/api/search?q=${query}`, { signal });
    return response.json();
  } catch (error) {
    if (error.name !== "AbortError") throw error;
  }
}
```

---

## 27. Local Storage & Session Storage

```javascript
// localStorage — persists until explicitly cleared
// sessionStorage — cleared when tab/window closes

// Both have the same API:

// Store:
localStorage.setItem("key", "string value");
localStorage.setItem("user", JSON.stringify({ name: "Alice", age: 30 }));

// Retrieve:
const value = localStorage.getItem("key");           // "string value" or null
const user  = JSON.parse(localStorage.getItem("user")); // parsed object

// Remove:
localStorage.removeItem("key");
localStorage.clear(); // remove all items

// Length & keys:
localStorage.length;  // number of items
localStorage.key(0);  // get key at index 0

// Iterate all:
for (let i = 0; i < localStorage.length; i++) {
  const key = localStorage.key(i);
  const val = localStorage.getItem(key);
  console.log(key, val);
}

// Storage helper class:
class Storage {
  static get(key, defaultValue = null) {
    try {
      const item = localStorage.getItem(key);
      return item ? JSON.parse(item) : defaultValue;
    } catch {
      return defaultValue;
    }
  }

  static set(key, value) {
    try {
      localStorage.setItem(key, JSON.stringify(value));
      return true;
    } catch {
      return false; // storage quota exceeded
    }
  }

  static remove(key) { localStorage.removeItem(key); }
  static clear()     { localStorage.clear(); }
}

// Storage event (fires in OTHER tabs when storage changes):
window.addEventListener("storage", (event) => {
  console.log(event.key);      // changed key
  console.log(event.newValue); // new value
  console.log(event.oldValue); // previous value
  console.log(event.url);      // URL of page that changed it
});
```

---

## 28. Regular Expressions

### Creating Regex

```javascript
// Literal syntax:
const regex1 = /pattern/flags;
const email  = /^[\w.-]+@[\w.-]+\.\w{2,}$/i;

// Constructor (for dynamic patterns):
const pattern = "hello";
const regex2 = new RegExp(pattern, "gi");
const dynamic = new RegExp(`^${userInput}`, "i"); // careful with special chars!
```

### Flags

```javascript
/pattern/i   // case Insensitive
/pattern/g   // Global (find all matches)
/pattern/m   // Multiline (^ and $ match line start/end)
/pattern/s   // dotAll (. matches newlines too)
/pattern/u   // Unicode
/pattern/gi  // combine flags
```

### Common Patterns

```javascript
// Characters:
/./           // any character except newline
/\d/          // digit [0-9]
/\D/          // non-digit
/\w/          // word char [a-zA-Z0-9_]
/\W/          // non-word char
/\s/          // whitespace (space, tab, newline)
/\S/          // non-whitespace
/\b/          // word boundary
/\B/          // non-word boundary

// Quantifiers:
/a*/          // 0 or more 'a'
/a+/          // 1 or more 'a'
/a?/          // 0 or 1 'a'
/a{3}/        // exactly 3 'a'
/a{2,5}/      // 2 to 5 'a'
/a{2,}/       // 2 or more 'a'
/a*?/         // non-greedy (as few as possible)

// Anchors:
/^hello/      // starts with "hello"
/world$/      // ends with "world"
/^hello world$/ // exact match

// Groups:
/(ab)+/       // capturing group
/(?:ab)+/     // non-capturing group
/(?<name>\w+)/ // named capturing group
/(a)|(b)/     // alternation (a OR b)

// Lookahead / Lookbehind:
/foo(?=bar)/  // "foo" followed by "bar" (positive lookahead)
/foo(?!bar)/  // "foo" NOT followed by "bar" (negative)
/(?<=foo)bar/ // "bar" preceded by "foo" (positive lookbehind)
/(?<!foo)bar/ // "bar" NOT preceded by "foo" (negative)
```

### Using Regex

```javascript
const text = "Hello, my email is alice@mail.com and bob123@test.org";

// test — returns boolean:
/\d+/.test("abc123"); // true
/^\d+$/.test("123");  // true (only digits)

// match — returns matches:
"hello world".match(/\w+/);   // ["hello"] (first match without g)
"hello world".match(/\w+/g);  // ["hello", "world"] (all with g)

// matchAll — returns iterator of all matches with groups:
const emailRegex = /(?<user>[\w.-]+)@(?<domain>[\w.-]+)/g;
for (const match of text.matchAll(emailRegex)) {
  console.log(match[0]);          // full match: "alice@mail.com"
  console.log(match.groups.user); // "alice"
  console.log(match.groups.domain); // "mail.com"
  console.log(match.index);       // position in string
}

// search — returns index of first match:
"hello world".search(/world/); // 6
"hello world".search(/xyz/);   // -1

// replace:
"hello world".replace(/o/g, "0");       // "hell0 w0rld"
"2024-01-15".replace(                   // reformat date
  /(\d{4})-(\d{2})-(\d{2})/,
  "$3/$2/$1"                            // using group references
); // "15/01/2024"

// Named groups in replace:
"John Smith".replace(
  /(?<first>\w+) (?<last>\w+)/,
  "$<last>, $<first>"
); // "Smith, John"

// replace with function:
"hello world".replace(/\b\w/g, char => char.toUpperCase());
// "Hello World"

// split with regex:
"one  two   three".split(/\s+/); // ["one", "two", "three"]
```

---

## 29. Iterators & Generators

### Iterators

```javascript
// An iterator is an object with a next() method that returns { value, done }

// Custom iterator:
function makeRangeIterator(start, end, step = 1) {
  let current = start;
  return {
    next() {
      if (current <= end) {
        const value = current;
        current += step;
        return { value, done: false };
      }
      return { value: undefined, done: true };
    },
    [Symbol.iterator]() { return this; } // makes it iterable!
  };
}

const range = makeRangeIterator(1, 10, 2);
console.log(range.next()); // { value: 1, done: false }
console.log(range.next()); // { value: 3, done: false }

// Use in for...of:
for (const num of makeRangeIterator(1, 5)) {
  console.log(num); // 1, 2, 3, 4, 5
}

// Spread iterable:
const arr = [...makeRangeIterator(1, 5)]; // [1, 2, 3, 4, 5]
```

### Generators

```javascript
// Generator functions use function* and yield
// They produce iterators automatically

function* counter(start = 0) {
  while (true) {
    yield start++;  // pause and return value, resume on next()
  }
}

const gen = counter(1);
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }

// Finite generator:
function* range(start, end, step = 1) {
  for (let i = start; i <= end; i += step) {
    yield i;
  }
}

for (const num of range(0, 10, 2)) {
  console.log(num); // 0, 2, 4, 6, 8, 10
}

// Two-way communication with generators:
function* calculator() {
  let result = 0;
  while (true) {
    const input = yield result; // send result, receive next input
    result += input;
  }
}

const calc = calculator();
calc.next();     // start the generator (runs until first yield)
calc.next(5);    // send 5 → result = 5
calc.next(10);   // send 10 → result = 15
calc.next(3);    // send 3 → result = 18

// Async generators (ES2018):
async function* fetchPages(baseUrl) {
  let page = 1;
  while (true) {
    const response = await fetch(`${baseUrl}?page=${page}`);
    const data = await response.json();
    if (data.length === 0) return;
    yield data;
    page++;
  }
}

for await (const page of fetchPages("/api/items")) {
  console.log(`Got ${page.length} items`);
}
```

---

## 30. Symbol, Map, Set, WeakMap, WeakSet

### Symbol

```javascript
// Symbols are unique, immutable primitive values
// Often used as unique object property keys

const id1 = Symbol("id");
const id2 = Symbol("id");
console.log(id1 === id2); // false — always unique!

// Use as object key:
const ID = Symbol("id");
const user = {
  name: "Alice",
  [ID]: 12345 // symbol key — won't show in for...in or JSON.stringify!
};
console.log(user[ID]);          // 12345
console.log(Object.keys(user)); // ["name"] — symbol not included
console.log(JSON.stringify(user)); // {"name":"Alice"} — symbol omitted

// Well-known symbols (customize built-in behavior):
class CustomArray {
  [Symbol.iterator]() {
    // make object iterable
    let i = 0;
    return { next: () => ({ value: this[i], done: i++ >= this.length }) };
  }
}

// Symbol.toPrimitive — customize type conversion:
const temperature = {
  celsius: 25,
  [Symbol.toPrimitive](hint) {
    if (hint === "number") return this.celsius;
    if (hint === "string") return `${this.celsius}°C`;
    return this.celsius;
  }
};
console.log(+temperature);    // 25
console.log(`${temperature}`); // "25°C"
```

### Map

```javascript
// Map — key-value pairs where keys can be ANY type

const map = new Map();

// Set values:
map.set("name", "Alice");
map.set(42, "the answer");
map.set(true, "boolean key");
const objKey = { id: 1 };
map.set(objKey, "object as key!");

// Get values:
map.get("name");    // "Alice"
map.get(42);        // "the answer"
map.get(objKey);    // "object as key!"
map.get({id: 1});   // undefined (different object reference!)

// Check:
map.has("name");    // true
map.size;           // 4

// Delete:
map.delete(42);

// Iterate:
for (const [key, value] of map) {
  console.log(key, "→", value);
}
map.forEach((value, key) => console.log(key, value));

// Convert:
const entries = [...map.entries()]; // [[key,val], ...]
const keys    = [...map.keys()];
const values  = [...map.values()];

// Initialize from array:
const map2 = new Map([["a", 1], ["b", 2], ["c", 3]]);

// Map vs Object:
// ✅ Map: any key type, maintains insertion order, size property, easier iteration
// ✅ Object: JSON serializable, destructuring, prototype methods available
```

### Set

```javascript
// Set — collection of UNIQUE values (no duplicates)

const set = new Set([1, 2, 3, 2, 1]); // {1, 2, 3} — duplicates removed

set.add(4);
set.add(2);  // already exists, nothing happens
set.has(3);  // true
set.size;    // 4
set.delete(1);
set.clear(); // remove all

// Iterate:
for (const value of set) {
  console.log(value);
}
set.forEach(value => console.log(value));

// Convert to array:
const arr = [...set]; // or Array.from(set)

// Remove duplicates from array:
const unique = [...new Set([1, 2, 2, 3, 3, 4])]; // [1, 2, 3, 4]

// Set operations:
const a = new Set([1, 2, 3, 4]);
const b = new Set([3, 4, 5, 6]);

const union        = new Set([...a, ...b]);        // {1,2,3,4,5,6}
const intersection = new Set([...a].filter(x => b.has(x))); // {3,4}
const difference   = new Set([...a].filter(x => !b.has(x))); // {1,2}
const symDiff      = new Set([...a, ...b].filter(x => !a.has(x) || !b.has(x))); // {1,2,5,6}
```

### WeakMap & WeakSet

```javascript
// WeakMap — keys must be objects, held WEAKLY (garbage collected when unreachable)
// WeakSet — values must be objects, held WEAKLY
// No size property, no iteration — designed for memory-safe associations

// WeakMap use case: store private data for objects:
const privateData = new WeakMap();

class User {
  constructor(name, password) {
    privateData.set(this, { password }); // tied to instance
    this.name = name;
  }
  checkPassword(input) {
    return privateData.get(this).password === input;
  }
}

const user = new User("Alice", "secret123");
user.checkPassword("secret123"); // true
// When 'user' is garbage collected, its private data is too ✅

// WeakSet use case: track which objects have been processed:
const processed = new WeakSet();

function process(obj) {
  if (processed.has(obj)) {
    console.log("Already processed");
    return;
  }
  // do work...
  processed.add(obj);
}
```

---

## 31. Proxy & Reflect

### Proxy

```javascript
// Proxy wraps an object and intercepts operations on it

// Syntax: new Proxy(target, handler)

// Validation proxy:
const validatedUser = new Proxy({}, {
  set(target, property, value) {
    if (property === "age") {
      if (typeof value !== "number") throw new TypeError("Age must be a number");
      if (value < 0 || value > 150)  throw new RangeError("Invalid age");
    }
    if (property === "name") {
      if (typeof value !== "string") throw new TypeError("Name must be a string");
      if (value.length < 2) throw new Error("Name too short");
    }
    target[property] = value;
    return true; // required for set trap
  },
  get(target, property) {
    if (!(property in target)) throw new Error(`Property "${property}" not found`);
    return target[property];
  }
});

validatedUser.name = "Alice"; // ✅
validatedUser.age  = 30;      // ✅
// validatedUser.age = -5;    // ❌ RangeError

// Logging proxy:
function createLogger(target) {
  return new Proxy(target, {
    get(obj, prop) {
      console.log(`GET ${prop}`);
      return typeof obj[prop] === "function"
        ? obj[prop].bind(obj)
        : obj[prop];
    },
    set(obj, prop, value) {
      console.log(`SET ${prop} = ${JSON.stringify(value)}`);
      obj[prop] = value;
      return true;
    }
  });
}

// Available traps:
// get, set, has (in operator), deleteProperty, apply (function calls),
// construct (new), getPrototypeOf, setPrototypeOf, ...
```

### Reflect

```javascript
// Reflect — provides methods that mirror Proxy traps
// Good practice: use Reflect in proxy handlers

const handler = {
  get(target, prop, receiver) {
    console.log(`Getting ${prop}`);
    return Reflect.get(target, prop, receiver); // default behavior
  },
  set(target, prop, value, receiver) {
    console.log(`Setting ${prop} = ${value}`);
    return Reflect.set(target, prop, value, receiver);
  }
};

// Reflect methods:
Reflect.get(obj, "name");            // obj.name
Reflect.set(obj, "name", "Alice");   // obj.name = "Alice"
Reflect.has(obj, "name");            // "name" in obj
Reflect.deleteProperty(obj, "name"); // delete obj.name
Reflect.ownKeys(obj);                // Object.keys + symbols
Reflect.apply(fn, thisArg, args);   // fn.apply(thisArg, args)
Reflect.construct(Cls, args);        // new Cls(...args)
```

---

## 32. Memory Management & Garbage Collection

### How It Works

```javascript
// JavaScript uses automatic garbage collection.
// The engine (e.g., V8) uses a Mark-and-Sweep algorithm:
// 1. Start from "roots" (global objects, current stack)
// 2. Mark all reachable objects
// 3. Sweep (delete) all unmarked objects

// Object becomes eligible for GC when no references exist:
let obj = { name: "Alice" }; // object in memory
obj = null;                   // no more references → can be collected

// Reference counting (simplified mental model):
let a = { x: 1 };
let b = a;       // 2 references to the same object
a = null;        // 1 reference remains
b = null;        // 0 references → collected
```

### Memory Leaks

```javascript
// 1. Accidental globals:
function leaky() {
  forgotVar = "I'm global!"; // no let/const/var → becomes global
}
// Fix: use "use strict" at top of file

// 2. Forgotten timers/intervals:
const data = fetchHugeDataset();
const interval = setInterval(() => {
  processData(data); // 'data' stays in memory while interval runs!
}, 1000);
// Fix: clearInterval(interval) when done!

// 3. Detached DOM nodes:
let button = document.querySelector("#btn");
const handler = () => console.log("clicked");
button.addEventListener("click", handler);

document.body.removeChild(button); // removed from DOM
// 'button' variable still holds reference → memory leak!
button.removeEventListener("click", handler);
button = null; // release reference

// 4. Closures holding large data:
function processLargeData() {
  const hugeArray = new Array(1000000).fill(0); // 1M elements

  return function() {
    // Only needs hugeArray[0], but closure captures ALL of it!
    return hugeArray[0];
  };
}
// Fix: extract only what you need:
function processLargeData2() {
  const hugeArray = new Array(1000000).fill(0);
  const firstValue = hugeArray[0]; // extract only what's needed
  // hugeArray can now be GC'd
  return function() {
    return firstValue;
  };
}

// 5. Map/Set with object keys (use WeakMap/WeakSet instead):
const cache = new Map();
const cache2 = new WeakMap(); // preferred for object-keyed caches
```

---

## 33. Design Patterns in JavaScript

### Singleton Pattern

```javascript
// Ensures only ONE instance of a class exists

class Database {
  static #instance = null;
  #connection;

  constructor(url) {
    if (Database.#instance) return Database.#instance;
    this.#connection = this.#connect(url);
    Database.#instance = this;
  }

  #connect(url) {
    console.log(`Connecting to ${url}`);
    return { url, connected: true };
  }

  query(sql) {
    return `Result of: ${sql}`;
  }

  static getInstance(url) {
    if (!Database.#instance) new Database(url);
    return Database.#instance;
  }
}

const db1 = new Database("mongodb://localhost");
const db2 = new Database("mongodb://other");
console.log(db1 === db2); // true — same instance!
```

### Observer Pattern

```javascript
// Objects subscribe to events emitted by a subject

class EventEmitter {
  #events = new Map();

  on(event, listener) {
    if (!this.#events.has(event)) this.#events.set(event, new Set());
    this.#events.get(event).add(listener);
    return () => this.off(event, listener); // returns unsubscribe fn
  }

  off(event, listener) {
    this.#events.get(event)?.delete(listener);
  }

  once(event, listener) {
    const wrapper = (...args) => {
      listener(...args);
      this.off(event, wrapper);
    };
    this.on(event, wrapper);
  }

  emit(event, ...args) {
    this.#events.get(event)?.forEach(listener => listener(...args));
  }
}

// Usage:
class Store extends EventEmitter {
  #state;
  constructor(initialState) {
    super();
    this.#state = initialState;
  }
  setState(newState) {
    const prev = this.#state;
    this.#state = { ...this.#state, ...newState };
    this.emit("change", this.#state, prev);
  }
  getState() { return { ...this.#state }; }
}

const store = new Store({ count: 0 });
const unsubscribe = store.on("change", (newState) => {
  console.log("State changed:", newState);
});
store.setState({ count: 1 }); // triggers listener
unsubscribe();                  // remove listener
```

### Factory Pattern

```javascript
// Creates objects without specifying exact class

class ShapeFactory {
  static create(type, ...args) {
    const shapes = {
      circle:    (radius)        => ({ type: "circle",    area: () => Math.PI * radius ** 2 }),
      rectangle: (width, height) => ({ type: "rectangle", area: () => width * height }),
      triangle:  (base, height)  => ({ type: "triangle",  area: () => 0.5 * base * height })
    };
    const creator = shapes[type];
    if (!creator) throw new Error(`Unknown shape: ${type}`);
    return creator(...args);
  }
}

const circle = ShapeFactory.create("circle", 5);
console.log(circle.area()); // 78.54...

const rect = ShapeFactory.create("rectangle", 10, 5);
console.log(rect.area()); // 50
```

### Module Pattern

```javascript
// Encapsulates related code and exposes public API

const ShoppingCart = (() => {
  // Private state:
  const items = [];
  let discount = 0;

  // Private helpers:
  function calculateTotal() {
    const subtotal = items.reduce((sum, item) => sum + item.price * item.qty, 0);
    return subtotal * (1 - discount);
  }

  // Public API:
  return {
    addItem(item) {
      const existing = items.find(i => i.id === item.id);
      if (existing) existing.qty++;
      else items.push({ ...item, qty: 1 });
      return this; // chainable
    },
    removeItem(id) {
      const index = items.findIndex(i => i.id === id);
      if (index !== -1) items.splice(index, 1);
      return this;
    },
    applyDiscount(percent) {
      discount = percent / 100;
      return this;
    },
    getTotal() { return calculateTotal(); },
    getItems() { return [...items]; } // return copy
  };
})();

ShoppingCart
  .addItem({ id: 1, name: "Book", price: 15 })
  .addItem({ id: 2, name: "Pen", price: 2 })
  .applyDiscount(10);
console.log(ShoppingCart.getTotal()); // 15.3
```

---

## 34. Functional Programming Concepts

### Pure Functions

```javascript
// A pure function:
// 1. Always returns same output for same input
// 2. Has NO side effects

// ❌ Impure — reads external state, modifies external data:
let tax = 0.2;
function calculateTotal(price) {
  return price * (1 + tax); // depends on external 'tax'
}

// ✅ Pure — only depends on inputs:
function calculateTotal(price, taxRate) {
  return price * (1 + taxRate); // predictable, testable
}

// ❌ Impure — mutates input:
function addItem(arr, item) {
  arr.push(item); // modifies original!
  return arr;
}

// ✅ Pure — returns new array:
function addItem(arr, item) {
  return [...arr, item]; // creates new array
}
```

### Immutability

```javascript
// Avoid mutating data — create new data instead

// ❌ Mutation:
const user = { name: "Alice", age: 30 };
user.age = 31; // mutates!

// ✅ Immutable update:
const updatedUser = { ...user, age: 31 }; // new object

// Array updates:
const numbers = [1, 2, 3, 4, 5];

// ❌ Mutation:
numbers.push(6);     // mutates
numbers[0] = 99;     // mutates

// ✅ Immutable:
const withSix  = [...numbers, 6];              // add
const without3 = numbers.filter(n => n !== 3); // remove
const updated  = numbers.map((n, i) => i === 0 ? 99 : n); // update at index

// Deep freeze for nested objects:
function deepFreeze(obj) {
  Object.getOwnPropertyNames(obj).forEach(name => {
    if (typeof obj[name] === "object" && obj[name] !== null) {
      deepFreeze(obj[name]);
    }
  });
  return Object.freeze(obj);
}
```

### Function Composition

```javascript
// Compose functions (right-to-left):
const compose = (...fns) => x => fns.reduceRight((v, fn) => fn(v), x);

// Pipe (left-to-right):
const pipe = (...fns) => x => fns.reduce((v, fn) => fn(v), x);

// Example:
const trim      = str => str.trim();
const lowercase = str => str.toLowerCase();
const words     = str => str.split(" ");
const unique    = arr => [...new Set(arr)];

const processText = pipe(trim, lowercase, words, unique);
console.log(processText("  Hello World hello JS  "));
// ["hello", "world", "js"]

// Currying — transform multi-arg function into chain of single-arg functions:
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    }
    return function(...more) {
      return curried(...args, ...more);
    };
  };
}

const add     = curry((a, b, c) => a + b + c);
const add5    = add(5);          // partial application
const add5and3 = add5(3);        // another partial
console.log(add5and3(2));        // 10
console.log(add(1)(2)(3));       // 6
console.log(add(1, 2)(3));       // 6
```

### Array Functional Methods Chaining

```javascript
const data = [
  { name: "Alice", age: 28, dept: "Engineering", salary: 90000 },
  { name: "Bob",   age: 35, dept: "Marketing",   salary: 65000 },
  { name: "Carol", age: 32, dept: "Engineering", salary: 95000 },
  { name: "Dave",  age: 25, dept: "Marketing",   salary: 55000 },
  { name: "Eve",   age: 41, dept: "Engineering", salary: 110000 }
];

// Functional chain: filter → map → sort → reduce
const result = data
  .filter(emp => emp.dept === "Engineering")      // only engineers
  .filter(emp => emp.age < 40)                   // under 40
  .map(emp => ({ ...emp, bonus: emp.salary * 0.1 })) // add bonus
  .sort((a, b) => b.salary - a.salary)           // sort by salary desc
  .reduce((acc, emp) => {                         // build summary
    return {
      ...acc,
      total: acc.total + emp.salary,
      employees: [...acc.employees, emp.name]
    };
  }, { total: 0, employees: [] });

console.log(result);
// { total: 185000, employees: ["Carol", "Alice"] }
```

---

## 35. Performance Best Practices

### General JavaScript Performance

```javascript
// 1. Cache DOM queries:
// ❌ Slow — queries DOM every loop iteration:
for (let i = 0; i < document.querySelectorAll("li").length; i++) {
  document.querySelectorAll("li")[i].style.color = "red";
}

// ✅ Fast — query once, cache result:
const listItems = document.querySelectorAll("li");
for (const item of listItems) {
  item.style.color = "red";
}

// 2. Debounce — delay execution until calls stop:
function debounce(fn, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}

const searchInput = document.querySelector("#search");
searchInput.addEventListener("input", debounce((e) => {
  fetchSearchResults(e.target.value); // only fires after typing stops
}, 300));

// 3. Throttle — limit to max once per interval:
function throttle(fn, interval) {
  let lastCall = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= interval) {
      lastCall = now;
      return fn.apply(this, args);
    }
  };
}

window.addEventListener("scroll", throttle(() => {
  updateProgressBar(); // max once per 100ms
}, 100));

// 4. Memoization — cache expensive function results:
function memoize(fn) {
  const cache = new Map();
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

const expensiveFn = memoize((n) => {
  // simulate heavy computation
  return n * n;
});

expensiveFn(42); // computed
expensiveFn(42); // returned from cache immediately!

// 5. Use DocumentFragment for batch DOM updates:
// ❌ Slow — causes reflow for each append:
const list = document.querySelector("#list");
for (let i = 0; i < 1000; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  list.appendChild(li); // reflow each time!
}

// ✅ Fast — one reflow at the end:
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  fragment.appendChild(li); // no reflow yet
}
list.appendChild(fragment); // one reflow at the end ✅

// 6. Use web workers for heavy computation:
const worker = new Worker("heavy-task.js");
worker.postMessage({ data: hugeDataset });
worker.onmessage = (e) => {
  console.log("Result:", e.data); // UI stays responsive!
};

// 7. Lazy loading with Intersection Observer:
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src; // load only when visible
      observer.unobserve(img);
    }
  });
});

document.querySelectorAll("img[data-src]").forEach(img => {
  observer.observe(img);
});
```

### Code Quality Tips

```javascript
// Use strict mode:
"use strict"; // catches silent errors, prevents bad patterns

// Prefer const > let > var:
const MAX = 100;    // can never be reassigned
let count = 0;      // may be reassigned

// Early return (guard clauses):
function process(user) {
  if (!user) return null;
  if (!user.isActive) return null;
  // main logic — no deep nesting!
  return processActiveUser(user);
}

// Meaningful names:
// ❌ Bad:
const d = new Date();
const arr = users.filter(u => u.a > 18);

// ✅ Good:
const currentDate = new Date();
const adultUsers  = users.filter(user => user.age > 18);

// Avoid magic numbers:
// ❌ Bad:
if (age > 18) { ... }
setTimeout(fn, 86400000);

// ✅ Good:
const LEGAL_AGE    = 18;
const ONE_DAY_MS   = 24 * 60 * 60 * 1000;
if (age > LEGAL_AGE) { ... }
setTimeout(fn, ONE_DAY_MS);
```

---

## 📖 Quick Reference Cheat Sheet

```
VARIABLES:        var (avoid) | let (mutable) | const (immutable)
TYPES:            number | string | boolean | null | undefined | symbol | bigint | object
TYPE CHECK:       typeof x | Array.isArray(x) | x instanceof Class
FUNCTIONS:        declaration | expression | arrow | IIFE | generator
ASYNC:            callbacks → Promises → async/await
EQUALITY:         Always use === (strict), avoid == (loose)
LOOPS:            for | while | do-while | for...of (iterables) | for...in (keys)
ARRAY METHODS:    map | filter | reduce | find | some | every | flat | flatMap
OBJECT METHODS:   keys | values | entries | assign | freeze | create | fromEntries
ERROR HANDLING:   try / catch / finally | throw new Error()
CLASSES:          class | constructor | extends | super | static | #privateField
MODULES:          export / import (ESM) | module.exports / require (CJS)
PATTERNS:         Singleton | Observer | Factory | Module | Proxy
FUNCTIONAL:       Pure functions | Immutability | Curry | Compose | Pipe
```

---

*📘 JavaScript Complete Reference — covers ES5 through ES2023+*
*Happy Coding! 🚀*
