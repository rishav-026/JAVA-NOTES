
Conditional Rendering , Event handling , form handling , Two -way Binding , Props drilling , 
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

# Event Handling in React 
**Event Handling** in React means **responding to user actions** like:
- Clicking buttons
- Typing in input fields
- Submitting forms
- Hovering mouse
**Event handling is the process of handling user actions like clicks, inputs, and submissions in React.**
###  Why We Use Event Handling
We use events to:
 - Handle button clicks  
 - Get user input  
 - Submit forms  
 - Show messages  
 - Update UI
Example:
```js
<button onClick={handleClick}>  
  Click Me  
</button>
```
#  onClick Event 
Used when user clicks a button.
## Example — Button Click

```js
import React from "react";  
function App() {  
  const handleClick = () => {  
    alert("Button Clicked!");  
  };  
  return (  
    <>  
      <button onClick={handleClick}>  
        Click Me  
      </button>  
    </>  
  );  
}  
export default App;
```
# Two-Way Binding in React
**Two-way binding** means:
**Data flows in both directions**

```
UI ↔ State
```
- Input changes → state updates
- State changes → UI updates
#### How Two-Way Binding Works in React
```
 React uses :  value + onChange
```
- `value` → state → UI
- `onChange` → UI → state
Example :
```js
const [email, setEmail] = useState("");
<input
  type="email"
  value={email}
  onChange={(e) => setEmail(e.target.value)}
/>
```
### What is Form Handling?
Form handling is the process of controlling form inputs using state and handling submission.
#### Form Submission
Use `onSubmit` + `preventDefault()`
```js
const handleSubmit = (e) => {  e.preventDefault(); 
 console.log(name);};
```
preventDefault : It prevents the browser from performing its default action like the page reloading.
##### Example :Form handling + Two-way Binding
```js
import React, {useState} from 'react'
const App = () => {
  const [username , setUsername]= useState("")
  const submitHandler = (e)=>{
    e.preventDefault();
  }
  return(
    <div>
      <form onSubmit ={(e)=>{
        submitHandler(e)
        console.log(username);
      }}>
        <input
        value={username}
        onChange ={(e)=>{
          setUsername(e.target.value);
        }}
        className = 'px-4 rounded py-3 text-xl m-5'
        type ="text"
        placeholder ="Enter your name"
        />
        <button className = 'px-4 rounded py-3 text-xl m-5 bg-blue-500 text-white' type='submit'>Submit</button>
      </form>
    </div>
  )
}
export default App
```
# Props Drilling in React
Props Drilling means passing data from a parent component to a deeply nested child component through multiple intermediate components.

It happens when:
 - Data is needed in a deeply nested component  
 - But state exists in a top-level (parent) component
So we pass data like:
```
Parent → Child → Grandchild → Deep Child
```
## Example of Props Drilling
#### Parent Component
```js
function App() {  const name = "Rishav";  return <Parent name={name} />;}
```
#### Intermediate Component
```js
function Parent({ name }) {  return <Child name={name} />;}
```
#### Another Intermediate
```js
function Child({ name }) {  return <GrandChild name={name} />;}
```
#### Final Component
```js
function GrandChild({ name }) {  return <h1>{name}</h1>;}
```
####  Flow
```js
App → Parent → Child → GrandChild
```

Even if only **GrandChild needs the data**, all components must pass it.
### Problem with Props Drilling
Props drilling can cause:
-  Too much repetitive code  
-  Hard to maintain  
-  Difficult to debug  
-  Unnecessary props in middle components
#### Solution to Props Drilling :  Context API











# Axios in React
- **Axios** is a **JavaScript library** used to **make HTTP requests** (API calls).
- **Axios is used to fetch or send data from/to a server.
- ```js
  import axios from "axios";
   axios.get("https://api.example.com/data")
  .then(res => console.log(res.data))
  .catch(err => console.log(err));
  ```
Example :
```js
import React, { useState, useEffect } from "react";
import axios from "axios";
function App() {
  const [images, setImages] = useState([]);
  const [loading, setLoading] = useState(true);
  useEffect(() => {
    axios.get("https://picsum.photos/v2/list?page=1&limit=50")
      .then((res) => {
        setImages(res.data);
        setLoading(false);
      })
      .catch((err) => {
        console.log(err);
        setLoading(false);
      });
  }, []);
  return (
    <div style={{ padding: "20px" }}>
      <h1>50 Lorem Ipsum Images</h1>
      {loading ? (
        <h2>Loading...</h2>
      ) : (
        <div style={{
          display: "grid",
          gridTemplateColumns: "repeat(auto-fill, minmax(200px, 1fr))",
          gap: "15px"
        }}>
          {images.map((img) => (
            <img
              key={img.id}
              src={img.download_url}
              alt="random"
              style={{ width: "100%", height: "200px", objectFit: "cover" }}
            />
          ))}
        </div>
      )}
    </div>
  );
}
export default App;
```
Flow:
```
Component loads
   ↓
useEffect runs
   ↓
Axios fetches data
   ↓
Data stored in state
   ↓
UI re-renders
   ↓
Images displayed
```
