# Web Module Questions

# -- Modern JS --

## 1., What is ECMAScript? What is the difference between Javascript & ECMAScript?

**ECMAScript (ES)** = The **standard** on which **JavaScript** is based.

**Difference:**

-   📜 **ECMAScript** = Rules/specification
-   💻 **JavaScript** = Language that implements ES + extras (e.g., DOM)

🔍 Think of **ECMAScript as the recipe**, **JavaScript as the final dish**.

---

## 2., Explain the concept of "block scoping" introduced in ES6. How does it differ from function scoping?

**Block scoping** (`let`, `const`) → Limited to `{}` blocks  
**Function scoping** (`var`) → Limited to the whole function

| Feature      | `var` (Function Scope)          | `let` / `const` (Block Scope)      |
| ------------ | ------------------------------- | ---------------------------------- |
| **Scope**    | Whole function                  | Inside `{}` only                   |
| **Lifetime** | Full function execution         | Ends after block finishes          |
| **Hoisting** | Yes, initialized as `undefined` | Yes, but in **TDZ** until declared |
| **Redefine** | Allowed in same scope           | ❌ Not allowed in same block       |

**Example:**

```js
if (true) {
    var a = 1; // function-scoped
    let b = 2; // block-scoped
}
console.log(a); // ✅ 1
console.log(b); // ❌ ReferenceError
```

## 3., What are template literals in ES6 and how do they improve string manipulation in JavaScript?

**Template Literals (ES6)** = Strings with **backticks \` \`** → easier string handling

### 🔑 Benefits:

-   💬 **Interpolation:** `${variable}`

```js
let name = "Jack";
console.log(`Hello, ${name}!`);
```

-   📄 **Multi-line strings:**

```js
let msg = `Line 1
Line 2`;
```

-   ➕ **Expressions inside strings:** `${a + b}`
-   🏷️ **Tagged templates:** Custom string processing

```js
function tag(strings, val) {
    return `${strings[0]}${val.toUpperCase()}`;
}
tag`Hi, ${"jack"}`; // Hi, JACK
```

## 4., Explain the concept of "destructuring assignment" in ES6. How does it simplify variable assignment and object/array manipulation.

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

---

## 5., What is the "spread operator" in ES6 and how can it be used to manipulate arrays and objects more effectively?

**Spread Operator (`...`)** = Expands arrays or objects into individual elements

### 📚 Arrays:

```js
const arr1 = [1, 2, 3];
const arr2 = [...arr1]; // copy
const merged = [...arr1, 4, 5];
```

### 🧩 Objects:

```js
const obj1 = { a: 1 };
const obj2 = { ...obj1, b: 2 }; // merge or copy
```

✅ Useful for **copying**, **merging**, and **passing elements**

---

## 6., How does ES6 introduce the concept of "default function parameters"? Provide an example of using default parameters in a function.

**Default Parameters (ES6)** = Set **default values** if no argument is passed

### 📌 Example:

```js
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}
greet(); // Hello, Guest
greet("Jack"); // Hello, Jack
```

### 💰 Multiple parameters:

```js
function calculatePrice(price, tax = 0.1) {
    return price + price * tax;
}
```

✅ Prevents `undefined` errors & simplifies code

---

## 7., Explain the concept of "modules" introduced in ES6. How do they improve code organization and reusability in JavaScript?

### **ES6 Modules** = Split JS code into **reusable, organized files**

🔑 **Features:**

-   🔒 **Encapsulation** – Scoped code
-   ♻️ **Reusability** – Share code across files
-   🛠️ **Maintainability** – Clean structure
-   ⚡ **Static imports/exports** – Better performance

### 📤 Exporting (Named Export):

```js
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

## 8., Compare the CommonJS and ES6 "modules". What are the differences?

### 🔍 Overview:

-   **CommonJS (CJS)** → Used in **Node.js**
-   **ES6 Modules (ESM)** → Modern standard (Browsers + Node.js)

### 🔑 Differences:

| Feature          | CommonJS (CJS)                 | ES6 Modules (ESM)   |
| ---------------- | ------------------------------ | ------------------- |
| **Syntax**       | `require()` / `module.exports` | `import` / `export` |
| **Execution**    | Synchronous                    | Asynchronous        |
| **Tree Shaking** | ❌ No                          | ✅ Yes              |
| **Used In**      | Node.js                        | Browsers & Node.js  |
| **Extensions**   | `.js`                          | `.js` / `.mjs`      |

### 🆚 Syntax Example:

**CJS:**

```js
// Export
module.exports.add = (a, b) => a + b;
// Import
const math = require("./math.js");
```

**ESM:**

```js
// Export
export const add = (a, b) => a + b;
// Import
import { add } from "./math.js";
```

---

## 9., What are higher-order functions in JavaScript?

**Higher-Order Function (HOF)** = A function that **takes or returns another function**

🔸 **Why use HOFs?** → More **reusable, readable, functional code**

### 📥 Takes a function:

```js
function greet(name, callback) {
    return callback(name);
}
greet("Alice", (name) => `Hello, ${name}!`);
```

### 📤 Returns a function:

```js
function multiplyBy(factor) {
    return (num) => num * factor;
}
const double = multiplyBy(2);
double(5); // 10
```

---

## 10., Explain the purpose and functionality of the map function in JavaScript. How does it differ from the filter and reduce functions?

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

## 11., How can the filter function be used to selectively extract elements from an array based on a given condition? Provide an example where the filter function is used to create a new array with only the elements that meet the specified criteria.

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

## 12., What is the role of the reduce function in JavaScript? How can it be used to aggregate or combine the elements of an array into a single value? Provide an example where the reduce function is used to calculate a cumulative sum or find the maximum value in an array.

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

# -- Fetch --

## 1., How does a query string parameter in a URL contribute to web application functionality? Explain how query string parameters are typically used to pass data between web pages or APIs.

**Query string parameters** = Key-value pairs added to a URL after `?`  
→ Used to **pass data between pages or APIs**

### 🔧 Example:

`example.com/products?category=shoes&page=2`

✅ Enable:

-   🔍 Filtering, searching, pagination
-   🧠 Dynamic content rendering
-   📊 Tracking user actions
-   🔄 API data control (e.g., sort, filter, limit)

---

## 2., What is the purpose and functionality of the fetch function in JavaScript?

**`fetch()`** = Built-in JS function to **make HTTP requests** (GET, POST, etc.)

✅ Returns a **Promise** → handles **API communication asynchronously**

### 📦 Example:

```js
fetch("https://api.example.com/data")
    .then((res) => res.json())
    .then((data) => console.log(data))
    .catch((err) => console.error("Error:", err));
```

🚀 Used for **fetching/sending data** in modern web apps

---

## 3., Explain the syntax of the fetch function and how it handles asynchronous operations. Compare and contrast the syntax of making HTTP requests using fetch with async/await versus the syntax using .then() and .catch(). What are the key differences and benefits of using the async/await syntax in terms of code structure and readability?

**`fetch()`** = Makes HTTP requests, returns a **Promise**

### 🔗 Basic Syntax (with `.then/.catch`):

```js
fetch(url)
    .then((res) => res.json())
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

### ✅ Using `async/await` (cleaner):

```js
async function getData() {
    try {
        const res = await fetch(url);
        const data = await res.json();
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}
getData();
```

### 🔍 Key Differences:

-   `.then()` → **Chained promises**, harder to read when nested
-   `async/await` → **Looks like sync code**, easier to read & debug  
    🚀 **`async/await` = cleaner, better code structure**

---

## 4., What is asynchronicity in JavaScript? Name some typical use cases when asynchronicity is needed.

-   **Asynchronicity** in JavaScript allows tasks to execute **without blocking** the main thread, enabling non-blocking operations.

### **Typical Use Cases:**

✅ **Fetching data from APIs** (`fetch`, `Axios`).  
✅ **Handling user input/events** (`setTimeout`, `setInterval`).  
✅ **Reading/writing files** (Node.js `fs` module).  
✅ **Database queries** (MongoDB, Firebase).  
✅ **WebSockets & real-time updates** (chat apps, live notifications).

-   🚀 **Ensures smooth performance without freezing the UI!**

---

## 5., How can you handle the response received from a fetch request?

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

## 6., How does the fetch function handle errors and handle HTTP status codes? Provide an example of using fetch to handle different types of responses, including successful and error responses.

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

## 7., Explain the parts of an URL.

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

---

# -- Serve --

## 1., Explain the concept of client-server communication in the context of web development. How does information flow between the client and the server in a typical client-server architecture?

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

## 2., What is the role of HTTP requests and responses in web development? Explain the structure of an HTTP request and an HTTP response.

### 🌐 HTTP Requests & Responses in Web Development

HTTP = Communication between **client (browser)** and **server**

### 📤 HTTP Request (from client):

-   **Method** → `GET`, `POST`, `PUT`, `DELETE`
-   **URL** → Resource location (`/api/data`)
-   **Headers** → Extra info (e.g., `Content-Type`)
-   **Body** → Data sent (in `POST`, `PUT`)

**Example:**

```
GET /api/users HTTP/1.1
Host: example.com
Authorization: Bearer token123
```

### 📥 HTTP Response (from server):

-   **Status Code** → `200`, `404`, `500`, etc.
-   **Headers** → Info like `Content-Type`
-   **Body** → Returned data (JSON, HTML, etc.)

**Example:**

```
HTTP/1.1 200 OK
Content-Type: application/json

{"id": 1, "name": "Alice"}
```

## 3., Explain the key differences between the CommonJS require syntax and the ECMAScript (ES) module syntax import. How do these two approaches handle module dependencies and exports in JavaScript?

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

## 4., What are the advantages of using the ES module syntax import over the CommonJS require syntax?

✅ **Asynchronous Loading** → ES Modules load **at compile time**, improving performance.  
✅ **Tree Shaking Support** → Removes unused code, reducing bundle size.  
✅ **Better Compatibility** → Works in both **browsers and Node.js**.  
✅ **Cleaner Syntax** → More **readable** and **structured**.

### Example:

```javascript
import { add } from "./math.js"; // ES Modules (better)
const math = require("./math.js"); // CommonJS
```

## 5., What is Express.js and how does it simplify web application development in Node.js? Explain the core features and benefits of using Express.js as a web framework.

**Express.js** = Fast, minimal web framework for **Node.js**

### 🚀 Core Features:

-   🔀 **Routing** → Handle HTTP methods (`GET`, `POST`, etc.)
-   ⚙️ **Middleware** → Process requests (auth, logging, etc.)
-   📁 **Static Files** → Serve CSS, images, etc.
-   🖋️ **Template Engines** → EJS, Pug for dynamic pages
-   🔗 **REST API Support** → Easy JSON-based APIs
-   🔌 **Extensible** → Add third-party middleware/plugins

✅ Makes backend dev **simpler, faster, scalable**

---

## 6., Explain the process of handling static files (e.g., CSS, images) in Express.js. How can you configure Express.js to serve static assets from a specific directory in your application?

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

## 7., How does Express.js handle HTTP request/response cycles? Explain the process of receiving and responding to requests using Express.js middleware and route handlers.

**Express.js Request/Response Cycle**

📥 When a request comes in:

1. 🔄 **Middleware** runs in order → modifies request, handles auth, logging, etc.
2. 🎯 **Route Handlers** → Match method & URL (`GET /users`, etc.), process request
3. 📤 **Response Sent** → Ends the cycle
4. ❌ If no route matches → **404 error**
5. ⚠️ Errors → Handled by special **error middleware**

---

# -- Forms --

## 1., How does routing work in Express.js? Explain how to define routes and handle different HTTP methods (GET, POST, etc.) in an Express.js application.

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

## 2., What are the various methods available in Express.js for sending responses to clients? Explain the differences between res.send() and res.json[] in Express.js.

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

## 3., Explain what the express.json() middleware does?

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

## 4., What is the purpose of the next() function in Express.js middleware? How can you use it to pass control to the next middleware function in the chain or to terminate the middleware processing?

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

## 5., Explain the concept of route parameters in Express.js. How can you extract dynamic values from the URL path using route parameters, and how are these values accessed within route handlers?

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

## 6., Can you name some typical HTTP response codes and their meaning?

✅ **Common HTTP Status Codes**

-   **200 OK** → Request successful
-   **201 Created** → Resource successfully created
-   **400 Bad Request** → Invalid client request
-   **401 Unauthorized** → Authentication required
-   **403 Forbidden** → Access denied
-   **404 Not Found** → Resource not found
-   **500 Internal Server Error** → Server-side issue

🚀 **HTTP status codes indicate request outcomes!**

## 7., Can you name some typical HTTP request/response headers and their meaning?

### 🔹 **Request Headers:**

✅ **`Content-Type`** → Specifies request body format (e.g., `application/json`)  
✅ **`Authorization`** → Sends credentials (e.g., `Bearer token`)  
✅ **`Accept`** → Defines response format expected by the client

### 🔹 **Response Headers:**

✅ **`Content-Type`** → Specifies response format (e.g., `application/json`)  
✅ **`Cache-Control`** → Controls caching behavior  
✅ **`Set-Cookie`** → Sends cookies to the client

🚀 **Headers provide metadata for HTTP communication!**

## 8., What are the common HTTP methods used in web development, and what are their respective purposes?

✅ **GET** → Retrieve data from the server  
✅ **POST** → Send data to the server (create resource)  
✅ **PUT** → Update/replace a resource  
✅ **PATCH** → Partially update a resource  
✅ **DELETE** → Remove a resource

🚀 **HTTP methods define actions for web communication!**

## 9., How does the GET method differ from the POST method? Explain when it is appropriate to use each method. Which one uses request body to send data? What the other method uses to send data?

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

## 10., Explain the use of the PATCH method in HTTP. How does it differ from the PUT method, and when should it be used to update a resource?

✅ **PATCH** → Partially updates a resource  
✅ **PUT** → Fully replaces a resource

### Key Differences:

| Feature       | PATCH                  | PUT                     |
| ------------- | ---------------------- | ----------------------- |
| **Purpose**   | Update specific fields | Replace entire resource |
| **Data Sent** | Only changed fields    | Full resource data      |
| **Use Case**  | Small modifications    | Complete updates        |

🚀 **Use PATCH for partial updates, PUT for full replacements!**

## 11., How can the DELETE method be used to remove a resource from a server? Explain how the DELETE method works and any considerations for handling resource deletion.

✅ **DELETE** → Removes a resource from the server.

### How It Works:

1. Client sends a `DELETE` request to the server.
2. Server processes and removes the specified resource.
3. Server responds with **200 OK**, **204 No Content**, or **404 Not Found** if the resource doesn’t exist.

### Considerations:

-   **Irreversible** → Ensure confirmation before deleting.
-   **Authorization Required** → Protect sensitive data with authentication.

## 12., How do you handle form submissions using JavaScript? Explain the process of capturing form data and preventing the default form submission behavior.

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

## 13., Explain the required elements necessary to define a form in HTML.

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

## 14., What is the purpose of the required attribute in HTML form elements? How does it enforce mandatory input fields and prevent form submission without the required information?

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

## 15., Explain the different types of form input fields available in HTML. How do input types like text, number, email, checkbox, and radio buttons differ, and how are they used in forms?

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

## 16., Can you explain the purpose of the name attribute in a context of form submission?

-   The `name` attribute in form elements identifies the input fields and is essential for form submission. When a form is submitted, the browser sends key-value pairs where the `name` is the key, and the input value is the value.

### **Example:**

```html
<input type="text" name="username" value="JohnDoe" />
```

-   Submits as **`username=JohnDoe`** in the request.

-   Without `name`, the field's data won't be included in form submissions. It is crucial for server-side processing and retrieving form data.

---

## 17., Can you explain how we can connect a label tag to a form element?

### 🔗 Connecting `<label>` to Form Elements

1️⃣ **Using `for` attribute (recommended):**

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username" />
```

✔ Links label to input by matching `for` and `id`  
✔ Clicking label focuses the input

2️⃣ **Wrapping input inside `<label>`:**

```html
<label>Username: <input type="text" name="username" /></label>
```

✔ Works without `id`, still focuses input

✅ **`for` attribute = better accessibility**

---

## 18., How can you dynamically manipulate or modify form elements using JavaScript? Explain how to add or remove form fields dynamically based on user interaction or specific conditions.

### ✨ Dynamic Form Manipulation with JavaScript

📥 **Add Input Field:**

```js
const form = document.getElementById("form");
const newInput = document.createElement("input");
newInput.type = "text";
newInput.name = "dynamicField";
form.appendChild(newInput);
```

❌ **Remove Input Field:**

```js
const inputToRemove = document.getElementById("inputId");
inputToRemove.remove();
```

⚡ **Add on Click (Event Listener):**

```js
document.getElementById("addBtn").addEventListener("click", () => {
    const input = document.createElement("input");
    input.type = "text";
    document.getElementById("form").appendChild(input);
});
```

✅ Use **event listeners** to add/remove fields based on user actions.

---

## 19., How can you convert form data into a format that can be easily transmitted or processed by the server?

### 📤 Converting Form Data for Server

1️⃣ **URL-encoded (default HTML form):**

```js
const formData = new URLSearchParams(new FormData(formElement)).toString();
```

2️⃣ **JSON (for APIs):**

```js
const formObject = Object.fromEntries(new FormData(formElement).entries());
const jsonData = JSON.stringify(formObject);
```

3️⃣ **FormData (for files/multipart):**

```js
const formData = new FormData(formElement);
```

✅ Choose format based on **server requirements**

---

# -- React --

## 1., What is React.js and what are its key features?

**React.js** = JavaScript library for building **UI**  
⚛️ **Key Features:**

-   🔁 **Components** → Reusable UI blocks
-   ⚡ **Virtual DOM** → Fast UI updates
-   📜 **JSX** → HTML-like syntax in JS
-   🔄 **One-way Data Flow** → Predictable state
-   🛠️ **Declarative** → Clear & simple code

---

## 2., Explain the concept of virtual DOM and how it contributes to React's performance.

**Virtual DOM** = Lightweight copy of the real DOM

⚙️ **How it boosts performance:**

1. 📝 Changes update the **Virtual DOM** first
2. 🔍 React compares it with the previous version (**diffing**)
3. 🎯 Only real DOM parts that changed are updated (**efficient updates**)

➡️ Result: **Faster, smoother UI rendering**

---

## 3., Explain the component-based architecture in React.js. How do components work, and how can they be composed to build complex user interfaces?

**Component-Based Architecture** = UI built from **independent, reusable pieces**

🔧 **How components work:**

-   📦 Each component = a small UI block (with its own logic, HTML & styling)
-   🔄 Can receive **props** (inputs) & manage **state** (internal data)

🏗️ **Composing UI:**

-   🔲 **Small components** → combined into **larger ones**
-   🧩 Like building blocks → create **complex interfaces** easily

---

## 4., What is the significance of JSX in React.js? Explain how JSX combines HTML-like syntax with JavaScript code and how it is transpiled into regular JavaScript during the build process.

**JSX** = HTML-like syntax inside **JavaScript**

💡 **Why it matters:**

-   📝 Makes UI code more **readable & intuitive**
-   💬 Lets you write **HTML + JS logic together**

⚙️ **Behind the scenes:**

-   🔁 JSX is **transpiled (via Babel)** → into **regular JS (`React.createElement`)**
-   📦 Helps React build the **UI structure efficiently**

---

## 5., What are props in React and how are they used to pass data between components? Explain the concept of props and how they facilitate parent-child component communication.

**Props** = **Inputs** passed from a **parent** to a **child** component

📦 Used to:

-   Send **data or functions** to child components
-   Make components **dynamic & reusable**

🔗 **Parent → Child Communication:**

```jsx
<ChildComponent title="Hello" />
```

➡️ **ChildComponent receives:** `props.title = "Hello"`

✅ **Props are read-only:** cannot be modified by the child

---

## 6., How can you access and utilize props within a functional component in React? Explain how to extract and use props using the destructuring syntax.

📥 **Accessing props in a functional component:**

```jsx
function Greeting(props) {
    return <h1>Hello, {props.name}</h1>;
}
```

🔓 **Destructuring props:**

```jsx
function Greeting({ name }) {
    return <h1>Hello, {name}</h1>;
}
```

✅ **Cleaner & easier to read** when using multiple props

---

## 7., How can you pass callback functions as props in React? Provide an example of how to pass a function from a parent component to a child component, enabling the child to communicate with the parent.

🔁 **Passing callback functions as props** = lets **child trigger actions in parent**

📦 **Parent → Child:**

```jsx
function Parent() {
    const handleClick = () => alert("Clicked!");
    return <Child onClick={handleClick} />;
}
```

👶 **Child uses the function:**

```jsx
function Child({ onClick }) {
    return <button onClick={onClick}>Click Me</button>;
}
```

✅ **Enables parent-child communication**

---

## 8., Explain the concept of spreading props in React. How can the spread operator be used to pass multiple props from a parent component to a child component in a concise manner?

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

---

## 9., Explain the concept of default props (with ES6 JS syntax) in React. How can you define default values for props in a component to handle cases where the prop value is not explicitly passed?

**Default props** are fallback values used when a prop is not passed to a component.

✅ **ES6 Syntax:**
You can define defaults directly in the function parameters:

```jsx
function Greeting({ name = "Guest" }) {
    return <h1>Hello, {name}!</h1>;
}
```

✅ Helps avoid **undefined values** and keeps components more **robust and predictable**.

---

## 10., Explain the immutability principle when working with props and states in React. Why is it important to avoid directly modifying prop values within a component, and what are some best practices for maintaining immutability?

In React, **props and state should not be modified directly**. Instead, always create a **new copy** when updating state to maintain **immutability**.

✅ **Why it matters:**  
Immutability helps React detect changes and trigger efficient re-renders.

✅ **Best practices:**

-   Use spread syntax (`...`) to update objects or arrays
-   Never modify props directly

---

## 11., How does React.js handle state management? Explain the concept of state and how it differs from props.

**State** holds dynamic, local data in a component and can change over time using hooks like `useState`.  
**Props** are read-only values passed from parent to child.

✅ **Key Difference:**

-   **State**: Internal, changeable.
-   **Props**: External, read-only.

---

## 12., What are React hooks? Explain the purpose and benefits of hooks like useState, useEffect in React.js.

**React Hooks** = Functions that add **state** and **lifecycle features** to functional components

### 🔧 Common Hooks:

-   **`useState`** → Manage local state
-   **`useEffect`** → Handle side effects (fetching, DOM, etc.)

✅ **Benefits:**

-   Cleaner, readable code
-   Reusable logic (custom hooks)
-   No class components needed
-   Better lifecycle handling

---

## 13., Explain the concept of virtual DOM reconciliation in React.js. How does React efficiently update and render components by performing minimal DOM manipulations?

**Virtual DOM** = Lightweight copy of the real DOM used by React

🔁 On state/prop change:

-   React creates a **new Virtual DOM**
-   Compares it with the **old one** (**diffing**)
-   Updates only the **changed parts** in the real DOM (**reconciliation**)

✅ Faster updates → **Better performance & smoother UI**

---

## 14., Explain how to manage complex state objects with useState. Explain techniques like object spreading or merging to update specific properties within an object state.

### 🔄 Managing Complex State in `useState`

❌ **Avoid direct mutation** → Always create a **new object reference**

✅ **Use object spread to update specific properties:**

```jsx
const [user, setUser] = useState({ name: "Alice", age: 25 });

setUser({ ...user, age: 26 }); // Updates age, keeps name
```

📌 **For deeply nested state**, use multiple spreads or consider **`useReducer`** for better management.

---

## 15., Why is it important to provide a new array as an argument to the useState hook when adding an item to an existing array?

In React, state updates must be **immutable** to ensure React detects changes and re-renders the component. Directly modifying the existing array (e.g., using `push()`) does not create a new reference, so React may not recognize the update.

✅ Instead, create a **new array** using spread syntax or array methods:

```jsx
setItems([...items, newItem]);
```

---

## 16., How does conditional rendering work in React? Explain the different techniques and approaches available to conditionally render components or content based on certain conditions or state values. How can it be used to control the visibility or behavior of components based on user interactions or other dynamic conditions?

### 🔀 Conditional Rendering in React

Render content **based on conditions (state/props)**

### ✅ Common Techniques:

1️⃣ **if/else (outside JSX):**

```jsx
if (isLoggedIn) return <Dashboard />;
else return <Login />;
```

2️⃣ **Ternary operator (inline):**

```jsx
{
    isLoggedIn ? <Dashboard /> : <Login />;
}
```

3️⃣ **Logical AND (`&&`):**

```jsx
{
    isAdmin && <AdminPanel />;
}
```

📌 **Use Cases:**

-   Show/hide content
-   Display loaders or errors
-   Switch views (e.g., login vs dashboard)

---

## 17., How can you create a select input element in React? How does it differ from the html's select tag? Can you show an example of a controlled and an uncontrolled select element with default value setting?

### 🔽 Controlled vs Uncontrolled `<select>` in React

#### ✅ **Controlled Select (React state manages value):**

```jsx
const [option, setOption] = useState("apple");

<select value={option} onChange={(e) => setOption(e.target.value)}>
    <option value="apple">Apple</option>
    <option value="banana">Banana</option>
    <option value="orange">Orange</option>
</select>;
```

#### ❎ **Uncontrolled Select (DOM manages value):**

```jsx
<select defaultValue="banana">
    <option value="apple">Apple</option>
    <option value="banana">Banana</option>
    <option value="orange">Orange</option>
</select>
```

### 🔑 Key Difference:

-   **Controlled** → `value` + `onChange` = **React-controlled**
-   **Uncontrolled** → `defaultValue`, no state tracking (React doesn't manage updates)

---

# -- Database --

## 1., What is MongoDB, and how does it differ from traditional relational databases? Explain the key features and advantages of MongoDB as a NoSQL database solution.

### 📦 MongoDB Overview

**MongoDB** = NoSQL, document-based database using **BSON (JSON-like)** format

### 🔍 Key Differences from RDBMS:

-   📄 **Schema-less** → Flexible structure (no fixed columns)
-   ⚡ **Horizontal scalability** → Sharding support
-   🔍 **Rich queries & indexing** → Powerful data access
-   🔗 **No Joins** → Uses **embedded documents**

### ✅ Advantages:

-   ⚡ Fast read/write performance
-   🔄 Flexible & scalable (great for big data, real-time apps)
-   💬 JSON-like data → Easy JS integration
-   🛡️ High availability via **automatic failover & replication**

---

## 2., Explain the concept of collections and documents in MongoDB? How does MongoDB store data, and how is it organized within collections and documents.

### 📂 MongoDB: Collections & Documents

-   **Document** = JSON-like BSON object  
    👉 Example: `{ name: "USA", population: 331000000 }`

-   **Collection** = Group of related documents (like a table, but **schema-less**)

### 📦 Data Storage & Organization:

-   Data stored in **flexible documents**
-   **Collections** hold similar data without fixed structure
-   Uses **index-based engine** for fast retrieval
-   Supports **embedded** (nested) & **referenced** (linked) document relationships

---

## 3., What is Mongoose.js, and how does it simplify working with MongoDB in a Node.js environment? Explain the key features and benefits of using Mongoose.js.

### 🧠 Mongoose.js Overview

**Mongoose** = ODM (Object Data Modeling) library for **MongoDB + Node.js**

### 🔑 Key Features:

-   📐 **Schema Definition** → Structured data models
-   ✅ **Validation** → Checks data before saving
-   🔄 **Middleware (Hooks)** → Pre/post processing (e.g., hash passwords)
-   🔍 **Query Builder** → Easy CRUD operations
-   🧮 **Virtuals & Methods** → Add computed fields & custom functions

### ✅ Benefits:

-   Cleaner, maintainable code
-   Ensures data consistency
-   Works great with **async/await**
-   Supports **relationships & population**

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

✅ **MERN Stack** = Full JavaScript solution for web apps

-   **MongoDB** → NoSQL database (flexible storage)
-   **Express.js** → Backend routing & API handling
-   **React.js** → Dynamic user interfaces
-   **Node.js** → Server-side JavaScript

✅ **Benefits:**

-   Fast development
-   Reusable components
-   Scalable architecture
-   One language across entire stack

---

## 6., How does data flow in the MERN stack architecture? Explain how the frontend, built with React.js, communicates with the backend, developed with Node.js and Express.js, to handle client requests and serve data from the MongoDB database.

✅ In the **MERN stack**, data flows like this:

➡️ **React (Client)** → `fetch` → **Express (API)** → **MongoDB (via Mongoose)** → Response → **React (UI update)**

📦 React sends requests → Express handles logic → MongoDB stores/fetches data → Response sent back

✅ Full-stack JS across **Frontend + Backend + Database**
