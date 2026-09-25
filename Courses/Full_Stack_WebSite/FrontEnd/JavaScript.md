# 🚀 Advanced JavaScript (JS) Guide & Projects

A practical JavaScript learning repository containing documentation, examples, and small interactive projects covering JavaScript fundamentals, DOM manipulation, arrays, functions, validation, CRUD operations, calculators, and interactive web applications.

---

## 📚 Table of Contents

- [JavaScript Integration](#-javascript-integration)
- [Student CRUD Management](#-student-crud-management)
- [Product Profit Calculator](#-product-profit-calculator)
- [JavaScript Calculator](#-javascript-calculator)
- [Array Operations](#-array-operations)
- [Conditional Arithmetic Calculator](#-conditional-arithmetic-calculator)
- [Multi-Operator Calculator](#-multi-operator-calculator)
- [Interactive Profile Card](#-interactive-profile-card)
- [Multi-Counter Application](#-multi-counter-application)
- [Interactive State Click Tracker](#-interactive-state-click-tracker)
- [Main JavaScript Concepts](#-main-javascript-concepts)
- [Learning Progression](#-learning-progression)
- [Suggested Project Structure](#-suggested-project-structure)

---

# 🟨 JavaScript Integration

JavaScript can be added to an HTML page in three main ways.

## 1. Inline JavaScript

JavaScript is written directly inside an HTML attribute.

```html
<button onclick="alert('Welcome to JavaScript!')">
    Quick Alert Trigger
</button>
```

### Use Case

Useful for very small examples and learning event handling.

---

## 2. Internal JavaScript

JavaScript can be written inside a `<script>` tag.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Internal JavaScript</title>
</head>

<body>

    <h1>JavaScript Example</h1>

    <script>
        alert("Welcome to JavaScript!");
    </script>

</body>
</html>
```

---

## 3. External JavaScript

JavaScript can be placed in a separate `.js` file.

### HTML

```html
<script src="js/app.js"></script>
```

### JavaScript

```javascript
alert("Welcome to JavaScript!");
```

### Why External JavaScript?

- Cleaner HTML
- Better project organization
- Easier maintenance
- JavaScript files can be reused
- Recommended for larger projects

---

# 👨‍🎓 Student CRUD Management

A simple Student Management System demonstrating CRUD operations.

CRUD means:

- Create
- Read
- Update
- Delete

---

## Student Data

```javascript
let students = [
    {
        name: "ali",
        age: 22,
        job: "eng"
    }
];

table(students);
```

---

## Display Students

```javascript
function table(data) {

    document.getElementById('tbl').innerHTML = "";

    let id = 0;

    data.forEach(element => {

        document.getElementById('tbl').innerHTML += `
            <tr>

                <td>${++id}</td>

                <td>${element.name}</td>

                <td>${element.age}</td>

                <td>${element.job}</td>

                <td>
                    <button onclick="edit(${id})">
                        Edit
                    </button>
                </td>

                <td>
                    <button onclick="del(${id})">
                        Delete
                    </button>
                </td>

            </tr>
        `;
    });
}
```

---

## Add Student

```javascript
function add() {

    let name =
        document.getElementById('name').value;

    let age =
        document.getElementById('age').value;

    let job =
        document.getElementById('job').value;

    if (name && age && job) {

        let student = {
            name,
            age,
            job
        };

        students.push(student);

        table(students);

        document.getElementById('name').value = "";
        document.getElementById('age').value = "";
        document.getElementById('job').value = "";

    } else {

        alert("Please enter data");
    }
}
```

---

## Delete Student

```javascript
function del(id) {

    id = id - 1;

    let temp = [];

    for (const key in students) {

        if (key != id) {

            temp.push(students[key]);
        }
    }

    students = temp;

    table(students);
}
```

---

## Edit Student

```javascript
function edit(id) {

    id = id - 1;

    document.getElementById('name').value =
        students[id].name;

    document.getElementById('age').value =
        students[id].age;

    document.getElementById('job').value =
        students[id].job;

    document.getElementById('btn').innerHTML =
        `<button onclick="update(${id})">
            Update
        </button>`;
}
```

---

## Update Student

```javascript
function update(id) {

    let name =
        document.getElementById('name').value;

    let age =
        document.getElementById('age').value;

    let job =
        document.getElementById('job').value;

    if (name && age && job) {

        let student = {
            name,
            age,
            job
        };

        students[id] = student;

        table(students);

        document.getElementById('name').value = "";
        document.getElementById('age').value = "";
        document.getElementById('job').value = "";

    } else {

        alert("Please enter data");
    }

    document.getElementById('btn').innerHTML =
        `<button onclick="add()">Add</button>`;
}
```

---

# 💰 Product Profit Calculator

This project calculates the profit of a product and dynamically adds the product to a table.

```javascript
function CalculateProfit() {

    let nameProduct =
        document.getElementById('name-product').value;

    let buyprice =
        document.getElementById('buy-price').value;

    let sellprice =
        document.getElementById('sell-price').value;

    let imgproduct =
        document.getElementById('img-product').value;


    if (
        nameProduct === "" ||
        buyprice === "" ||
        sellprice === "" ||
        imgproduct === ""
    ) {

        document.getElementById('error-box')
            .style.display = "flex";

        return;
    }


    let Profit = sellprice - buyprice;


    if (Profit > 0) {

        let newrow =
            document.createElement('tr');


        newrow.innerHTML = `
            <th>${nameProduct}</th>

            <th>
                <img src="${imgproduct}" width="100">
            </th>

            <th>${buyprice}</th>

            <th>${sellprice}</th>

            <th>${Profit}</th>
        `;


        document.getElementById('product-table')
            .getElementsByTagName("tbody")[0]
            .appendChild(newrow);


        document.getElementById('product-name')
            .innerText = nameProduct;


        document.getElementById('product-img')
            .innerHTML =
            `<img src="${imgproduct}" width="100">`;


        document.getElementById('buyprice')
            .innerText = buyprice;


        document.getElementById('sellprice')
            .innerText = sellprice;


        document.getElementById('profit')
            .innerText = Profit;
    }
}


function closeError() {

    document.getElementById('error-box')
        .style.display = "none";
}
```

---

# 🧮 JavaScript Calculator

A simple calculator using JavaScript.

```javascript
function appendValue(value) {

    document.getElementById('display').value += value;
}


function ClearDisplay() {

    document.getElementById('display').value = "";
}


function calculate() {

    try {

        document.getElementById('display').value =
            eval(
                document.getElementById('display').value
            );

    } catch (error) {

        alert('The operation is invalid');
    }
}
```

> ⚠️ `eval()` is useful for learning but should generally be avoided with untrusted input because it executes JavaScript code.

---

# 🚗 Array Operations

This project demonstrates common JavaScript array operations.

```javascript
const cars = [
    "bmw",
    "marcedes",
    "Volvo"
];


document.write(`
    <div class="container">
`);


document.write(`
    <h1>🚗 Cars Array</h1>
`);


document.write(`
    <div class="card">
        <span class="label">
            Original Array
        </span>

        <span class="value">
            ${cars}
        </span>
    </div>
`);


document.write(`
    <div class="card">
        <span class="label">
            car[2]
        </span>

        <span class="value">
            ${cars[2]}
        </span>
    </div>
`);


cars.push("kia");


document.write(`
    <div class="card">
        <span class="label">
            After push("kia")
        </span>

        <span class="value">
            ${cars}
        </span>
    </div>
`);


cars.pop();


document.write(`
    <div class="card">
        <span class="label">
            After pop()
        </span>

        <span class="value">
            ${cars}
        </span>
    </div>
`);


cars.shift();


document.write(`
    <div class="card">
        <span class="label">
            After shift()
        </span>

        <span class="value">
            ${cars}
        </span>
    </div>
`);


cars.unshift("audi");


document.write(`
    <div class="card">
        <span class="label">
            After unshift("audi")
        </span>

        <span class="value">
            ${cars}
        </span>
    </div>
`);


document.write(`
    <div class="card">
        <span class="label">
            Array Length
        </span>

        <span class="value">
            ${cars.length}
        </span>
    </div>
`);


document.write(`
    <div class="card">
        <span class="label">
            Include "Volvo"?
        </span>

        <span class="value">
            ${cars.includes("Volvo")}
        </span>
    </div>
`);


const car = [
    [],
    [3, 4]
];


document.write(`
    <div class="card">
        <span class="label">
            car[1][1]
        </span>

        <span class="value">
            ${car[1][1]}
        </span>
    </div>
`);


document.write(`
    </div>
`);
```

---

# ➕ Conditional Arithmetic Calculator

This project uses `prompt()` and conditions to perform arithmetic operations.

```javascript
let num1 =
    prompt("Please enter num1");


let num2 =
    prompt("Please enter num2");


let op =
    prompt(
        "Please enter the operation from (+,-,*,/,**,%)"
    );


num1 = parseInt(num1);

num2 = parseInt(num2);


document.write(`
    <table>

        <tr>
            <th>Number 1</th>
            <th>Operation</th>
            <th>Number 2</th>
            <th>Result</th>
        </tr>
`);


if (op == "+") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>+</td>
            <td>${num2}</td>
            <td>${num1 + num2}</td>
        </tr>
    `);

}

else if (op == "-") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>-</td>
            <td>${num2}</td>
            <td>${num1 - num2}</td>
        </tr>
    `);

}

else if (op == "*") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>*</td>
            <td>${num2}</td>
            <td>${num1 * num2}</td>
        </tr>
    `);

}

else if (op == "/") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>/</td>
            <td>${num2}</td>
            <td>${num1 / num2}</td>
        </tr>
    `);

}

else if (op == "**") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>**</td>
            <td>${num2}</td>
            <td>${num1 ** num2}</td>
        </tr>
    `);

}

else if (op == "%") {

    document.write(`
        <tr>
            <td>${num1}</td>
            <td>%</td>
            <td>${num2}</td>
            <td>${num1 % num2}</td>
        </tr>
    `);

}

else {

    document.write(`
        <tr>
            <td colspan="4">
                Invalid Operation
            </td>
        </tr>
    `);
}


document.write(`</table>`);
```

---

# 🧮 Multi-Operator Calculator

This version performs several operations at the same time.

```javascript
let val1 =
    prompt("Enter the first number");


let val2 =
    prompt("Enter the second number");


val1 = parseInt(val1);

val2 = parseInt(val2);


document.write(`
    <table>

        <tr>
            <th>Operation</th>
            <th>Result</th>
        </tr>

        <tr>
            <td>Addition</td>
            <td>${val1 + val2}</td>
        </tr>

        <tr>
            <td>Subtraction</td>
            <td>${val1 - val2}</td>
        </tr>

        <tr>
            <td>Multiplication</td>
            <td>${val1 * val2}</td>
        </tr>

        <tr>
            <td>Division</td>
            <td>${val1 / val2}</td>
        </tr>

        <tr>
            <td>Power</td>
            <td>${val1 ** val2}</td>
        </tr>

        <tr>
            <td>Modulus</td>
            <td>${val1 % val2}</td>
        </tr>

    </table>
`);
```

---

# 👤 Interactive Profile Card

This project collects user information using `prompt()` and `confirm()`.

```javascript
let name =
    prompt("Enter your name");


let age =
    prompt("Enter your age");


let image =
    prompt("Enter your image URL");


let address =
    prompt("Enter your address");


let gender =
    confirm("Are you male?");


document.write(`

    <div class="profile-card">

        <img
            src="${image}"
            alt="Profile Image"
        >

        <h2>
            ${name}
        </h2>

        <p>
            Age: ${age}
        </p>

        <p>
            Address: ${address}
        </p>

        <p>
            ${gender ? "♂ Male" : "♀ Female"}
        </p>

    </div>

`);
```

---

# 🔢 Multi-Counter Application

A simple application containing multiple independent counters.

```javascript
let count = [0, 0, 0];


function increase(x) {

    document.getElementById(
        "counter" + x
    ).innerHTML =
        ++count[x - 1];
}


function reset(x) {

    count[x - 1] = 0;

    document.getElementById(
        "counter" + x
    ).innerHTML =
        count[x - 1];
}
```

### Example HTML

```html
<div>

    <h2 id="counter1">
        0
    </h2>

    <button onclick="increase(1)">
        Increase
    </button>

    <button onclick="reset(1)">
        Reset
    </button>

</div>


<div>

    <h2 id="counter2">
        0
    </h2>

    <button onclick="increase(2)">
        Increase
    </button>

    <button onclick="reset(2)">
        Reset
    </button>

</div>


<div>

    <h2 id="counter3">
        0
    </h2>

    <button onclick="increase(3)">
        Increase
    </button>

    <button onclick="reset(3)">
        Reset
    </button>

</div>
```

---

# 🖱️ Interactive State Click Tracker

This project changes the displayed message depending on the number of clicks.

```javascript
let i = 0;


function change(x) {

    i++;


    if (i < 3) {

        document.getElementById("name")
            .innerHTML =
            "Please enter more than 5";

        document.getElementById("name")
            .style.color =
            "red";

    }

    else if (i < 5) {

        document.getElementById("name")
            .innerHTML =
            "You are close 5";

        document.getElementById("name")
            .style.color =
            "green";

    }

    else {

        document.getElementById("name")
            .innerHTML =
            x;

        document.getElementById("name")
            .style.color =
            "orange";
    }
}
```

---

# 🧠 Main JavaScript Concepts Used

## 1. Variables

Variables store data.

```javascript
let name = "Mohamed";

let age = 21;

const country = "Egypt";
```

### `let`

Used when the value may change.

```javascript
let count = 0;

count = 1;
```

### `const`

Used when the variable should not be reassigned.

```javascript
const cars = ["BMW", "Volvo"];
```

---

# 2. Data Types

JavaScript supports several common data types.

```javascript
let name = "Mohamed";       // String

let age = 21;              // Number

let isStudent = true;      // Boolean

let value = null;          // Null

let x;                     // Undefined

let student = {            // Object
    name: "Mohamed",
    age: 21
};

let numbers = [1, 2, 3];   // Array
```

---

# 3. Objects

Objects store related data as key-value pairs.

```javascript
let student = {

    name: "Ali",

    age: 22,

    job: "Engineer"
};
```

Accessing properties:

```javascript
student.name;

student.age;

student.job;
```

---

# 4. Arrays

Arrays store multiple values.

```javascript
let cars = [
    "BMW",
    "Mercedes",
    "Volvo"
];
```

Access an item:

```javascript
cars[0];
```

Result:

```text
BMW
```

---

# 5. Array Methods

## push()

Adds an item to the end.

```javascript
cars.push("Kia");
```

---

## pop()

Removes the last item.

```javascript
cars.pop();
```

---

## shift()

Removes the first item.

```javascript
cars.shift();
```

---

## unshift()

Adds an item to the beginning.

```javascript
cars.unshift("Audi");
```

---

## includes()

Checks whether a value exists.

```javascript
cars.includes("Volvo");
```

Returns:

```text
true
```

or

```text
false
```

---

## length

Returns the number of elements.

```javascript
cars.length;
```

---

# 6. Multidimensional Arrays

An array can contain other arrays.

```javascript
const car = [
    [],
    [3, 4]
];
```

Accessing:

```javascript
car[1][1];
```

Result:

```text
4
```

---

# 7. Functions

Functions group reusable code.

```javascript
function sayHello() {

    alert("Hello");
}
```

Call the function:

```javascript
sayHello();
```

---

# 8. Function Parameters

Functions can receive data.

```javascript
function increase(x) {

    console.log(x);
}
```

Call:

```javascript
increase(5);
```

Here:

```text
x = 5
```

---

# 9. Conditional Statements

Used to make decisions.

```javascript
if (age >= 18) {

    console.log("Adult");

}

else {

    console.log("Minor");
}
```

Multiple conditions:

```javascript
if (op == "+") {

    // Addition

}

else if (op == "-") {

    // Subtraction

}

else {

    // Invalid operation
}
```

---

# 10. Comparison Operators

```javascript
==
```

Equal value.

```javascript
===
```

Equal value and type.

```javascript
!=
```

Not equal.

```javascript
>
```

Greater than.

```javascript
<
```

Less than.

```javascript
>=
```

Greater than or equal.

```javascript
<=
```

Less than or equal.

---

# 11. Logical Operators

### AND

```javascript
&&
```

Example:

```javascript
if (name && age && job) {

    // Valid
}
```

All conditions must be truthy.

---

### OR

```javascript
||
```

Example:

```javascript
if (age < 18 || age > 60) {

    // Condition
}
```

At least one condition must be true.

---

### NOT

```javascript
!
```

Example:

```javascript
if (!name) {

    alert("Name is required");
}
```

---

# 12. Ternary Operator

A short version of `if/else`.

```javascript
gender
    ? "♂ Male"
    : "♀ Female";
```

Equivalent to:

```javascript
if (gender) {

    "♂ Male";

} else {

    "♀ Female";
}
```

---

# 13. Loops

## for Loop

```javascript
for (
    let i = 0;
    i < 5;
    i++
) {

    console.log(i);
}
```

---

# 14. for...in

Used to iterate over object properties or array indexes.

```javascript
for (const key in students) {

    console.log(
        students[key]
    );
}
```

---

# 15. forEach()

Used to execute code for every array element.

```javascript
students.forEach(element => {

    console.log(element.name);

});
```

---

# 🌐 DOM Manipulation

DOM means:

**Document Object Model**

JavaScript uses the DOM to interact with HTML elements.

---

# 16. getElementById()

Find an HTML element using its ID.

```javascript
document.getElementById("name");
```

Example:

```javascript
let name =
    document.getElementById("name").value;
```

---

# 17. value

Used to get the value entered into an input.

HTML:

```html
<input id="name">
```

JavaScript:

```javascript
let name =
    document.getElementById("name").value;
```

---

# 18. innerHTML

Used to read or replace HTML content.

```javascript
document.getElementById("box")
    .innerHTML =
    "<h1>Hello</h1>";
```

It can also insert dynamic HTML.

```javascript
element.innerHTML = `
    <p>Hello Mohamed</p>
`;
```

---

# 19. innerText

Used to change text.

```javascript
document.getElementById("name")
    .innerText =
    "Mohamed";
```

---

# 20. style

Used to change CSS through JavaScript.

```javascript
document.getElementById("name")
    .style.color =
    "red";
```

---

# 21. createElement()

Creates a new HTML element.

```javascript
let row =
    document.createElement("tr");
```

---

# 22. appendChild()

Adds an element to another element.

```javascript
table.appendChild(row);
```

---

# 📝 User Input

## prompt()

Displays a dialog and gets user input.

```javascript
let name =
    prompt("Enter your name");
```

The result is normally returned as a string.

---

# 23. parseInt()

Converts a string to an integer.

```javascript
let age =
    parseInt(
        prompt("Enter your age")
    );
```

Example:

```javascript
"25"
```

becomes:

```javascript
25
```

---

# 24. confirm()

Displays a Yes/No style confirmation.

```javascript
let gender =
    confirm("Are you male?");
```

The result is:

```javascript
true
```

or:

```javascript
false
```

---

# 🧩 Template Literals

Template literals use backticks.

```javascript
let name = "Mohamed";

let message = `
    Hello ${name}
`;
```

`${}` allows JavaScript variables or expressions to be inserted into strings.

Example:

```javascript
let age = 21;

document.write(`
    <h1>
        Age: ${age}
    </h1>
`);
```

---

# 🔄 CRUD

CRUD stands for:

| Operation | Meaning |
|---|---|
| Create | Add new data |
| Read | Display data |
| Update | Modify existing data |
| Delete | Remove data |

The Student Management project demonstrates all four operations.

---

# ✅ Form Validation

Validation checks whether the user entered the required information.

```javascript
if (name && age && job) {

    // Continue

} else {

    alert("Please enter data");
}
```

A more explicit validation example:

```javascript
if (
    name === "" ||
    age === "" ||
    job === ""
) {

    alert("Please fill all fields");

    return;
}
```

---

# 🛡️ Error Handling

JavaScript provides `try/catch` for handling runtime errors.

```javascript
try {

    // Code that may fail

}

catch (error) {

    console.log(error);
}
```

Example:

```javascript
try {

    let result = eval(expression);

}

catch (error) {

    alert("Invalid operation");
}
```

---

# ⚠️ eval()

`eval()` executes a string as JavaScript code.

Example:

```javascript
eval("2 + 5");
```

Result:

```text
7
```

It is used in the calculator project for learning purposes.

However, using `eval()` with untrusted user input is generally unsafe and should be avoided in production applications.

---

# 🖱️ Events

Events allow JavaScript to respond to user actions.

Example:

```html
<button onclick="increase(1)">
    Increase
</button>
```

The `onclick` event runs the JavaScript function when the button is clicked.

Other common events:

```text
onclick
onchange
oninput
onsubmit
onmouseover
onkeydown
```

---

# 🔢 Increment Operator

```javascript
++count
```

Increases the value by one.

Example:

```javascript
let count = 0;

++count;
```

Result:

```text
1
```

---

# ➗ JavaScript Arithmetic Operators

| Operator | Operation |
|---|---|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `**` | Power |
| `%` | Modulus |

Examples:

```javascript
10 + 5;   // 15

10 - 5;   // 5

10 * 5;   // 50

10 / 5;   // 2

2 ** 3;   // 8

10 % 3;   // 1
```

---

# 🏗️ Suggested Project Structure

```text
JavaScript/
│
├── README.md
│
├── 01-JavaScript-Basics/
│   ├── index.html
│   └── app.js
│
├── 02-Student-CRUD/
│   ├── index.html
│   ├── style.css
│   └── app.js
│
├── 03-Product-Profit-Calculator/
│   ├── index.html
│   ├── style.css
│   └── app.js
│
├── 04-Calculator/
│   ├── index.html
│   ├── style.css
│   └── app.js
│
├── 05-Array-Operations/
│   └── app.js
│
├── 06-Conditional-Calculator/
│   └── app.js
│
├── 07-Multi-Operator-Calculator/
│   └── app.js
│
├── 08-Profile-Card/
│   └── app.js
│
├── 09-Multi-Counter/
│   ├── index.html
│   └── app.js
│
└── 10-Interactive-State/
    ├── index.html
    └── app.js
```

---

# 📈 Learning Progression

The projects follow a gradual learning path:

```text
JavaScript Basics
        ↓
Variables & Data Types
        ↓
Operators
        ↓
Conditions
        ↓
Arrays & Objects
        ↓
Functions
        ↓
Loops
        ↓
DOM Manipulation
        ↓
Events
        ↓
Forms & Validation
        ↓
Dynamic HTML
        ↓
CRUD Operations
        ↓
Interactive Applications
```

---

# 🎯 Skills Practiced

Through these projects, I practiced:

- JavaScript Fundamentals
- Variables
- Data Types
- Operators
- Conditional Statements
- Ternary Operator
- Functions
- Parameters
- Arrays
- Array Methods
- Objects
- Multidimensional Arrays
- Loops
- `for...in`
- `forEach()`
- DOM Manipulation
- `getElementById()`
- `innerHTML`
- `innerText`
- `style`
- `createElement()`
- `appendChild()`
- User Input
- `prompt()`
- `confirm()`
- `parseInt()`
- Template Literals
- Events
- Form Validation
- Error Handling
- `try/catch`
- CRUD Operations
- Dynamic Tables
- Dynamic UI
- Calculations
- Interactive Applications
- Basic State Management

---

# 🚀 Learning Outcome

These projects helped build a practical understanding of JavaScript before moving into larger frontend applications and frameworks such as React.

The main focus was not only learning syntax, but also understanding how JavaScript can:

- Store and manipulate data
- Process user input
- Modify HTML dynamically
- Respond to user actions
- Validate forms
- Build CRUD applications
- Create interactive interfaces
- Work with arrays and objects
- Control application state

---

# 👨‍💻 Author

**Mohamed**

Computer Engineering Student | Cybersecurity Learner | Frontend Developer

### Focus Areas

- JavaScript
- React
- Frontend Development
- Cybersecurity
- Penetration Testing
- Linux
- Problem Solving

---

⭐ If this documentation helped you, consider giving the repository a star.
