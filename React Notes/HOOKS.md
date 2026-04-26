# React Hooks
Hooks are special **functions in React** that allow us to **use state and other React features inside functional components**.
Before Hooks, these features were only available in **class components**.
# Why We Use Hooks
Hooks are used to:
 - Add **state** to functional components  
 - Handle **side effects** (like API calls)  
 - Reuse logic between components  
 - Replace complex class components  
 - Make code simpler and cleaner
#### Example :
```js
import React from 'react'
const App = ()=> {
  let user ="Rishav";
  let age =22;
  const changeUser = ()=>{
    user="Rishav Kumar";
    age = 23;
    console.log( age);
  }
  return (
    <>
    <h1> hello</h1>
    <h1> {user} , {age}</h1>
    <h2 onClick ={changeUser}> {user} ,{age}</h2>
    <h3 onClick = {changeUser}> {age+1} </h3>
    </>
  )
}
export default App
```
This will not change the name and age in UI because we are changing into DOM not in react .
So , If i want to change the name from Rishav to Rishav Kumar then i have to use React Hooks - useState.
#### Example Using UseState Hooks:
```js
import React, { useState } from "react";
const App = () => {
  const [user, setUser] = useState("Rishav");
  const [age, setAge] = useState(22);
  const changeUser = () => {
    setUser("Rishav Kumar");
    setAge(23);
  };
  return (
    <>
      <h1>Hello</h1>
      <h1>{user}, {age}</h1>
      <h2 onClick={changeUser}>
        {user}, {age}
      </h2>
      <h3 onClick={changeUser}>
        {age + 1}
      </h3>
    </>
  );
};
export default App;
```
### Commonly Used Hooks
These are the most important Hooks:

| Hook            | Purpose              |
| --------------- | -------------------- |
| **useState**    | Manage state         |
| **useEffect**   | Handle side effects  |
| **useContext**  | Use context data     |
| **useRef**      | Access DOM elements  |
| **useMemo**     | Optimize performance |
| **useCallback** | Optimize functions   |

## 1.useState Hook:
useState is a React Hook that allows functional components to **store and update data (state)**.
Syntax:
```js
const [state, setState] = useState(initialValue);
```
Example 1:
```js
import React, { useState } from "react";
function App() {
  const [num,setNum] = useState(0);
return(
  <>
  <h3> Number is {num} </h3>
  <button onClick ={() => setNum(num+1)}>Increment</button>
  <button onClick ={() => setNum(num-1)}>Decrement</button>
  </>
)}
export default App;
```
Example 2:
```js
import React, { useState } from "react";
function ToggleExample() {
  const [show, setShow] = useState(false);
  const toggleText = () => {
    setShow(!show);
  };
  return (
    <>
      <h1>Toggle Example</h1>
      <button onClick={toggleText}>
        {show ? "Hide" : "Show"}
      </button>
      {show && <p>This text is now visible!</p>}
    </>
  );
}
export default ToggleExample;
```
### Why We Use useState
 - Store dynamic data  
 - Update UI automatically  
 - Handle user interactions  
 - Manage component data
Examples of state:
- Counter value
- User input
- Theme mode
- Toggle button
- API data

# 2. useEffect?
- **useEffect** is a React Hook used to **perform side effects** in functional components.
- useEffect is used to perform tasks after the component renders
###  What are Side Effects?
**Side effects** are operations that happen **outside normal rendering**.
Examples:
- API calls  
- Fetching data  
- Updating DOM  
- Timers (`setTimeout`)  
- Event listeners  
- Local storage operations
####  Why We Use useEffect
We use **useEffect** to:
 - Fetch data from API  
 - Run code after rendering  
 - Handle timers  
 - Add event listeners  
 - Update external systems
Syntax:
```js
useEffect(() => {
  // Side effect code here
}, []);
```
useEffect  -> Hook name
() => {}   -> function to run
[ ]   ->    Dependency array
The **dependency array** controls **when useEffect runs**.

```js
//Run Once (On Mount)
useEffect(() => {  
console.log("Runs once");  
}, []);
```
```js
//Run on Every Render
useEffect(() => {
  console.log("Runs every render");
});
```
```js
//Run When State(count) Changes
useEffect(() => {
  console.log("Runs when count changes");
}, [count]);
```

Example-1:Run Once
```js
import React, { useEffect } from "react";
function App() {
  useEffect(() => {
    console.log("Component Loaded");
  }, []);
  return <h1>Hello</h1>;
}
export default App;
```
Example-2: With State Dependency
```js
import React, { useState, useEffect } from "react";
function Counter() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    console.log("Count changed:", count);
  }, [count]);
  return (
    <>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </>
  );
}
export default Counter;
```

Example-3:API Call
```js
import React, { useState, useEffect } from "react";
function Users() {
  const [users, setUsers] = useState([]);
  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(data => setUsers(data));
  }, []);
  return (
    <>
      <h1>User List</h1>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </>
  );
}
export default Users;
```
# Cleanup Function 
- Used to **remove side effects**.
- **cleanup functions** are usually used when you need to **cancel ongoing work** like API calls, timers, or event listeners
Example:
 - Remove timers  
 - Remove event listeners
```js
useEffect(() => {
  // effect code
  return () => {
    // cleanup code
  };
}, []);
```
Example 1:
```js
import React, { useEffect } from "react";
function Timer() {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log("Running...");
    }, 1000);
    // Cleanup
    return () => {
      clearInterval(timer);
      console.log("Timer Stopped");
    };
  }, []);
  return <h1>Timer Running</h1>;
}
export default Timer;
```

Example 2 : API Call with Cleanup Function (Abort Fetch)
```js
import React, { useState, useEffect } from "react";
function Users() {
  const [users, setUsers] = useState([]);
  useEffect(() => {
    const controller = new AbortController();
    fetch("https://jsonplaceholder.typicode.com/users", {
      signal: controller.signal
    })
      .then(response => response.json())
      .then(data => setUsers(data))
      .catch(error => {
        if (error.name !== "AbortError") {
          console.log(error);
        }
      });
    // Cleanup Function
    return () => {
      controller.abort();
      console.log("Fetch Aborted");
    };
  }, []);
  return (
    <>
      <h1>User List</h1>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </>
  );
}
export default Users;
```
### When We Use Cleanup Function
Use cleanup when working with:
 - API requests  
 - Timers (`setInterval`, `setTimeout`)  
 - Event listeners  
 - Subscriptions  
 - WebSockets
# What is Conditional Rendering?

- Conditional Rendering means showing or hiding UI elements based on conditions.
- Just like if-else in JavaScript, React can render different UI depending on conditions.
- Conditional rendering is used to display different UI elements based on conditions.
###  Why We Use Conditional Rendering
We use it to:
 Show/Hide components  
 Display login/logout buttons  
 Show loading messages  
Display error messages  
 Toggle content
---
#   Using `if-else`
```js
import React, { useState } from "react";  
function App() {  
  const [isLoggedIn, setIsLoggedIn] = useState(true);  
  if (isLoggedIn) {  
    return <h1>Welcome User</h1>;  
  } else {  
    return <h1>Please Login</h1>;  
  }  
}  
export default App;
```
### Using Ternary 
 
Syntax:
```js
condition ? truePart : falsePart
```
Example:
```js
import React, { useState } from "react";  
function App() {  
  const [isLoggedIn, setIsLoggedIn] = useState(false);  
  return (  
    <>  
      <h1>  
        {isLoggedIn ? "Welcome User" : "Please Login"}  
      </h1>  
    </>  
  );  
}  
export default App;
```
### Using Logical AND (`&&`)
Used when showing something **only if condition is true**.
```js
import React, { useState } from "react";  
function App() {  
  const [show, setShow] = useState(true);  
  return (  
    <>  
      {show && <h1>Hello User</h1>}  
    </>  
  );  
}  
export default App;
```

