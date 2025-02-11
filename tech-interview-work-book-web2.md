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

-   answer

### 8., Compare the CommonJS and ES6 "modules". What are the differences?

-   answer

### 9., What are higher-order functions in JavaScript?

-   answer

### 10., Explain the purpose and functionality of the map function in JavaScript. How does it differ from the filter and reduce functions?

-   answer

### 11., How can the filter function be used to selectively extract elements from an array based on a given condition? Provide an example where the filter function is used to create a new array with only the elements that meet the specified criteria.

-   answer

### 12., What is the role of the reduce function in JavaScript? How can it be used to aggregate or combine the elements of an array into a single value? Provide an example where the reduce function is used to calculate a cumulative sum or find the maximum value in an array.

-   answer

## Fetch

### 1., How does a query string parameter in a URL contribute to web application functionality? Explain how query string parameters are typically used to pass data between web pages or APIs.

-   answer

### 2., What is the purpose and functionality of the fetch function in JavaScript?

-   answer

### 3., Explain the syntax of the fetch function and how it handles asynchronous operations. Compare and contrast the syntax of making HTTP requests using fetch with async/await versus the syntax using .then() and .catch(). What are the key differences and benefits of using the async/await syntax in terms of code structure and readability?

-   answer

### 4., What is asynchronicity in JavaScript? Name some typical use cases when asynchronicity is needed.

-   answer

### 5., How can you handle the response received from a fetch request?

-   answer

### 6., How does the fetch function handle errors and handle HTTP status codes? Provide an example of using fetch to handle different types of responses, including successful and error responses.

-   answer

### 7., Explain the parts of an URL.

-   answer

## Serve

### 1., Explain the concept of client-server communication in the context of web development. How does information flow between the client and the server in a typical client-server architecture?

-   answer

### 2., What is the role of HTTP requests and responses in web development? Explain the structure of an HTTP request and an HTTP response.

-   answer

### 3., Explain the key differences between the CommonJS require syntax and the ECMAScript (ES) module syntax import. How do these two approaches handle module dependencies and exports in JavaScript?

-   answer

### 4., What are the advantages of using the ES module syntax import over the CommonJS require syntax?

-   answer

### 5., What is Express.js and how does it simplify web application development in Node.js? Explain the core features and benefits of using Express.js as a web framework.

-   answer

### 6., Explain the process of handling static files (e.g., CSS, images) in Express.js. How can you configure Express.js to serve static assets from a specific directory in your application?

-   answer

### 7., How does Express.js handle HTTP request/response cycles? Explain the process of receiving and responding to requests using Express.js middleware and route handlers.

-   answer

## Forms

### 1., How does routing work in Express.js? Explain how to define routes and handle different HTTP methods (GET, POST, etc.) in an Express.js application.

-   answer

### 2., What are the various methods available in Express.js for sending responses to clients? Explain the differences between res.send() and res.json[] in Express.js.

-   answer

### 3., Explain what the express.json() middleware does?

-   answer

### 4., What is the purpose of the next() function in Express.js middleware? How can you use it to pass control to the next middleware function in the chain or to terminate the middleware processing?

-   answer

### 5., Explain the concept of route parameters in Express.js. How can you extract dynamic values from the URL path using route parameters, and how are these values accessed within route handlers?

-   answer

### 6., Can you name some typical HTTP response codes and their meaning?

-   answer

### 7., Can you name some typical HTTP request/response headers and their meaning?

-   answer

### 8., What are the common HTTP methods used in web development, and what are their respective purposes?

-   answer

### 9., How does the GET method differ from the POST method? Explain when it is appropriate to use each method. Which one uses request body to send data? What the other method uses to send data?

-   answer

### 10., Explain the use of the PATCH method in HTTP. How does it differ from the PUT method, and when should it be used to update a resource?

-   answer

### 11., How can the DELETE method be used to remove a resource from a server? Explain how the DELETE method works and any considerations for handling resource deletion.

-   answer

### 12., How do you handle form submissions using JavaScript? Explain the process of capturing form data and preventing the default form submission behavior.

-   answer

### 13., Explain the required elements necessary to define a form in HTML.

-   answer

### 14., What is the purpose of the required attribute in HTML form elements? How does it enforce mandatory input fields and prevent form submission without the required information?

-   answer

### 15., Explain the different types of form input fields available in HTML. How do input types like text, number, email, checkbox, and radio buttons differ, and how are they used in forms?

-   answer

### 16., Can you explain the purpose of the name attribute in a context of form submission?

-   answer

### 17., Can you explain how we can connect a label tag to a form element?

-   answer

### 18., How can you dynamically manipulate or modify form elements using JavaScript? Explain how to add or remove form fields dynamically based on user interaction or specific conditions.

-   answer

### 19., How can you convert form data into a format that can be easily transmitted or processed by the server?

-   answer

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

-   answer

### 9., Explain the concept of default props (with ES6 JS syntax) in React. How can you define default values for props in a component to handle cases where the prop value is not explicitly passed?

-   answer

### 10., Explain the immutability principle when working with props and states in React. Why is it important to avoid directly modifying prop values within a component, and what are some best practices for maintaining immutability?

-   answer

### 11., How does React.js handle state management? Explain the concept of state and how it differs from props.

-   answer

### 12., What are React hooks? Explain the purpose and benefits of hooks like useState, useEffect in React.js.

-   answer

### 13., Explain the concept of virtual DOM reconciliation in React.js. How does React efficiently update and render components by performing minimal DOM manipulations?

-   answer

### 14., Explain how to manage complex state objects with useState. Explain techniques like object spreading or merging to update specific properties within an object state.

-   answer

### 15., Why is it important to provide a new array as an argument to the useState hook when adding an item to an existing array?

-   answer

### 16., How does conditional rendering work in React? Explain the different techniques and approaches available to conditionally render components or content based on certain conditions or state values. How can it be used to control the visibility or behavior of components based on user interactions or other dynamic conditions?

-   answer

### 17., How can you create a select input element in React? How does it differ from the html's select tag? Can you show an example of a controlled and an uncontrolled select element with default value setting?

-   answer

## Database

### 1., What is MongoDB, and how does it differ from traditional relational databases? Explain the key features and advantages of MongoDB as a NoSQL database solution.

-   answer

### 2., Explain the concept of collections and documents in MongoDB? How does MongoDB store data, and how is it organized within collections and documents.

-   answer

### 3., What is Mongoose.js, and how does it simplify working with MongoDB in a Node.js environment? Explain the key features and benefits of using Mongoose.js.

-   answer

### 4., How do you define and create schemas in Mongoose.js? Explain how schemas define the structure and validation rules for documents in MongoDB collections.

-   answer

### 5., Explain the different types of Mongoose.js data modeling techniques. How can you define relationships between MongoDB collections using Mongoose.js, such as one-to-one, one-to-many, and many-to-many relationships?

-   answer

### 6., What are the available options for querying and manipulating data using Mongoose.js? Explain how to perform CRUD operations (create, read, update, delete) using Mongoose.js methods and queries.

-   answer

### 7., Explain the process of connecting to a MongoDB database using Mongoose.js. How can you configure and establish a connection to a MongoDB server using Mongoose.js in a Node.js application?

-   answer

## MERN

### 1., Explain the concept of React Router. How does it enable client-side routing in React.js applications and facilitate the creation of multi-page-like experiences?

-   answer

### 2., Explain the concept of server-side routing in Express.js. How does Express handle incoming requests and route them to the appropriate API endpoints or route handlers?

-   answer

### 3., What is the MERN stack? Explain the individual components of the MERN stack and their role in building web applications.

-   answer

### 4., Explain how does a proxy works during React development. How can you tell the webpack dev server to proxy the requests to your backend? What kind of URLs you have to use in the fetch in your JS code, if you want to use the proxy.

-   answer

### 5., Explain the advantages and benefits of using the MERN stack for web development. How does each component of the MERN stack contribute to the development process and overall efficiency of building modern web applications?

-   answer

### 6., How does data flow in the MERN stack architecture? Explain how the frontend, built with React.js, communicates with the backend, developed with Node.js and Express.js, to handle client requests and serve data from the MongoDB database.

-   answer

```

```
