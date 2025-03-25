## **🔹 What is an Event in React?**  
👉 **React Event হলো ইউজারের Action-এর (Click, Input, Hover, etc.) প্রতিক্রিয়া।**  
👉 **React-এ Event Handling হয় JavaScript-এর মতো, তবে Event Name CamelCase (`onClick`, `onChange`) ফরম্যাটে হয়।**  
👉 **Event Handler হিসেবে `function` ব্যবহার করতে হয়।**  
👉 **React-এ SyntheticEvent ব্যবহার করা হয়, যা Browser-এর Native Event-এর Wrapper।**  

---

## **📌 Handling Events in React 19**  

### **✅ Example 1: Handling Button Click Event**  
```jsx
const ButtonClick = () => {
  const handleClick = () => {
    alert("Button Clicked!");
  };

  return (
    <button onClick={handleClick}>Click Me</button>
  );
};

export default ButtonClick;
```
✅ **Button-এ `onClick` ইভেন্ট ব্যবহার করা হয়েছে।**  

---

## **📌 Passing Arguments to Event Handler**  
👉 **Event Handler-এ Parameter পাঠানোর জন্য `arrow function` ব্যবহার করা হয়।**  

### **✅ Example 2: Passing Parameters to Event Handler**
```jsx
const ButtonClick = () => {
  const showMessage = (name) => {
    alert(`Hello, ${name}!`);
  };

  return (
    <button onClick={() => showMessage("Shihab")}>Click Me</button>
  );
};

export default ButtonClick;
```
✅ **Function-এর মধ্যে Argument পাঠানোর জন্য `() =>` ব্যবহার করা হয়েছে।**  

---

## **📌 Event Object Handling**  
👉 **React-এর Event Object `e` দিয়ে Access করা যায়।**  

### **✅ Example 3: Handling Event Object**
```jsx
const InputEvent = () => {
  const handleChange = (e) => {
    console.log("Typed:", e.target.value);
  };

  return (
    <input type="text" onChange={handleChange} placeholder="Type something..." />
  );
};

export default InputEvent;
```
✅ **`onChange` ইভেন্ট ব্যবহার করে Input Field-এর Value Console-এ দেখানো হয়েছে।**  

---

## **📌 Handling Form Submit Event**  
👉 **Form Submit করলে Default Behavior (Page Reload) বন্ধ করতে `e.preventDefault()` ব্যবহার করা হয়।**  

### **✅ Example 4: Handling Form Submission**
```jsx
const FormSubmit = () => {
  const handleSubmit = (e) => {
    e.preventDefault();
    alert("Form Submitted!");
  };

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
};

export default FormSubmit;
```
✅ **`e.preventDefault()` ব্যবহার করে Page Reload হওয়া বন্ধ করা হয়েছে।**  

---

## **📌 Event Binding in Class Components** (React 19-এ Functional Component বেশি ব্যবহার হয়)  
👉 **Class Component-এ `this` Bind করতে হয়।**  

### **✅ Example 5: Event Binding in Class Component**
```jsx
import React, { Component } from "react";

class ClickEvent extends Component {
  constructor() {
    super();
    this.state = { message: "Hello!" };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({ message: "Button Clicked!" });
  }

  render() {
    return (
      <div>
        <h2>{this.state.message}</h2>
        <button onClick={this.handleClick}>Click Me</button>
      </div>
    );
  }
}

export default ClickEvent;
```
✅ **Class Component-এ `this.handleClick = this.handleClick.bind(this);` ব্যবহার করা হয়েছে।**  

---

## **📌 Handling Mouse Events**  
👉 **Mouse ইভেন্টগুলো হলো: `onMouseEnter`, `onMouseLeave`, `onMouseMove` ইত্যাদি।**  

### **✅ Example 6: Handling Mouse Events**
```jsx
const MouseEvent = () => {
  const handleMouseEnter = () => {
    console.log("Mouse Entered!");
  };

  return (
    <div onMouseEnter={handleMouseEnter} style={{ padding: "20px", backgroundColor: "lightgray" }}>
      Hover over this box
    </div>
  );
};

export default MouseEvent;
```
✅ **Mouse Hover করলে Console-এ Message দেখা যাবে।**  

---

## **📌 Handling Keyboard Events**  
👉 **Keyboard ইভেন্টগুলো হলো: `onKeyDown`, `onKeyPress`, `onKeyUp` ইত্যাদি।**  

### **✅ Example 7: Handling Key Press Events**
```jsx
const KeyPressEvent = () => {
  const handleKeyPress = (e) => {
    console.log(`Key Pressed: ${e.key}`);
  };

  return (
    <input type="text" onKeyPress={handleKeyPress} placeholder="Press any key..." />
  );
};

export default KeyPressEvent;
```
✅ **Keyboard Button Press করলে Key Name Console-এ দেখা যাবে।**  

---

## **📌 Handling Toggle Event with State**  
👉 **Button ক্লিক করে কিছু Show/Hide করা যায়।**  

### **✅ Example 8: Toggle Event Handling**
```jsx
import { useState } from "react";

const ToggleEvent = () => {
  const [show, setShow] = useState(true);

  return (
    <div>
      <button onClick={() => setShow(!show)}>Toggle</button>
      {show && <h2>Hello, React!</h2>}
    </div>
  );
};

export default ToggleEvent;
```
✅ **Button ক্লিক করলে Element Show/Hide হবে।**  

---

## **📌 Fetching Data with Event Handling**  
👉 **Button ক্লিক করলে API থেকে Data Load করা যাবে।**  

### **✅ Example 9: Fetching Data on Button Click**
```jsx
import { useState } from "react";

const FetchData = () => {
  const [users, setUsers] = useState([]);

  const fetchUsers = async () => {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");
    const data = await response.json();
    setUsers(data);
  };

  return (
    <div>
      <button onClick={fetchUsers}>Load Users</button>
      <ul>
        {users.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default FetchData;
```
✅ **Button ক্লিক করলে API থেকে Data Fetch হবে।**  

---

## **📌 Conclusion**  
✔ **React-এ Event Handling সহজ এবং কার্যকর।**  
✔ **`onClick`, `onChange`, `onSubmit`, `onMouseEnter`, `onKeyPress` ইত্যাদি ইভেন্ট বেশি ব্যবহৃত হয়।**  
✔ **Functional Component-এ Event Handling সহজ, Class Component-এ `bind` করা লাগে।**  
✔ **React 19-এ `useState` ব্যবহার করে Event Handling আরও সহজ হয়েছে।**  
