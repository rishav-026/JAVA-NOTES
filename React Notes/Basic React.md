React-Notes/  
│  
├── 01-Introduction  
├── 02-Setup  
├── 03-JSX  
├── 04-Components  
├── 05-Props  
├── 06-State  
├── 07-Events  
├── 08-Forms  
├── 09-Hooks  
├── 10-Routing  
├── 11-Styling  
├── 12-API  
├── 13-Context  
├── 14-Redux  
├── 15-Performance  
├── 16-Testing  
├── 17-Deployment  
├── 18-Advanced  
├── 19-TypeScript  
├── 20-Projects

## React Intro

**React** is a **JavaScript library** used to build **user interfaces (UI)**, especially for **single-page applications (SPA)**.
It allows developers to create **reusable UI components** and efficiently update the UI when data changes.
- Developed by → **Meta Platforms** (formerly Facebook)
- First released → **2013**
- Used by companies like:
    - **Facebook**
    - **Instagram**
    - **Netflix**
    - **Airbnb**
# Why We Need React (Short Answer)

We need **React** to build **fast, interactive, and maintainable user interfaces** efficiently.
###  Main Reasons to Use React

1️ **Component-Based Structure**  
React divides UI into **small reusable components**, making code easier to manage and reuse.

2️ **Fast Performance (Virtual DOM)**  
React uses a **Virtual DOM** to update only changed elements instead of reloading the whole page, which improves speed.

3️ **Reusable Code**  
Components can be reused multiple times, reducing duplicate code.

4️ **Easy UI Updates**  
React automatically updates the UI when data changes using **state**.

5️ **Better Code Maintenance**  
Large applications become easier to manage and debug.

# What is DOM?

##  Real DOM (Document Object Model)
**Real DOM** is the **actual webpage structure** created by the **browse**
**DOM** is a tree-like structure representing HTML elements.
Example:
```html
<html>  
  <body>  
    <h1>Hello</h1>
  </body>  
</html>
```

DOM Tree:
html  
 └── body  
      └── h1
Browser updates UI using the **Real DOM**.
#### React and React DOM
- React : It's an object of js. It's job is only to describe what the UI should look like . It doesn't create DOM elements .It create lightweight js objects that acts as a blueprint.
- React focuses on building UI components and managing UI logic

- React DOM: This is the renderer. It's job is only to take the blue print from react and build the UI for specific platform.
- React DOM is responsible for creating/updating real DOM elements and rendering these components in the browser.
- **React DOM** is a **library** that connects React with the **Real DOM**.

### Virtual DOM vs Real DOM (React DOM)

## What is React DOM?
**Real DOM ≠ React DOM**
**React DOM** is a **library** that allows React to interact with the **Real DOM** of the browser.

It is responsible for:
- Rendering React components into the browser
- Updating the Real DOM
- Managing UI changes

Example:
```javascript
import ReactDOM from "react-dom/client";  
ReactDOM.createRoot(document.getElementById("root")).render(  
  <App />  
);
```
 Here, **React DOM** renders the `App` component into the browser.
---
##  What is Virtual DOM?
**Virtual DOM** is a **lightweight copy of the Real DOM** stored in memory.

React uses Virtual DOM to:
1. Detect UI changes
2. Compare old and new Virtual DOM
3. Update only changed parts in Real DOM
This makes UI updates faster.

In Real DOM: If we want to change h1 tag then it reloads the whole window 
In virtual DOM: It makes multiple copies of the main and then change where we want to change ,then it compares with the original one . SO, it doesn't reload the whole window.
## In Virtual DOM:

1️ React creates Virtual DOM  
2️ Change happens (like updating `<h1>`)  
3️ React compares:
- Old Virtual DOM
- New Virtual DOM
4️ React updates **only changed elements** in Real DOM
This process is called:
 **Diffing**  
 **Reconciliation**

# JSX (JavaScript XML)

**JSX (JavaScript XML)** is a syntax extension for JavaScript that allows us to **write HTML-like code inside JavaScript**.
It makes React code **easier to read and write**.

Example:
```javascript
const element = <h1>Hello World</h1>;
```

Here:
- `<h1>Hello World</h1>` looks like HTML
- But it is actually **JSX**

#### Without JSX
```javascript
const element = React.createElement(  
  "h1",  
  null,  
  "Hello World"  
);//It is hard to read
```
---
#### With JSX
```javascript
const element = <h1>Hello World</h1>; 
//
Easy to read 
```
# How JSX Works Internally
JSX is **not understood directly by browsers**.
It is converted into JavaScript using **Babel**.
JSX:
```javascript
const element = <h1>Hello</h1>;
```
Converted to:
```javascript
const element = React.createElement(  
  "h1",  
  null,  
  "Hello"  
);
```

So:  JSX → JavaScript → Browser

# JSX Fragment
Fragment allows multiple elements **without adding extra div**.

Example:
```javascript
<>  
  <h1>Hello</h1>  
  <p>World</p>  
</>
```
```js
import React from "react";  
function App() {  
return (  
   <React.Fragment>  
      <h1>Hello</h1>  
      <p>World</p>  
   </React.Fragment>  
   );  
}
```
Why use Fragment?
- Avoid unnecessary `<div>`
- Keeps DOM clean

# React Components

##  What is a Component?
- A **Component** is a **reusable piece of UI** in React.
- It is like a **function** that returns JSX (UI).
- Components help divide the UI into **small, independent, reusable parts**.
---
####  Real-Life Exampl
Think of a website like:
```page
Website  
 ├── Navbar  
 ├── Sidebar  
 ├── Content  
 └── Footer
```
Each part is a **component**.
So instead of writing one large file, we create **multiple small components**.

---
#  Why Components are Used
Components make code: Reusable , Maintainable , Organized and easy to debug

Without components:
- Code becomes large
- Hard to manage
- Hard to reuse UI
---
###  Types of Components in React

There are **two main types**:
1️ Functional Components (Most Used)  
2️ Class Components (Older Method)

---
### 1️ Functional Components(Most used) 
A **Functional Component** is a **JavaScript function** that returns JSX.
This is the **modern and most used** way.
```js
function Welcome() {  
  return <h1>Hello World</h1>;  
}  
export default Welcome;
```
---
#### Using the Component
```js
import Welcome from "./Welcome";  
  
function App() {  
  return (  
    <>  
      <Welcome />  
    </>  
  );  
}//Output: Hello World
```
---
### 2️ Class Components
Class Components are the **older way** of creating components.
They use JavaScript classes.
Now mostly replaced by **Functional Components + Hooks**.

---
#### Example: Class Component
```js
import React from "react";  
class Welcome extends React.Component {  
  render() {  
    return <h1>Hello World</h1>;  
  }  
}  
export default Welcome;
```
#### Naming Rules for Components
Important rules:
 - Must start with **Capital Letter**  
 - Use **PascalCase**
Correct:
```page
Navbar  
UserProfile  
LoginForm
```
# Creating a Component (Step-by-Step)
#### Step 1: Create File
Example:   Navbar.jsx

---
#### Step 2: Write Component
```js
function Navbar() {  
  return <h1>Navbar</h1>;  
}  
  
export default Navbar;
```
---
#### Step 3: Import Component
```js
import Navbar from "./Navbar";
```
---
#### Step 4: Use Component
```js
function App() {  
  return (  
    <>  
      <Navbar />  
    </>  
  );  
}
```
# Reusable Components
Components can be used **multiple times**.

Example:
```js
function Button() {  
  return <button>Click</button>;  
}
```
Using multiple times:
```js
function App() {  
  return (  
    <>  
      <Button />  
      <Button />  
      <Button />  
    </>  
  );  
}
```
Output:
Click  
Click  
Click

---
#  Nested Components
A component inside another component.
Example:
```js
function Header() {  
  return <h1>Header</h1>;  
}  
function App() {  
  return (  
    <>  
      <Header />  
      <p>Welcome</p>  
    </>  
  );  
}
```
# Component Composition
Combining multiple components together.
Example:
```js
function Navbar() {  
  return <h1>Navbar</h1>;  
}  
function Footer() {  
  return <h1>Footer</h1>;  
}  
function App() {  
  return (  
    <>  
      <Navbar />  
      <Footer />  
    </>  
  );  
}
```
# Exporting Components
Used to make components available in other files.

---
##### Default Export
```js
export default Navbar;
```
Import:
```js
import Navbar from "./Navbar";
```
---
##### Named Export
```js
export function Navbar() {  
  return <h1>Navbar</h1>;  
}
```

Import:
```js
import { Navbar } from "./Navbar";
```

# Props in React
- **Props (short for Properties)** are used to **pass data from one component to another**.
- They allow components to be **dynamic and reusable**.
 - Props are passed from **Parent Component → Child Component**.
Think of props like **function arguments**.
```js
function greet(name) {  //Here , name is a argument and props in react
return "Hello " + name;  
}
```
#### Props Example :
###### Parent Component
```js
import React from "react";  
import User from "./User";  
  
const App = () => {  
  return (  
    <>  
      <User name="Rishav" age={22} />  
    </>  
  );  
};  
export default App;
```
---
###### Child Component
```js
import React from "react";  
const User = ({ name, age }) => {  
  return (  
    <>  
      <h1>{name}</h1>  
      <h2>{age}</h2>  
    </>  
  );  
};  
export default User;
```

### Some Keywords:
#### Compilers & Transpilers
##### Compiler
- Converts code from **high-level → low-level language**
##### Transpiler (Source-to-source compiler)
- Converts code between **two high-level languages**
- Example: Modern JS → Older JS
#### Babel
- Works as:
    -  Compiler
    -  Transpiler
---
####  Bundlers & Build Tools
##### Bundlers
- Used during development
- Combine multiple files into optimized output
**Examples:**
- Webpack
- Vite
---
### Vite
- Modern build tool
- Uses **ESBuild** (very fast )
- Reduces need for Babel in many cases
---
####  Browser Compatibility
##### Polyfills
- Used when a browser doesn't support a feature
**Example:**

```
let → var
```
---
#####  Webpack
- Helps bundle and optimize files
- Manages dependency versions
**Example Version:**

```
2.1 → 3.2.2
```
---
####  Node Modules & NPM
### node_modules
- Stores:
    - Third-party libraries
    - Dependencies
- Managed by **npm**
---
####  Versioning (Semantic Versioning)
**Example:**
```
^19.2.0
```
##### Breakdown
- **19 → Major**
- **2 → Minor**
- **0 → Patch**

---
####  Types of Updates

- 🐞 Bug Fix → Patch  
    `19.2.1`
- ✨ New Feature  → Minor  
    `19.3.0`
- ⚠️ Breaking Change → Major  
    `20.0.0`

>  Avoid major updates if stability is important
####  Version Symbols
#### Caret (^)
- Allows:
    - Minor updates
    - Patch updates
#### Tilde (~)
- Allows:  Only patch updates

---
####  Project Setup
```
npm init
```
---
####  React Imports
```
import React from "react";
import ReactDOM from "react-dom/client";
```
---
####  ES Modules in HTML
```
<script type="module"></script>
```
---
###  Build & Deployment

##### dist Folder
- Contains production-ready build files
##### Build Command
```
npm run build
```
**Output:**
- Optimized files
- Ready for deployment 🚀
---
####  Plugins
- Adds extra functionality to tools like Vite
---
**React:**
```
plugins: [react()]
```
**Vue:**
```
plugins: [vue()]
```
### node_modules
node_modules is a folder that stores **all installed packages (libraries)** required for the project.
```page
npm install  or npm install react
```
###  dependencies
Dependencies are packages required to **run the application in production**.
Example: `react`, `react-dom`, `axios`
```page
npm install package-name
```
###  devDependencies
**devDependencies** are packages required **only during development**, not in production.
Example: testing tools, build tools like `vite`
###  package.json
It is a file that stores **project information, scripts, and dependency details**.
```json
{
  "name": "my-app",
  "version": "1.0.0",
  "dependencies": {
    "react": "^18.0.0",
    "axios": "^1.0.0"
  },
  "devDependencies": {
    "vite": "^5.0.0"
  }
}
```
```json
"scripts": {  
"dev": "vite",  
"build": "vite build",  
"start": "vite preview"  
}
```
###  package-lock.json
package-lock.json is a file that stores the **exact versions of installed dependencies** to ensure consistent installation across systems.

NOTE : package.json stores project information and dependency names, while package-lock.json stores the exact versions of dependencies to ensure consistent installation across systems.




