# **🔹 What is a Component?**  
👉 **React Component** হলো **একটি ফাংশন** বা **ক্লাস** যা **UI রেন্ডার করে**।  
👉 প্রতিটি কম্পোনেন্ট **অন্য কম্পোনেন্টের মধ্যে ব্যবহার করা যায়**।  
👉 **Component-based Architecture** এর কারণে **কোড রিইউজযোগ্য, মেইন্টেইনেবল এবং স্কেলেবল** হয়।  

---

# **📌 Types of React Components**  
### ✅ **1️⃣ Functional Components (✅ Recommended)**
- এই কম্পোনেন্ট একটি **JavaScript ফাংশন** যা JSX রিটার্ন করে।  
- এটি `useState`, `useEffect` ইত্যাদি **React Hooks** ব্যবহার করতে পারে।  

### ❌ **2️⃣ Class Components (❌ Deprecated in React 19)**
- **React 19-এর পর থেকে Functional Component সবচেয়ে বেশি ব্যবহৃত হয়।**  

---

# **📌 Functional Component Example (React 19 Standard)**  
```jsx
const Greeting = () => {
  return <h1>Hello, React 19!</h1>;
};

export default Greeting;
```
✅ **এই কম্পোনেন্ট `Greeting` কে অন্য জায়গায় ব্যবহার করা যাবে।**  

### **📌 Using in App.js**
```jsx
import Greeting from "./Greeting";

const App = () => {
  return (
    <div>
      <Greeting />
    </div>
  );
};

export default App;
```

---

# **📌 Passing Data with Props**
👉 **Props (Properties)** ব্যবহার করে **এক কম্পোনেন্ট থেকে অন্য কম্পোনেন্টে ডাটা পাঠানো যায়।**  

### **📌 Example:**
```jsx
const Welcome = (props) => {
  return <h1>Welcome, {props.name}!</h1>;
};

const App = () => {
  return (
    <div>
      <Welcome name="Shihab" />
      <Welcome name="Omar" />
      <Welcome name="Siam" />
    </div>
  );
};

export default App;
```
✅ **Props immutable (পরিবর্তন করা যায় না)।**  

---

# **📌 State in Functional Components**
👉 **State হলো একটি Component-এর Dynamic Data, যা পরিবর্তন হলে UI আপডেট হয়।**  
👉 **React 19-এর `useState` হুক ব্যবহার করে State তৈরি করা হয়।**  

### **📌 Example: Counter Component**
```jsx
import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
};

export default Counter;
```
✅ **State পরিবর্তন হলে React UI আপডেট করে।**  

---

# **📌 Event Handling in Components**
👉 **Button Click বা User Interaction** হ্যান্ডেল করতে ইভেন্ট ব্যবহার করা হয়।  

### **📌 Example: Button Click Event**
```jsx
const ClickHandler = () => {
  const handleClick = () => {
    alert("Button Clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
};

export default ClickHandler;
```

---

# **📌 List Rendering & Key Prop**
👉 **React-এ `.map()` ব্যবহার করে লিস্ট রেন্ডার করা হয়।**  
👉 **প্রতিটি লিস্ট আইটেমে `key` দেওয়া বাধ্যতামূলক!**  

### **📌 Example:**
```jsx
const users = ["Shihab", "Omar", "Siam"];

const UserList = () => {
  return (
    <ul>
      {users.map((user, index) => (
        <li key={index}>{user}</li>
      ))}
    </ul>
  );
};

export default UserList;
```
✅ **Key Prop না দিলে React Warning দেখাবে।**  

---

# **📌 Conditional Rendering in Components**
👉 **UI কন্ডিশন অনুযায়ী দেখাতে `if-else` বা `ternary operator` ব্যবহার করা হয়।**  

### **📌 Example:**
```jsx
const UserStatus = ({ isLoggedIn }) => {
  return isLoggedIn ? <h2>Welcome Back!</h2> : <h2>Please Login</h2>;
};
```
✅ **Props দিয়ে ভিন্ন UI দেখানো যায়।**  

---

# **📌 Fetching Data in Components (React 19 Style)**
👉 **React 19-এর `use` হুক ব্যবহার করে সহজে API থেকে ডাটা লোড করা যায়।**  

### **📌 Example: Fetching Users List**
```jsx
import { use } from "react";

const fetchUsers = async () => {
  return fetch("https://jsonplaceholder.typicode.com/users")
    .then((res) => res.json());
};

const Users = () => {
  const users = use(fetchUsers());

  return (
    <div>
      <h2>Users List</h2>
      <ul>
        {users.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default Users;
```
✅ **React 19-এর `use` হুক ব্যবহার করে সহজেই ডাটা লোড করা যায়।**  

---

# **📌 Parent & Child Components**
👉 **Parent Component এর মধ্যে Child Component ব্যবহার করা হয়।**  

### **📌 Example:**
```jsx
const Child = ({ message }) => {
  return <h2>{message}</h2>;
};

const Parent = () => {
  return (
    <div>
      <Child message="Hello from Parent Component!" />
    </div>
  );
};

export default Parent;
```
✅ **Parent থেকে Data Child-এ পাঠানো সহজ।**  

---

# **📌 Reusable Components**
👉 **একই Component একাধিক জায়গায় ব্যবহার করা যায়।**  

### **📌 Example:**
```jsx
const Button = ({ text }) => {
  return <button>{text}</button>;
};

const App = () => {
  return (
    <div>
      <Button text="Click Me" />
      <Button text="Submit" />
      <Button text="Delete" />
    </div>
  );
};

export default App;
```
✅ **একটি কম্পোনেন্ট বারবার ব্যবহার করা যায়।**  

---

# **📌 Conclusion:**
✔ **React Component হল Reusable UI Blocks**  
✔ **Props দিয়ে Parent থেকে Child-এ Data পাঠানো হয়**  
✔ **State ব্যবহারে Dynamic Data Handle করা যায়**  
✔ **Event Handling দ্বারা User Interaction Manage করা যায়**  
✔ **API Fetching সহজে করা যায় `use` Hook দিয়ে**  
✔ **React 19-এ Performance & Efficiency আরও উন্নত হয়েছে**  
