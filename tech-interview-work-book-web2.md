# Web Module Questions

## Modern JS

### 1., What is ECMAScript? What is the difference between Javascript & ECMAScript?

-   JavaScript implements with environment-specific features, while ECMAScript is a standardized specification ensuring compatibility across implementations and settings.

**ECMAScript (ES)** is a standardized scripting language specification on which **JavaScript** is based.

**Difference:**

-   **ECMAScript** is the specification (set of rules).
-   **JavaScript** is the implementation (actual programming language following ECMAScript).
-   Think of ECMAScript as the recipe (standard) and JavaScript as the cooked dish (implementation).

JavaScript extends ECMAScript with additional features like DOM manipulation. :rocket:

---

### 2., Explain the concept of "block scoping" introduced in ES6. How does it differ from function scoping?

### **Block Scoping (ES6) vs. Function Scoping**

**Block scoping** (with `let` and `const`) restricts variable access to the block `{}` where it is declared, whereas **function scoping** (with `var`) allows access throughout the entire function.

#### **Key Differences**

| Feature          | Function Scoping (`var`)                             | Block Scoping (`let` & `const`)                                                 |
| ---------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Scope**        | Limited to the **function** where it's declared.     | Limited to the **block `{}` (if, loops, etc.)** where it's declared.            |
| **Lifetime**     | Exists throughout the **entire function execution**. | Exists **only within the block** and is **destroyed** after the block executes. |
| **Hoisting**     | **Hoisted** but initialized as `undefined`.          | **Hoisted**, but in a **Temporal Dead Zone (TDZ)** until initialized.           |
| **Redefinition** | Can be re-declared in the same function.             | Cannot be re-declared in the same block.                                        |

#### **Example**

```js
function test() {
    if (true) {
        var x = 10; // Function-scoped (accessible outside block)
        let y = 20; // Block-scoped (only inside this block)
    }
    console.log(x); // ✅ Works (10)
    console.log(y); // ❌ ReferenceError (y is block-scoped)
}
test();
```

### 3., What are template literals in ES6 and how do they improve string manipulation in JavaScript?

**Template literals**, introduced in ES6, use backticks (`` ` ``) instead of quotes, allowing for **easier string manipulation** in JavaScript.

### Key Benefits:

-   **String Interpolation:** Embed variables and expressions using `${}`

```javascript
let name = "Jack";
console.log(`Hello, ${name}!`); // Hello, Jack!
```

-   **Multi-line Strings:** No need for `\n` or concatenation

```javascript
let message = `This is
a multi-line string.`;
```

-   **Expression Evaluation:** Directly evaluate expressions

```javascript
let a = 10,
    b = 20;
console.log(`Sum: ${a + b}`); // Sum: 30
```

-   **Tagged Templates:** Process strings with functions

```javascript
function tag(strings, value) {
    return `${strings[0]}${value.toUpperCase()}`;
}
console.log(tag`Hello, ${"jack"}!`); // Hello, JACK!
```

### 4., Explain the concept of "destructuring assignment" in ES6. How does it simplify variable assignment and object/array manipulation.

-   **Destructuring assignment** is an ES6 feature that allows unpacking values from arrays or properties from objects into distinct variables in a concise way.

#### Example with Arrays:

```javascript
const numbers = [1, 2, 3];
const [a, b, c] = numbers;
console.log(a, b, c); // 1 2 3
```

#### Example with Objects:

```javascript
const person = { name: "Jack", age: 25 };
const { name, age } = person;
console.log(name, age); // Jack 25
```

### 5., What is the "spread operator" in ES6 and how can it be used to manipulate arrays and objects more effectively?

The **spread operator (`...`)** allows expanding arrays or objects into individual elements, making them easier to manipulate.

#### Example with Arrays:

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1]; // Creates a new copy
console.log(arr2); // [1, 2, 3]
```

```javascript
const arrA = [1, 2];
const arrB = [3, 4];
const merged = [...arrA, ...arrB];
console.log(merged); // [1, 2, 3, 4]
```

#### Example with Objects:

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };
console.log(obj2); // { a: 1, b: 2, c: 3 }
```

```javascript
const objA = { name: "Jack" };
const objB = { age: 25 };
const person = { ...objA, ...objB };
console.log(person); // { name: "Jack", age: 25 }
```

### 6., How does ES6 introduce the concept of "default function parameters"? Provide an example of using default parameters in a function.

S6 introduces **default function parameters**, allowing functions to assign default values to parameters when no argument is provided. This helps prevent `undefined` errors and reduces the need for manual checks.

---

#### Example with a Single Parameter:

```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Guest!
greet("Jack"); // Output: Hello, Jack!
```

#### Example with Multiple Parameters:

```javascript
function calculatePrice(price, tax = 0.1) {
    return price + price * tax;
}

console.log(calculatePrice(100)); // 110 (default tax applied)
console.log(calculatePrice(100, 0.2)); // 120 (custom tax applied)
```

### 7., Explain the concept of "modules" introduced in ES6. How do they improve code organization and reusability in JavaScript?

## What Are ES6 Modules?

ES6 introduced **modules**, allowing JavaScript code to be split into reusable files. This improves **organization, maintainability, and performance**.

### Key Features:

-   **Encapsulation** – Limits scope of variables and functions.
-   **Reusability** – Share code across files.
-   **Better Maintainability** – Encourages structured code.
-   **Static Imports/Exports** – Optimizes performance.

## Exporting in ES6

Modules can export functions, objects, or variables.

**Named Export:**

```javascript
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

### 8., Compare the CommonJS and ES6 "modules". What are the differences?

### 1. Overview

JavaScript uses **modules** for organizing code.

-   **CommonJS (CJS)** → Used in **Node.js**.
-   **ES6 Modules (ESM)** → Standard for **modern JavaScript** (browsers & Node.js).

### 2. Key Differences

| Feature            | CommonJS (CJS)                     | ES6 Modules (ESM)                        |
| ------------------ | ---------------------------------- | ---------------------------------------- |
| **Syntax**         | `require()` / `module.exports`     | `import` / `export`                      |
| **Execution**      | **Synchronous** (loads at runtime) | **Asynchronous** (loads at compile time) |
| **Tree Shaking**   | ❌ No                              | ✅ Yes (removes unused code)             |
| **Environment**    | Node.js                            | Browsers & Node.js                       |
| **File Extension** | `.js`                              | `.js` or `.mjs`                          |

## 3. Syntax Comparison

**CommonJS:**

```javascript
// Export
module.exports.add = (a, b) => a + b;
// Import
const math = require("./math.js");
console.log(math.add(5, 3));
```

**ES6 Modules**

```javascript
// Export
export const add = (a, b) => a + b;
// Import
import { add } from "./math.js";
console.log(add(5, 3));
```

### 9., What are higher-order functions in JavaScript?

A **higher-order function (HOF)** is a function that **takes another function as an argument** or **returns a function**.

🔹 **Why use HOFs?**  
They make code **more reusable, readable, and functional**.

### Passing a Function:

```javascript
function greet(name, callback) {
    return callback(name);
}

console.log(greet("Alice", (name) => `Hello, ${name}!`));
```

### Returning a Function:

```javascript
function multiplyBy(factor) {
    return (num) => num * factor;
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

### 10., Explain the purpose and functionality of the map function in JavaScript. How does it differ from the filter and reduce functions?

-   The **`map`** function in JavaScript creates a **new array** by applying a callback function to each element of an existing array.

### **Example:**

```js
const nums = [1, 2, 3];
const squared = nums.map((n) => n * n); // [1, 4, 9]
```

### **Differences:**

-   ✅ **`map`** → Transforms each element, returns a new array.
-   ✅ **`filter`** → Returns a new array with elements that pass a condition.
-   ✅ **`reduce`** → Reduces array to a single value (e.g., sum, product).

-   🚀 **`map` is great for transformations!**

---

### 11., How can the filter function be used to selectively extract elements from an array based on a given condition? Provide an example where the filter function is used to create a new array with only the elements that meet the specified criteria.

-   The **`filter`** function in JavaScript creates a **new array** containing only elements that satisfy a given condition.

### **Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
const evens = numbers.filter((n) => n % 2 === 0); // [2, 4, 6]
```

-   ✅ Keeps elements that meet the condition.
-   ✅ Returns a new array without modifying the original.

-   🚀 **Great for filtering data dynamically!**

---

### 12., What is the role of the reduce function in JavaScript? How can it be used to aggregate or combine the elements of an array into a single value? Provide an example where the reduce function is used to calculate a cumulative sum or find the maximum value in an array.

-   The **`reduce`** function in JavaScript processes an array and returns a **single value** by applying a reducer function.

### **Example 1: Cumulative Sum**

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, n) => acc + n, 0); // 10
```

### **Example 2: Find Maximum**

```js
const nums = [5, 12, 8, 21];
const max = nums.reduce((acc, n) => Math.max(acc, n), nums[0]); // 21
```

-   ✅ **Used for sums, max/min, averages, etc.**
-   🚀 **Powerful for data aggregation!**

---

## Fetch

### 1., How does a query string parameter in a URL contribute to web application functionality? Explain how query string parameters are typically used to pass data between web pages or APIs.

-   A query string parameter in a URL helps pass data between web pages or APIs by appending key-value pairs after a ?. They allow dynamic content rendering, filtering, searching, and tracking user actions. For example, example.com/products?category=shoes&page=2 enables retrieving specific data without modifying the URL structure. APIs use them to filter, sort, or paginate responses efficiently. 🚀

---

### 2., What is the purpose and functionality of the fetch function in JavaScript?

-   The `fetch` function in JavaScript is used to **make HTTP requests** to servers. It returns a **Promise** that resolves to a `Response` object, allowing you to retrieve data from APIs, send data, or interact with web services asynchronously. It supports **GET, POST, PUT, DELETE**, and more. Example:

```js
fetch("https://api.example.com/data")
    .then((response) => response.json())
    .then((data) => console.log(data))
    .catch((error) => console.error("Error:", error));
```

-   This makes it essential for **fetching API data** dynamically in web applications. 🚀

---

### 3., Explain the syntax of the fetch function and how it handles asynchronous operations. Compare and contrast the syntax of making HTTP requests using fetch with async/await versus the syntax using .then() and .catch(). What are the key differences and benefits of using the async/await syntax in terms of code structure and readability?

-   The **`fetch`** function in JavaScript is used to make HTTP requests and returns a **Promise** that resolves to a `Response` object.

### **Basic Syntax:**

```js
fetch(url, options)
    .then((response) => response.json()) // Parse JSON
    .then((data) => console.log(data))
    .catch((error) => console.error(error));
```

### **Using `async/await` (More Readable & Clean)**

```js
async function getData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
getData();
```

### **Key Differences:**

-   ✅ **`.then().catch()`** → Uses chained promises, can get messy with nesting.
-   ✅ **`async/await`** → Looks synchronous, easier to read & debug.
-   🚀 **`async/await` improves code structure and readability!**

---

### 4., What is asynchronicity in JavaScript? Name some typical use cases when asynchronicity is needed.

-   **Asynchronicity** in JavaScript allows tasks to execute **without blocking** the main thread, enabling non-blocking operations.

### **Typical Use Cases:**

✅ **Fetching data from APIs** (`fetch`, `Axios`).  
✅ **Handling user input/events** (`setTimeout`, `setInterval`).  
✅ **Reading/writing files** (Node.js `fs` module).  
✅ **Database queries** (MongoDB, Firebase).  
✅ **WebSockets & real-time updates** (chat apps, live notifications).

-   🚀 **Ensures smooth performance without freezing the UI!**

---

### 5., How can you handle the response received from a fetch request?

### Handling Fetch Responses

The `fetch()` function returns a **Promise** that resolves to a `Response` object. Use `.json()`, `.text()`, or `.blob()` to process the data.

### Example: Handling JSON Response

```javascript
fetch("https://api.example.com/data")
    .then((response) => response.json()) // Convert to JSON
    .then((data) => console.log("Data:", data)) // Handle data
    .catch((error) => console.error("Error:", error)); // Handle errors
```

### Other Response Methods:

-   **`response.text()`** → For plain text responses
-   **`response.blob()`** → For images/files

### 6., How does the fetch function handle errors and handle HTTP status codes? Provide an example of using fetch to handle different types of responses, including successful and error responses.

### Handling Errors & HTTP Status Codes with `fetch()`

The `fetch()` function in JavaScript **does not reject on HTTP errors** (e.g., 404, 500). It only rejects for **network issues**. You must manually check `response.ok` and `response.status`.

### Example: Handling Success & Errors

```javascript
fetch("https://api.example.com/data")
    .then((response) => {
        if (!response.ok) {
            throw new Error(`HTTP Error! Status: ${response.status}`);
        }
        return response.json();
    })
    .then((data) => console.log("Success:", data))
    .catch((error) => console.error("Error:", error.message));
```

### 7., Explain the parts of an URL.

### Example

https://www.example.com:8080/path/page.html?search=query#section

### Key Components:

-   **Protocol** → `https://` → Communication method (e.g., HTTP, HTTPS)
-   **Domain** → `www.example.com` → Website address
-   **Port (Optional)** → `:8080` → Specifies a connection port (default: 80 for HTTP, 443 for HTTPS)
-   **Path** → `/path/page.html` → Specific resource on the server
-   **Query String** → `?search=query` → Key-value pairs for data transfer
-   **Fragment** → `#section` → Jumps to a specific page section

🔹 **URLs help locate and access resources on the web.** 🚀

## Serve

### 1., Explain the concept of client-server communication in the context of web development. How does information flow between the client and the server in a typical client-server architecture?

### Client-Server Communication in Web Development

In a **client-server architecture**, the **client** (browser/app) requests data from the **server**, which processes the request and responds.

### Information Flow:

1. **Client Sends Request** → Uses HTTP/HTTPS to request data from the server.
2. **Server Processes Request** → Retrieves, processes, or updates data.
3. **Server Sends Response** → Returns **HTML, JSON, XML, or files** to the client.
4. **Client Renders Data** → Displays content based on the response.

### Example:

```javascript
fetch("https://api.example.com/data")
    .then((response) => response.json())
    .then((data) => console.log(data));
```

### 2., What is the role of HTTP requests and responses in web development? Explain the structure of an HTTP request and an HTTP response.

### Role of HTTP Requests & Responses in Web Development

HTTP enables **communication between the client (browser) and the server** through **requests** and **responses**.

### 1. **HTTP Request Structure**

Sent by the client to request data.

**Components:**

-   **Method** → `GET`, `POST`, `PUT`, `DELETE` (defines action)
-   **URL** → Resource location (e.g., `/api/data`)
-   **Headers** → Metadata (e.g., `Content-Type`)
-   **Body** (optional) → Data (used in `POST`, `PUT`)

### Example:

```http
GET /api/users HTTP/1.1
Host: example.com
Authorization: Bearer token123
```

### 2. HTTP Response Structure

Sent by the server with requested data.

### Components:

-   **Status Code** → `200 OK`, `404 Not Found`, `500 Internal Server Error`
-   **Headers** → Metadata (e.g., `Content-Type: application/json`)
-   **Body** → Data (JSON, HTML, XML, etc.)

### Example:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id": 1, "name": "Alice"}
```

### 3., Explain the key differences between the CommonJS require syntax and the ECMAScript (ES) module syntax import. How do these two approaches handle module dependencies and exports in JavaScript?

### Key Differences

| Feature          | CommonJS (`require`)               | ES Modules (`import`)                    |
| ---------------- | ---------------------------------- | ---------------------------------------- |
| **Syntax**       | `require()` / `module.exports`     | `import` / `export`                      |
| **Execution**    | **Synchronous** (loads at runtime) | **Asynchronous** (loads at compile time) |
| **Environment**  | Node.js                            | Browsers & Node.js                       |
| **Tree Shaking** | ❌ No                              | ✅ Yes (removes unused code)             |

### Example

**CommonJS:**

```javascript
const math = require("./math.js");
console.log(math.add(5, 3));
```

**ES6 Modules:**

```javascript
import { add } from "./math.js";
console.log(add(5, 3));
```

### 4., What are the advantages of using the ES module syntax import over the CommonJS require syntax?

✅ **Asynchronous Loading** → ES Modules load **at compile time**, improving performance.  
✅ **Tree Shaking Support** → Removes unused code, reducing bundle size.  
✅ **Better Compatibility** → Works in both **browsers and Node.js**.  
✅ **Cleaner Syntax** → More **readable** and **structured**.

### Example:

```javascript
import { add } from "./math.js"; // ES Modules (better)
const math = require("./math.js"); // CommonJS
```

### 5., What is Express.js and how does it simplify web application development in Node.js? Explain the core features and benefits of using Express.js as a web framework.

-   Express.js is a lightweight and fast web framework for Node.js that simplifies web application development by providing a minimal and flexible structure.

### Core Features & Benefits:

-   **Routing**: Built-in routing system for handling different HTTP requests.
-   **Middleware**: Supports middleware for request processing, authentication, and logging.
-   **Static File Serving**: Easily serves static assets like CSS and images.
-   **Template Engines**: Supports templating engines like EJS and Pug for dynamic content.
-   **REST API Development**: Simplifies building APIs with JSON support.
-   **Extensibility**: Supports third-party middleware and plugins.
-   Express.js makes backend development in Node.js more efficient with minimal boilerplate and better scalability.

---

### 6., Explain the process of handling static files (e.g., CSS, images) in Express.js. How can you configure Express.js to serve static assets from a specific directory in your application?

-   In Express.js, you can serve static files (e.g., CSS, images) using the built-in `express.static` middleware. To configure it, use:

```js
app.use(express.static("public"));
```

This tells Express to serve static assets from the `public` directory. Users can then access files directly via their URLs (e.g., `/images/logo.png`). You can also specify a virtual path:

```js
app.use("/static", express.static("public"));
```

-   Now, static files are accessible via `/static/images/logo.png`.

---

### 7., How does Express.js handle HTTP request/response cycles? Explain the process of receiving and responding to requests using Express.js middleware and route handlers.

-   Express.js handles HTTP request/response cycles using middleware and route handlers. When a request is received, it passes through a series of middleware functions in the order they are defined. Middleware can modify the request, execute code, or end the response. Route handlers match specific request URLs and HTTP methods, process the request, and send a response. If no route matches, Express sends a 404 error. The cycle ends when a response is sent or an error is passed to an error-handling middleware.

---

## Forms

### 1., How does routing work in Express.js? Explain how to define routes and handle different HTTP methods (GET, POST, etc.) in an Express.js application.

Express.js **routes** define how the server handles **HTTP requests** (GET, POST, etc.).

### Defining Routes:

```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => res.send("Hello, GET!"));
app.post("/data", (req, res) => res.send("Received POST request"));

app.listen(3000, () => console.log("Server running on port 3000"));
```

✅ **`app.get()`** → Handles GET requests  
✅ **`app.post()`** → Handles POST requests  
✅ **Other Methods:** `PUT`, `DELETE`, `PATCH`

### 2., What are the various methods available in Express.js for sending responses to clients? Explain the differences between res.send() and res.json[] in Express.js.

Express provides several methods to send responses to clients:

✅ **`res.send()`** → Sends text, HTML, or JSON (auto-detects type)  
✅ **`res.json()`** → Sends JSON response (sets `Content-Type: application/json`)  
✅ **`res.redirect()`** → Redirects to another URL  
✅ **`res.status()`** → Sets HTTP status code  
✅ **`res.end()`** → Ends the response without data

### Example:

```javascript
app.get("/text", (req, res) => res.send("Hello!"));
app.get("/json", (req, res) => res.json({ message: "Hello!" }));
```

### 3., Explain what the express.json() middleware does?

✅ **`express.json()`** is built-in middleware in Express.js that **parses incoming JSON data** from `req.body`.  
✅ It is required for handling `POST`, `PUT`, or `PATCH` requests with JSON payloads.

### Example:

```javascript
const express = require("express");
const app = express();

app.use(express.json()); // Enables JSON parsing

app.post("/data", (req, res) => {
    console.log(req.body); // Access JSON data
    res.send("JSON received");
});
```

### 4., What is the purpose of the next() function in Express.js middleware? How can you use it to pass control to the next middleware function in the chain or to terminate the middleware processing?

✅ **`next()`** passes control to the **next middleware** in the stack.  
✅ If not called, the request **hangs** without a response.  
✅ Used for **logging, authentication, error handling**, etc.

### Example:

```javascript
app.use((req, res, next) => {
    console.log("Middleware executed");
    next(); // Passes control to the next middleware/route
});

app.get("/", (req, res) => res.send("Hello, World!"));
```

### 5., Explain the concept of route parameters in Express.js. How can you extract dynamic values from the URL path using route parameters, and how are these values accessed within route handlers?

✅ **Route parameters** allow extracting **dynamic values** from the URL.  
✅ Defined using `:` in the route path.  
✅ Accessed via `req.params`.

### Example:

```javascript
app.get("/user/:id", (req, res) => {
    res.send(`User ID: ${req.params.id}`);
});
```

### Request:

```http
GET /user/123
```

### Response:

```http
User ID: 123
```

### 6., Can you name some typical HTTP response codes and their meaning?

✅ **200 OK** → Request successful  
✅ **201 Created** → Resource successfully created  
✅ **400 Bad Request** → Invalid client request  
✅ **401 Unauthorized** → Authentication required  
✅ **403 Forbidden** → Access denied  
✅ **404 Not Found** → Resource not found  
✅ **500 Internal Server Error** → Server-side issue

🚀 **HTTP status codes indicate request outcomes!**

### 7., Can you name some typical HTTP request/response headers and their meaning?

### 🔹 **Request Headers:**

✅ **`Content-Type`** → Specifies request body format (e.g., `application/json`)  
✅ **`Authorization`** → Sends credentials (e.g., `Bearer token`)  
✅ **`Accept`** → Defines response format expected by the client

### 🔹 **Response Headers:**

✅ **`Content-Type`** → Specifies response format (e.g., `application/json`)  
✅ **`Cache-Control`** → Controls caching behavior  
✅ **`Set-Cookie`** → Sends cookies to the client

🚀 **Headers provide metadata for HTTP communication!**

### 8., What are the common HTTP methods used in web development, and what are their respective purposes?

✅ **GET** → Retrieve data from the server  
✅ **POST** → Send data to the server (create resource)  
✅ **PUT** → Update/replace a resource  
✅ **PATCH** → Partially update a resource  
✅ **DELETE** → Remove a resource

🚀 **HTTP methods define actions for web communication!**

### 9., How does the GET method differ from the POST method? Explain when it is appropriate to use each method. Which one uses request body to send data? What the other method uses to send data?

✅ **GET** → Retrieves data, sends parameters via **URL/query string**  
✅ **POST** → Sends data, uses **request body**

### Key Differences:

| Feature           | GET                          | POST                         |
| ----------------- | ---------------------------- | ---------------------------- |
| **Purpose**       | Fetch data                   | Send/create data             |
| **Data Location** | URL (query parameters)       | Request body                 |
| **Security**      | Less secure (visible in URL) | More secure (hidden in body) |
| **Caching**       | Can be cached                | Not cached                   |

🚀 **Use GET for reading data, POST for sending/modifying data!**

### 10., Explain the use of the PATCH method in HTTP. How does it differ from the PUT method, and when should it be used to update a resource?

✅ **PATCH** → Partially updates a resource  
✅ **PUT** → Fully replaces a resource

### Key Differences:

| Feature       | PATCH                  | PUT                     |
| ------------- | ---------------------- | ----------------------- |
| **Purpose**   | Update specific fields | Replace entire resource |
| **Data Sent** | Only changed fields    | Full resource data      |
| **Use Case**  | Small modifications    | Complete updates        |

🚀 **Use PATCH for partial updates, PUT for full replacements!**

### 11., How can the DELETE method be used to remove a resource from a server? Explain how the DELETE method works and any considerations for handling resource deletion.

✅ **DELETE** → Removes a resource from the server.

### How It Works:

1. Client sends a `DELETE` request to the server.
2. Server processes and removes the specified resource.
3. Server responds with **200 OK**, **204 No Content**, or **404 Not Found** if the resource doesn’t exist.

### Considerations:

-   **Irreversible** → Ensure confirmation before deleting.
-   **Authorization Required** → Protect sensitive data with authentication.

### 12., How do you handle form submissions using JavaScript? Explain the process of capturing form data and preventing the default form submission behavior.

✅ **Capture Form Data** → Use `document.querySelector()` to access form elements.  
✅ **Prevent Default Submission** → Use `event.preventDefault()` to stop page reload.  
✅ **Process Data** → Read input values and send via `fetch()` or `XMLHttpRequest`.

### Example:

```javascript
document.querySelector("form").addEventListener("submit", function (event) {
    event.preventDefault(); // Prevents page reload
    const formData = new FormData(event.target);
    console.log(Object.fromEntries(formData)); // Logs form data
});
```

### 13., Explain the required elements necessary to define a form in HTML.

✅ **`<form>`** → Defines the form container  
✅ **`action`** → URL where form data is sent  
✅ **`method`** → HTTP method (`GET` or `POST`)  
✅ **`<input>`** → Fields for user input  
✅ **`name`** → Identifier for form fields  
✅ **`<label>`** → Describes input fields  
✅ **`<button type="submit">`** → Submits the form

### Example:

```html
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required />
    <button type="submit">Submit</button>
</form>
```

### 14., What is the purpose of the required attribute in HTML form elements? How does it enforce mandatory input fields and prevent form submission without the required information?

✅ **Ensures Mandatory Input** → Prevents form submission if the field is empty.  
✅ **Works on `<input>`, `<textarea>`, `<select>`** → Enforces required data entry.  
✅ **Provides Built-in Validation** → Shows error messages without JavaScript.

### Example:

```html
<form>
    <input type="text" name="username" required />
    <button type="submit">Submit</button>
</form>
```

### 15., Explain the different types of form input fields available in HTML. How do input types like text, number, email, checkbox, and radio buttons differ, and how are they used in forms?

✅ **`text`** → Single-line text input (e.g., name, username)  
✅ **`number`** → Accepts numeric values (e.g., age, quantity)  
✅ **`email`** → Validates email format (`example@mail.com`)  
✅ **`checkbox`** → Allows multiple selections (e.g., interests)  
✅ **`radio`** → Allows **one** selection from a group (e.g., gender)

### Example:

```html
<form>
    <input type="text" placeholder="Name" />
    <input type="number" placeholder="Age" />
    <input type="email" placeholder="Email" />
    <input type="checkbox" /> Subscribe
    <input type="radio" name="gender" value="male" /> Male
    <input type="radio" name="gender" value="female" /> Female
</form>
```

### 16., Can you explain the purpose of the name attribute in a context of form submission?

-   The `name` attribute in form elements identifies the input fields and is essential for form submission. When a form is submitted, the browser sends key-value pairs where the `name` is the key, and the input value is the value.

### **Example:**

```html
<input type="text" name="username" value="JohnDoe" />
```

-   Submits as **`username=JohnDoe`** in the request.

-   Without `name`, the field's data won't be included in form submissions. It is crucial for server-side processing and retrieving form data.

---

### 17., Can you explain how we can connect a label tag to a form element?

-   You can connect a `<label>` tag to a form element in two ways:

1. **Using the `for` attribute (recommended):**

    ```html
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" />
    ```

    - The `for` attribute links the label to the input with the matching `id`.
    - Clicking the label focuses the input field.

2. **Wrapping the input inside the `<label>` tag:**
    ```html
    <label>Username: <input type="text" name="username" /></label>
    ```
    - No `id` is needed, and clicking the label still focuses the input.

-   Using the `for` attribute is preferred for better accessibility.

---

### 18., How can you dynamically manipulate or modify form elements using JavaScript? Explain how to add or remove form fields dynamically based on user interaction or specific conditions.

-   You can dynamically manipulate form elements using JavaScript by adding or removing fields based on user interaction.

### **Adding Form Fields:**

```js
const form = document.getElementById("form");
const newInput = document.createElement("input");
newInput.type = "text";
newInput.name = "dynamicField";
form.appendChild(newInput);
```

### **Removing Form Fields:**

```js
const inputToRemove = document.getElementById("inputId");
inputToRemove.remove();
```

### **Event-Based Manipulation:**

```js
document.getElementById("addBtn").addEventListener("click", () => {
    const input = document.createElement("input");
    input.type = "text";
    document.getElementById("form").appendChild(input);
});
```

-   Use event listeners to add/remove elements dynamically based on user actions.

---

### 19., How can you convert form data into a format that can be easily transmitted or processed by the server?

-   You can convert form data into a format that the server can process using **URL encoding, JSON, or FormData**:

1. **URL-encoded format** (default for HTML forms):

    ```js
    const formData = new URLSearchParams(new FormData(formElement)).toString();
    ```

2. **JSON format** (for APIs):

    ```js
    const formObject = Object.fromEntries(new FormData(formElement).entries());
    const jsonData = JSON.stringify(formObject);
    ```

3. **FormData object** (for files or multipart data):
    ```js
    const formData = new FormData(formElement);
    ```

-   The choice depends on the server's expected format.

---

## React

### 1., What is React.js and what are its key features?

-   answer

### 2., Explain the concept of virtual DOM and how it contributes to React's performance.

-   answer

### 3., Explain the component-based architecture in React.js. How do components work, and how can they be composed to build complex user interfaces?

-   answer

### 4., What is the significance of JSX in React.js? Explain how JSX combines HTML-like syntax with JavaScript code and how it is transpiled into regular JavaScript during the build process.

-   answer

### 5., What are props in React and how are they used to pass data between components? Explain the concept of props and how they facilitate parent-child component communication.

-   answer

### 6., How can you access and utilize props within a functional component in React? Explain how to extract and use props using the destructuring syntax.

-   answer

### 7., How can you pass callback functions as props in React? Provide an example of how to pass a function from a parent component to a child component, enabling the child to communicate with the parent.

-   answer

### 8., Explain the concept of spreading props in React. How can the spread operator be used to pass multiple props from a parent component to a child component in a concise manner?

**Prop spreading** allows you to pass multiple props at once using the **spread operator (`...`)** for cleaner and more concise code.

✅ **Example:**

```jsx
const props = { name: "John", age: 30 };
<Profile {...props} />;
```

This is equivalent to:

```jsx
<Profile name="John" age="30" />
```

✅ Useful for **reusable components** and **dynamic prop passing**.

### 9., Explain the concept of default props (with ES6 JS syntax) in React. How can you define default values for props in a component to handle cases where the prop value is not explicitly passed?

**Default props** are fallback values used when a prop is not passed to a component.

✅ **ES6 Syntax:**
You can define defaults directly in the function parameters:

```jsx
function Greeting({ name = "Guest" }) {
    return <h1>Hello, {name}!</h1>;
}
```

✅ Helps avoid **undefined values** and keeps components more **robust and predictable**.

### 10., Explain the immutability principle when working with props and states in React. Why is it important to avoid directly modifying prop values within a component, and what are some best practices for maintaining immutability?

In React, **props and state should not be modified directly**. Instead, always create a **new copy** when updating state to maintain **immutability**.

✅ **Why it matters:**  
Immutability helps React detect changes and trigger efficient re-renders.

✅ **Best practices:**

-   Use spread syntax (`...`) to update objects or arrays
-   Never modify props directly

### 11., How does React.js handle state management? Explain the concept of state and how it differs from props.

**State** holds dynamic, local data in a component and can change over time using hooks like `useState`.  
**Props** are read-only values passed from parent to child.

✅ **Key Difference:**

-   **State**: Internal, changeable.
-   **Props**: External, read-only.

### 12., What are React hooks? Explain the purpose and benefits of hooks like useState, useEffect in React.js.

**React Hooks** are functions that let you use state and other React features in functional components without writing class components.

-   **`useState`** allows you to add and manage local state in functional components.
-   **`useEffect`** lets you perform side effects (e.g., data fetching, subscriptions, DOM updates) in components.

✅ **Benefits of Hooks:**

-   Cleaner and more readable code
-   Reusable logic through custom hooks
-   No need for class components
-   Better separation of concerns and component lifecycle handling

### 13., Explain the concept of virtual DOM reconciliation in React.js. How does React efficiently update and render components by performing minimal DOM manipulations?

The **Virtual DOM** is a lightweight copy of the real DOM that React uses to optimize rendering. When the state or props change, React creates a new virtual DOM and compares it with the previous one using a process called **reconciliation**.

React identifies the **differences (diffing)** between the old and new virtual DOM and updates only the changed parts in the **real DOM**, instead of re-rendering everything.

✅ This approach minimizes costly DOM manipulations and ensures better performance and a smoother user experience.

### 14., Explain how to manage complex state objects with useState. Explain techniques like object spreading or merging to update specific properties within an object state.

When managing complex state objects with `useState`, you should **avoid directly mutating the state**. Instead, use techniques like **object spreading** to update specific properties while keeping the rest unchanged.

✅ Example using object spread syntax:

```jsx
const [user, setUser] = useState({ name: "Alice", age: 25 });

setUser({ ...user, age: 26 }); // updates only the age, keeps the name
```

This ensures a **new object reference**, so React can detect the change and re-render correctly.

You can also update **deeply nested properties** by combining multiple spread operators or consider using **state management tools like `useReducer`** for more complex state structures.

### 15., Why is it important to provide a new array as an argument to the useState hook when adding an item to an existing array?

In React, state updates must be **immutable** to ensure React detects changes and re-renders the component. Directly modifying the existing array (e.g., using `push()`) does not create a new reference, so React may not recognize the update.

✅ Instead, create a **new array** using spread syntax or array methods:

```jsx
setItems([...items, newItem]);
```

### 16., How does conditional rendering work in React? Explain the different techniques and approaches available to conditionally render components or content based on certain conditions or state values. How can it be used to control the visibility or behavior of components based on user interactions or other dynamic conditions?

Conditional rendering in React means displaying components or content based on certain conditions (e.g., state or props). It allows dynamic control of what gets rendered in the UI.

#### ✅ Common Techniques:

-   **if/else statements** (outside JSX):

```jsx
if (isLoggedIn) {
    return <Dashboard />;
} else {
    return <Login />;
}
```

#### ✅ Common Techniques:

-   **Ternary operator (inline in JSX):**

```jsx
{
    isLoggedIn ? <Dashboard /> : <Login />;
}
```

-   **Logical AND (`&&`) operator (for rendering something only if a condition is true):**

```jsx
{
    isAdmin && <AdminPanel />;
}
```

-   **Conditional functions or return statements:**  
    Used in render methods or functional components to decide what to return based on conditions.

### 📌 Use Cases:

-   Show/hide elements based on user interaction
-   Render loading spinners or error messages
-   Display different content based on authentication status or app state

### 17., How can you create a select input element in React? How does it differ from the html's select tag? Can you show an example of a controlled and an uncontrolled select element with default value setting?

In React, you create a `<select>` input similarly to HTML, but typically use it as a **controlled component**, where the selected value is managed by React state. Unlike plain HTML, React requires explicit `value` and `onChange` props for controlled inputs.

#### ✅ Controlled Select Example:

```jsx
import { useState } from "react";

function ControlledSelect() {
    const [option, setOption] = useState("apple");

    return (
        <select value={option} onChange={(e) => setOption(e.target.value)}>
            <option value="apple">Apple</option>
            <option value="banana">Banana</option>
            <option value="orange">Orange</option>
        </select>
    );
}
```

```js
function UncontrolledSelect() {
    return (
        <select defaultValue="banana">
            <option value="apple">Apple</option>
            <option value="banana">Banana</option>
            <option value="orange">Orange</option>
        </select>
    );
}
```

### 🔑 Key Difference

-   **Controlled Components**: React handles the selected value via **state** using `value` and `onChange` props. This provides better control and synchronization with other UI elements.

-   **Uncontrolled Components**: The DOM manages the value internally using `defaultValue`. React does **not track** the changes unless you manually access the value using **refs**.

# -- Database --

## 1., What is MongoDB, and how does it differ from traditional relational databases? Explain the key features and advantages of MongoDB as a NoSQL database solution.

-   MongoDB is a NoSQL, document-oriented database that stores data in flexible, JSON-like BSON format instead of tables and rows like traditional relational databases (RDBMS).

### **Key Differences from RDBMS:**

-   **Schema-less**: No fixed table structure; documents can have varying fields.
-   **Scalability**: Horizontally scalable via sharding, unlike most RDBMS that scale vertically.
-   **Flexible Queries**: Supports rich queries, indexing, and aggregation.
-   **No Joins**: Uses embedded documents instead of costly joins.

### **Advantages of MongoDB:**

✅ **Fast Read/Write**: Optimized for high-speed data access.  
✅ **Flexible & Scalable**: Ideal for big data, real-time apps, and distributed systems.  
✅ **JSON-like Storage**: Easier integration with JavaScript and modern web apps.  
✅ **Automatic Failover**: Built-in replication ensures high availability.

---

## 2., Explain the concept of collections and documents in MongoDB? How does MongoDB store data, and how is it organized within collections and documents.

-   In MongoDB, **collections** and **documents** replace tables and rows in relational databases.

### **Concepts:**

-   **Document**: A JSON-like BSON object containing key-value pairs (e.g., `{ name: "USA", population: 331000000 }`).
-   **Collection**: A group of related documents, similar to a table but without a fixed schema.

### **Data Storage & Organization:**

-   Data is stored in **documents**, allowing flexibility in structure.
-   **Collections** hold multiple documents with similar data types but no enforced schema.
-   MongoDB uses an **index-based** storage engine for efficient retrieval.
-   Documents can be **embedded** (nested) or **referenced** (linked) for relationships.

---

## 3., What is Mongoose.js, and how does it simplify working with MongoDB in a Node.js environment? Explain the key features and benefits of using Mongoose.js.

-   ### **Mongoose.js**
    Mongoose is an **ODM (Object Data Modeling) library** for MongoDB in **Node.js**, providing schema-based structure and validation for MongoDB documents.

### **Key Features:**

✅ **Schema Definition** – Defines strict data models using schemas.  
✅ **Validation** – Built-in data validation before saving to the database.  
✅ **Middleware (Hooks)** – Pre/post-processing of data (e.g., hashing passwords).  
✅ **Query Building** – Simplifies CRUD operations with an intuitive API.  
✅ **Virtuals & Methods** – Adds computed properties and custom methods.

### **Benefits of Using Mongoose:**

✔ **Easier Data Management** – Structured and readable code.  
✔ **Better Data Integrity** – Prevents inconsistent data with schemas.  
✔ **Async/Await Support** – Handles queries efficiently in modern JS.  
✔ **Relationship Handling** – Supports document references and population.

---

## 4., How do you define and create schemas in Mongoose.js? Explain how schemas define the structure and validation rules for documents in MongoDB collections.

✅ In Mongoose, **schemas define the structure and validation rules** for documents in a MongoDB collection.

```js
const mongoose = require("mongoose");
const Schema = mongoose.Schema;

const UserSchema = new Schema({
    name: { type: String, required: true },
    age: { type: Number, min: 0 },
    email: { type: String, unique: true },
});
```

✅ A **model** is then created from the schema:

```js
const User = mongoose.model("User", UserSchema);
```

Schemas help enforce **data types, constraints, and validation rules** before saving data.

---

## 5., Explain the different types of Mongoose.js data modeling techniques. How can you define relationships between MongoDB collections using Mongoose.js, such as one-to-one, one-to-many, and many-to-many relationships?

✅ Mongoose supports various **data modeling techniques** to define relationships:

-   **One-to-One:** Use a field with `type: mongoose.Schema.Types.ObjectId` referencing another model.

```js
const ProfileSchema = new Schema({
    user: { type: mongoose.Schema.Types.ObjectId, ref: "User" },
});
```

-   **One-to-Many:** Store an array of ObjectIds referencing another model.

```js
const BlogSchema = new Schema({
    comments: [{ type: mongoose.Schema.Types.ObjectId, ref: "Comment" }],
});
```

-   **Many-to-Many:** Both models contain arrays of references to each other.

```js
const StudentSchema = new Schema({
    courses: [{ type: mongoose.Schema.Types.ObjectId, ref: "Course" }],
});

const CourseSchema = new Schema({
    students: [{ type: mongoose.Schema.Types.ObjectId, ref: "Student" }],
});
```

✅ These relationships are handled using `.populate()` to fetch related data.

---

## 6., What are the available options for querying and manipulating data using Mongoose.js? Explain how to perform CRUD operations (create, read, update, delete) using Mongoose.js methods and queries.

✅ Mongoose provides built-in methods to perform **CRUD operations**:

-   **Create:** `Model.create()` or `new Model().save()`

```js
User.create({ name: "Alice", age: 25 });
```

-   **Read:** `Model.find()`, `Model.findById()`, `Model.findOne()`

```js
User.find({ age: 25 });
```

-   **Update:** `Model.updateOne()`, `Model.findByIdAndUpdate()`

```js
User.updateOne({ name: "Alice" }, { age: 26 });
```

-   **Delete:** `Model.deleteOne()`, `Model.findByIdAndDelete()`

```js
User.deleteOne({ name: "Alice" });
```

✅ These methods allow efficient querying and data manipulation in MongoDB.

## 7., Explain the process of connecting to a MongoDB database using Mongoose.js. How can you configure and establish a connection to a MongoDB server using Mongoose.js in a Node.js application?

**Mongoose.js** is an ODM (Object Data Modeling) library for MongoDB and Node.js.

✅ **Basic Connection Setup:**

```js
const mongoose = require("mongoose");

mongoose
    .connect("mongodb://localhost:27017/mydb", {
        useNewUrlParser: true,
        useUnifiedTopology: true,
    })
    .then(() => console.log("Connected to MongoDB"))
    .catch((err) => console.error("Connection error:", err));
```

✅ Mongoose simplifies schema creation, data validation, and queries in MongoDB.

# -- MERN --

## 1., Explain the concept of React Router. How does it enable client-side routing in React.js applications and facilitate the creation of multi-page-like experiences?

-   ### **React Router**
    React Router is a **routing library** for React that enables **client-side navigation**, creating multi-page-like experiences without full page reloads.

### **How It Works:**

✅ Uses the **History API** to update the URL dynamically.  
✅ **Routes map** URLs to components, rendering based on the path.  
✅ Supports **nested routes, redirects, and dynamic parameters**.

### **Benefits:**

✔ **Faster navigation** – No full page reloads.  
✔ **Single Page Application (SPA)** – Feels like multiple pages.  
✔ **Declarative Routing** – Easy-to-manage route components.

## 2., Explain the concept of server-side routing in Express.js. How does Express handle incoming requests and route them to the appropriate API endpoints or route handlers?

-   ### **Server-Side Routing in Express.js**
    Express.js handles **server-side routing** by mapping **incoming requests** (URLs) to specific **route handlers**.

### **How It Works:**

✅ Uses `app.METHOD(PATH, HANDLER)` (e.g., `app.get('/users', handler)`).  
✅ **Middleware & Controllers** process requests before sending responses.  
✅ Supports **dynamic routes**, query params, and route grouping via `express.Router()`.

### **Benefits:**

✔ **Efficient API handling** for backend services.  
✔ **Modular & Scalable** structure with routers.  
✔ **Supports Middleware** for authentication, logging, etc.

## Essential for **MERN** backend development! 🚀

## 3., What is the MERN stack? Explain the individual components of the MERN stack and their role in building web applications.

-   ### **MERN Stack**
    MERN is a **JavaScript-based** tech stack for building full-stack web apps.

### **Components & Roles:**

✅ **MongoDB** – NoSQL database for storing data.  
✅ **Express.js** – Backend framework for handling API requests.  
✅ **React.js** – Frontend library for building UI.  
✅ **Node.js** – Runtime for executing JavaScript on the server.

## 💡 **MERN enables full-stack JavaScript development, making apps fast & scalable!** 🚀

## 4., Explain how does a proxy works during React development. How can you tell the webpack dev server to proxy the requests to your backend? What kind of URLs you have to use in the fetch in your JS code, if you want to use the proxy.

-   ### **Proxy in React Development**
    A **proxy** helps bypass CORS issues by forwarding frontend requests to the backend during development.

### **Setting Up Proxy in React:**

1. Add to `package.json`:
    ```json
    "proxy": "http://localhost:5000"
    ```
2. Use **relative URLs** in `fetch` requests:
    ```js
    fetch("/api/data"); // Proxied to backend
    ```

### **How It Works:**

✅ Webpack Dev Server **forwards** requests to `localhost:5000`.  
✅ No need for full backend URLs in `fetch`.  
✅ Simplifies API calls in development. 🚀

---

## 5., Explain the advantages and benefits of using the MERN stack for web development. How does each component of the MERN stack contribute to the development process and overall efficiency of building modern web applications?

✅ The **MERN stack** is a full JavaScript solution for modern web apps.

-   **MongoDB**: NoSQL database for flexible data storage
-   **Express.js**: Handles backend routing and APIs
-   **React.js**: Builds dynamic user interfaces
-   **Node.js**: Runs JavaScript on the server

✅ Benefits:  
Fast development, reusable components, scalable architecture, and a unified language across the stack.

---

## 6., How does data flow in the MERN stack architecture? Explain how the frontend, built with React.js, communicates with the backend, developed with Node.js and Express.js, to handle client requests and serve data from the MongoDB database.

✅ In the **MERN stack**, data flows from the **React frontend** to the **Node.js + Express backend** via HTTP requests (e.g., using `fetch`). The backend processes the request, interacts with the **MongoDB database** using **Mongoose**, and sends the response back to the frontend.

➡️ React (Client) → Express (API) → MongoDB (Database) → Response → React (UI update)

This architecture enables full-stack development using JavaScript across all layers.
