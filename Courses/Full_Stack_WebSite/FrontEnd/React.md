# ⚛️ React.js Master Documentation & Projects

A practical React.js documentation and learning guide covering environment setup, project creation, components, JSX, CSS integration, NPM packages, routing, Axios, JSON Server, and essential React Hooks.

This documentation focuses on understanding how React works through practical examples and small projects.

---

## 📚 Table of Contents

- [Environment Setup](#-environment-setup)
- [Creating a React Application](#-creating-a-react-application)
- [Project Structure](#-project-structure)
- [Cleaning the Default React Project](#-cleaning-the-default-react-project)
- [JSX Components](#-jsx-components)
- [Component Naming](#-component-naming)
- [CSS in React](#-css-in-react)
- [NPM Packages](#-npm-packages)
- [React Router](#-react-router)
- [Custom Development Port](#-custom-development-port)
- [React Hooks](#-react-hooks)
  - [useState](#-usestate)
  - [useEffect](#-useeffect)
  - [useParams](#-useparams)
- [Axios](#-axios)
- [JSON Server](#-json-server)
- [Fetching Products](#-fetching-products)
- [Fetching a Single Product](#-fetching-a-single-product)
- [React Learning Progression](#-react-learning-progression)

---

# ⚙️ Environment Setup

Before creating a React application, install:

- Node.js
- Git
- Visual Studio Code

Verify Node.js and NPM:

```bash
node -v
npm -v
```

Then :

```bash
npm install -g node-gyp
```

---

# 🏗️ Creating a React Application

Create a React application using Create React App:

```bash
npx create-react-app my-app-name
```

Move into the project:

```bash
cd my-app-name
```

Open the project in VS Code:

```bash
code .
```

Start the development server:

```bash
npm start
```

The application will normally run on:

```text
http://localhost:3000
```

---

# 📁 Project Structure

A basic React project contains:

```text
my-app-name/
│
├── public/
│   └── index.html
│
├── src/
│   ├── App.js
│   ├── index.js
│   └── ...
│
├── package.json
├── package-lock.json
└── README.md
```

---

# 🧹 Cleaning the Default React Project

Create React App provides several example files that are not always needed.

For a simple learning project, unnecessary files can be removed.

The important files are:

```text
public/
└── index.html

src/
├── App.js
└── index.js
```

---

## `public/index.html`

The HTML page contains the root element:

```html
<div id="root"></div>
```

React uses this element as the main mounting point for the application.

---

# `src/App.js`

A clean starting point:

```jsx
function App() {
    return (
        <div>
        </div>
    );
}

export default App;
```

---

# `src/index.js`

With modern React:

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(
    document.getElementById('root')
);

root.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>
);
```

---

# 🧩 JSX Components

React applications are divided into reusable components.

Example:

```jsx
function Nav() {

    return (
    <>
        <nav>
            <h1>My Website</h1>
        </nav>
    </>
    );
}

export default Nav;
```

Then import it into `App.js`:

```jsx
import Nav from './Nav';

function App() {

    return (
    <>
      <Nav />
    </>
    );
}

export default App;
```

---

# 🏷️ Component Naming

React component names should start with a capital letter.

Correct:

```text
Nav.jsx
Home.jsx
Menu.jsx
Footer.jsx
Product.jsx
```

Example:

```jsx
function Nav() {
    return (
    <>
      <h1>Navigation</h1>
    </>
    );
}
```

Incorrect:

```jsx
function nav() {
    return (
    <>
      <h1>Navigation</h1>
    </>
    );
}
```

Using capitalized names helps React distinguish custom components from normal HTML elements.

---

# 🧩 Creating Components with VS Code

The **ES7+ React/Redux/React-Native snippets** extension can generate React component templates.

For example:

```text
rfce
```

then press:

```text
Enter
```

This can generate a functional component structure.

Example:

```jsx
import React from 'react';

function Nav() {

    return (
        <div>

        </div>
    );
}

export default Nav;
```

---

# 🎨 CSS in React

Each component can have its own CSS file.

Example:

```text
src/
├── Nav.jsx
└── Nav.css
```

---

## `Nav.css`

```css
.navbar-brand {
    color: crimson;
    font-weight: bold;
}
```

---

## `Nav.jsx`

```jsx
import React from 'react';
import "./Nav.css";

function Nav() {

    return (
        <nav className="navbar-brand">

            <h1>
                Website Navigation Banner Header
            </h1>

        </nav>
    );
}

export default Nav;
```

The CSS file is imported into the component:

```jsx
import "./Nav.css";
```

---

# 📦 NPM Packages

React projects can use external packages.

---

## React Router

Install:

```bash
npm install react-router-dom
```

Used to create different routes/pages.

Example:

```text
/
 /menu
 /details/:id
 /login
 /admin/dashboard
```

---

## Axios

Install:

```bash
npm install axios
```

Axios is used to communicate with APIs.

Example:

```jsx
import axios from "axios";

axios.get("http://localhost:5000/products");
```

---

## JSON Server

Install:

```bash
npm install json-server
```

JSON Server can create a simple fake REST API from a `db.json` file.

Example:

```json
{
    "products": [
        {
            "id": 1,
            "name": "Pizza",
            "price": 150
        }
    ]
}
```

---

# 🌐 React Router

React Router allows the application to display different components based on the URL.

Example:

```jsx
import { BrowserRouter,Routes,Route } from "react-router-dom";

function App() {

return (
<>
        <BrowserRouter>

            <Routes>

                <Route
                    path="/"
                    element={<Home />}
                />

                <Route
                    path="/menu"
                    element={<Menu />}
                />

                <Route
                    path="/details/:id"
                    element={<Details />}
                />

            </Routes>

        </BrowserRouter>
</>
);
}
```

---

# 🔗 Dynamic Routes

A route can contain a dynamic parameter:

```text
/details/:id
```

For example:

```text
/details/1
/details/2
/details/10
```

The `id` changes depending on the URL.

This is where `useParams()` becomes useful.

---

# 🖥️ Custom Development Port

If port `3000` is already being used, another port can be selected.

## Windows

```bash
set PORT=5000 && npm start
```

## macOS / Linux

```bash
PORT=5000 npm start
```

---

# 🧠 React Hooks

Hooks are functions provided by React that allow functional components to use React features such as state and side effects.

The main hooks used in these projects are:

```text
useState
useEffect
useParams
```

They each solve a different problem.

---

# 🔵 useState()

## What is `useState()`?

`useState()` is used when a component needs to **store data that can change**.

For example:

```jsx
const [products, setProducts] = useState([]);
```

Here we have two things:

```text
products
```

The current value.

And:

```text
setProducts
```

The function used to change the value.

The initial value is:

```text
[]
```

which means an empty array.

---

## Basic Example

```jsx
import { useState } from "react";

function App() {

    const [name, setName] = useState("");

return (
<>
        <div>

            <h1>
                {name}
            </h1>

            <button
                onClick={() =>
                    setName("Mohamed")
                }
            >
                Change Name
            </button>

        </div>
</>
);
}
```

Initially:

```text
name = ""
```

After clicking the button:

```text
name = "Mohamed"
```

React automatically re-renders the component.

---

# 🔵 Why Do We Use `useState()`?

Because the UI often depends on changing data.

Examples:

```jsx
const [products, setProducts] = useState([]);

const [loading, setLoading] = useState(true);

const [error, setError] = useState("");

const [count, setCount] = useState(0);
```

Each one stores a different piece of state.

---

# 🔵 `useState()` with API Data

Suppose the API returns products.

We can store them:

```jsx
const [products, setProducts] = useState([]);
```

Then after receiving the API response:

```jsx
setProducts(result.data);
```

The flow becomes:

```text
API
 ↓
result.data
 ↓
setProducts()
 ↓
products
 ↓
React re-renders
 ↓
Products appear on screen
```

---

# 🟢 useEffect()

## What is `useEffect()`?

`useEffect()` is used to execute code when a component performs a **side effect**.

A very common example is:

```text
Fetching data from an API
```

For example:

```jsx
useEffect(() => {

    getData();

}, []);
```

The empty array:

```jsx
[]
```

means the effect runs after the component mounts.

---

# 🟢 Why Do We Use `useEffect()`?

Imagine this:

```jsx
function Menu() {

    const getData = async () => {
        let result = await axios.get("http://localhost:5000/products");
        setProducts(result.data);
    };

    getData();

    return (...);
}
```

The function would run every time the component renders.

This can cause repeated API requests.

Instead:

```jsx
useEffect(() => {

    getData();

}, []);
```

React runs the effect after the component renders.

With:

```jsx
[]
```

the effect is intended to run once on mount.

---

# 🟢 useEffect() Dependency Array

The dependency array controls when the effect runs.

### Empty Array

```jsx
useEffect(() => {

    // Runs after mount

}, []);
```

---

### With Dependency

```jsx
useEffect(() => {

    // Runs when id changes

}, [id]);
```

If:

```text
id = 1
```

and later becomes:

```text
id = 2
```

the effect runs again.

---

# 🟣 useParams()

## What is `useParams()`?

`useParams()` is used with React Router to get dynamic values from the URL.

Suppose we have:

```jsx
<Route path="/details/:id" element={<Details />}/>
```

If the user visits:

```text
/details/5
```

then:

```jsx
const { id } = useParams();
```

* OR

```jsx
const data = useParams();
let id = data.id
```

gives:

```text
id = 5
```

---

# 🟣 Why Do We Need `useParams()`?

Because we may want to request one specific item.

For example:

```text
/products/1
/products/2
/products/3
```

The ID changes.

So instead of writing:

```jsx
axios.get("http://localhost:5000/products/1");
```

we can use:

```jsx
const data = useParams();
let id = data.id

axios.get(`http://localhost:5000/products/${id}`);
```

Now the same component can work with:

```text
/products/1
/products/2
/products/3
/products/10
```

---

# 🔥 useState + useEffect + useParams

These three hooks are especially useful together.

Consider this route:

```jsx
<Route path="/details/:id" element={<Details />}/>
```

The user opens:

```text
/details/5
```

First:

```jsx
const { id } = useParams();
```

* OR

```jsx
const data = useParams();
let id = data.id
```

gets:

```text
5
```

Then:

```jsx
useEffect(() => {

    getData();

}, [id]);
```

runs the API request.

Then:

```jsx
setProduct(result.data);
```

stores the product.

Finally:

```jsx
{product.name}
```

displays the product.

The complete flow is:

```text
URL
 ↓
/details/5
 ↓
useParams()
 ↓
id = 5
 ↓
useEffect()
 ↓
Axios GET
 ↓
API
 ↓
result.data
 ↓
setProduct()
 ↓
useState()
 ↓
React re-render
 ↓
Product displayed
```

---

# 🌐 Axios

Axios is an HTTP client used to communicate with APIs.

Install:

```bash
npm install axios
```

Import:

```jsx
import axios from "axios";
```

---

# 📥 GET Request

To get data:

```jsx
let result = await axios.get("http://localhost:5000/products");
```

The API response is stored in:

```jsx
result
```

The actual returned data is:

```jsx
result.data
```

---

# 📥 Getting All Products

Example:

```jsx
import React, { useEffect, useState } from "react";

import axios from "axios";


function Menu() {

    const [products, setProducts] = useState([]);

    const getData = async () => {
        let result = await axios.get("http://localhost:5000/products");
        setProducts(result.data);
    };


    useEffect(() => {

        getData();

    }, []);


return (
<>
        <div>

            {products.map(product => (

                <div key={product.id}>

                    <h2>
                        {product.name}
                    </h2>

                    <p>
                        {product.price}
                    </p>

                </div>

            ))}

        </div>
</>
);
}

export default Menu;
```

---

# 🔎 Getting One Product

Suppose the route is:

```jsx
<Route path="/details/:id" element={<Details />}/>
```

Then:

```jsx
import React, { useEffect,useState } from "react";

import {
    useParams
} from "react-router-dom";

import axios from "axios";


function Details() {

    const data = useParams();
    let id = data.id
    const [product, setProduct] = useState(null);

    const getData = async () => {
        let result = await axios.get(`http://localhost:5000/products/${id}`);
        setProduct(result.data);
    };


    useEffect(() => {

        getData();

    }, [id]);


return (
<>
        <div>

            {product && (

                <div>

                    <h1>
                        {product.name}
                    </h1>

                    <p>
                        Price: {product.price}
                    </p>

                    <p>
                        {product.description}
                    </p>

                </div>

            )}

        </div>
</>
);
}

export default Details;
```

---

# 🧩 Understanding the Details Example

## Step 1 — Get the ID

```jsx
const { id } = useParams();
```

If the URL is:

```text
/details/7
```

then:

```text
id = 7
```

---

## Step 2 — Create State

```jsx
const [product, setProduct] = useState(null);
```

Initially:

```text
product = null
```

because we haven't received the API data yet.

---

## Step 3 — Create API Function

```jsx
const getData = async () => {
    let result = await axios.get(`http://localhost:5000/products/${id}`);
    setProduct(result.data);
};
```

The request becomes:

```text
http://localhost:5000/products/7
```

if:

```text
id = 7
```

---

## Step 4 — Run the Function

```jsx
useEffect(() => {

    getData();

}, [id]);
```

The function runs after the component loads.

It will also run again if the `id` changes.

---

## Step 5 — Store the Result

```jsx
setProduct(result.data);
```

The returned product is stored in:

```text
product
```

---

## Step 6 — Display the Product

```jsx
{product && (

    <h1>
        {product.name}
    </h1>

)}
```

The `&&` ensures that React does not try to access:

```jsx
product.name
```

while `product` is still `null`.

---

# 🔄 API Request Lifecycle

A typical React API request follows this pattern:

```text
Component Loads
      ↓
useEffect()
      ↓
API Function
      ↓
Axios
      ↓
API / JSON Server
      ↓
Response
      ↓
result.data
      ↓
setState()
      ↓
React Re-render
      ↓
Display Data
```

---

# ⏳ Loading State

A loading state can be used while waiting for the API.

```jsx
const [loading, setLoading] = useState(true);
```

Then:

```jsx
useEffect(() => {

    const getData = async () => {

        setLoading(true);

        let result =
            await axios.get(
                "http://localhost:5000/products"
            );

        setProducts(result.data);

        setLoading(false);
    };

    getData();

}, []);
```

Display:

```jsx
if (loading) {

    return <h2>Loading...</h2>;
}
```

---

# ❌ Error Handling

API requests can fail.

Use `try/catch`:

```jsx
const [error, setError] =
    useState("");


const getData = async () => {

    try {

        let result =
            await axios.get(
                "http://localhost:5000/products"
            );

        setProducts(result.data);

    } catch (error) {

        setError(
            "Failed to load products"
        );
    }
};
```

Display the error:

```jsx
if (error) {

    return (
        <h2>
            {error}
        </h2>
    );
}
```

---

# 🗄️ JSON Server

JSON Server allows us to create a simple REST API without building a backend.

Example:

```text
db.json
```

```json
{
    "products": [
        {
            "id": 1,
            "name": "Pizza",
            "price": 150,
            "description": "Cheese Pizza"
        },
        {
            "id": 2,
            "name": "Burger",
            "price": 120,
            "description": "Beef Burger"
        }
    ]
}
```

Start JSON Server:

```bash
npx json-server --watch db.json --port 5000
```

The API becomes:

```text
http://localhost:5000/products
```

One product:

```text
http://localhost:5000/products/1
```

---

# 🔗 React + Axios + JSON Server

The complete architecture:

```text
React
  ↓
Axios
  ↓
JSON Server
  ↓
db.json
```

For example:

```jsx
axios.get(
    "http://localhost:5000/products"
);
```

JSON Server returns:

```json
[
    {
        "id": 1,
        "name": "Pizza",
        "price": 150
    }
]
```

Axios receives it:

```jsx
result.data
```

Then React stores it:

```jsx
setProducts(result.data);
```

Then React displays it.

---

# 📊 Hook Comparison

| Hook | Purpose | Example |
|---|---|---|
| `useState()` | Store changing data | Products, user, counter |
| `useEffect()` | Run side effects | API requests |
| `useParams()` | Get dynamic URL values | Product ID |

---

# 🔥 Practical Example

A complete product details component:

```jsx
import React, { useEffect, useState } from "react";

import { useParams } from "react-router-dom";

import axios from "axios";


function Details() {

    const data = useParams();
    let id = data.id

    const [product, setProduct] = useState([]);


    const [loading, setLoading] = useState(true);


    const [error, setError] = useState("");


    useEffect(() => {

        const getData = async () => {

            try {

                setLoading(true);

                let result =
                    await axios.get(
                        `http://localhost:5000/products/${id}`
                    );

                setProduct(result.data);

            } catch (err) {

                setError(
                    "Failed to load product"
                );

            } finally {

                setLoading(false);
            }
        };


        getData();

    }, [id]);


    if (loading) {

        return (
            <h2>
                Loading...
            </h2>
        );
    }


    if (error) {

        return (
            <h2>
                {error}
            </h2>
        );
    }


return (
<>
        <div>

            {product && (

                <div>

                    <h1>
                        {product.name}
                    </h1>

                    <p>
                        Price: {product.price}
                    </p>

                    <p>
                        {product.description}
                    </p>

                </div>
            )}

        </div>
</>
);
}


export default Details;
```

---

# 🧠 React Hooks Summary

## `useState`

Used to store data that changes.

```jsx
const [products, setProducts] = useState([]);
```

Think:

```text
useState = Store Data
```

---

## `useEffect`

Used to execute side effects such as API requests.

```jsx
useEffect(() => {

    getData();

}, []);
```

Think:

```text
useEffect = Run Code
```

---

## `useParams`

Used to extract parameters from the URL.

```jsx
const { id } = useParams();
```

* OR

```jsx
const data = useParams();
let id = data.id
```

Think:

```text
useParams = Get Data From URL
```

---

# 🧠 The Three Hooks Together

```text
useParams
    ↓
Get ID from URL
    ↓
useEffect
    ↓
Run API Request
    ↓
Axios
    ↓
Receive Data
    ↓
useState
    ↓
Store Data
    ↓
React Re-renders
    ↓
Display Data
```

This pattern is one of the most important patterns used in the React projects in this repository.

---

# 📈 React Learning Progression

The learning path used in these projects:

```text
React Basics
      ↓
JSX
      ↓
Components
      ↓
Props
      ↓
CSS
      ↓
Events
      ↓
useState
      ↓
React Router
      ↓
useParams
      ↓
useEffect
      ↓
Axios
      ↓
JSON Server
      ↓
REST APIs
      ↓
CRUD Applications
      ↓
Admin Dashboards
      ↓
Real React Applications
```

---

# 🎯 Skills Practiced

Through these React projects, I practiced:

- React Fundamentals
- JSX
- Functional Components
- Component Reusability
- CSS Integration
- NPM
- React Router
- Dynamic Routes
- `useState`
- `useEffect`
- `useParams`
- Axios
- REST APIs
- JSON Server
- API Requests
- Loading States
- Error Handling
- Dynamic Rendering
- Array `.map()`
- CRUD Concepts
- Component-Based Architecture
- Dynamic Product Pages
- Admin Dashboard Concepts

---

# 👨‍💻 Author

**Mohamed**

Computer Engineering Student | Cybersecurity Learner | Frontend Developer

### Focus Areas

- React
- JavaScript
- Frontend Development
- Cybersecurity
- Penetration Testing
- Linux
- Problem Solving

---

⭐ If this documentation helped you, consider giving the repository a star.
