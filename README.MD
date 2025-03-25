React সম্পর্কে **একটি সম্পূর্ণ গাইড** চাও? আমি **React-এর বেসিক থেকে অ্যাডভান্স পর্যন্ত** প্রতিটি বিষয় কভার করবো, যাতে তুমি সহজেই **React Developer** হতে পারো! 🚀  

---

# **📌 React সম্পূর্ণ গাইড**  

## **🔹 React কি? (What is React?)**
**React** হলো **Facebook (Meta)** ডেভেলপ করা **একটি ফ্রন্ট-এন্ড JavaScript লাইব্রেরি** যা **UI (User Interface)** তৈরি করতে ব্যবহার করা হয়।  

✅ **React-এর কিছু বৈশিষ্ট্য:**  
✔ **Component-based Architecture** (কম্পোনেন্ট ভাগ করা যায়)  
✔ **Virtual DOM** (ফাস্ট এবং পারফরম্যান্স ভালো)  
✔ **One-way Data Binding** (ডাটা ম্যানেজমেন্ট সহজ)  
✔ **Reusable Components** (কোড রিপিট না করেও রিইউজ করা যায়)  
✔ **SEO Friendly** (সার্চ ইঞ্জিন অপটিমাইজেশন ভালো)  

---

# **🚀 React Installation & Setup**
React ব্যবহার করতে প্রথমে এটি ইন্সটল করতে হবে।  

## **📌 React Project তৈরি (Using Vite - Fastest Way)**  
```sh
npm create vite@latest my-app --template react
cd my-app
npm install
npm run dev
```
✅ **Vite কেন?**  
- এটি **Fast & Lightweight**।  
- **Webpack-এর তুলনায় 10x গতি বেশি**।  

---

# **🔹 JSX (JavaScript XML) – React-এর নিজস্ব Syntax**
JSX হলো **HTML-এর মতো একটি সিনট্যাক্স যা JavaScript-এর মধ্যে লেখা হয়।**  

### **📌 Example:**
```jsx
const heading = <h1>Hello, React!</h1>;
```
✅ **JSX-এর সুবিধা:**  
✔ HTML-এর মতো লেখা যায়  
✔ JavaScript-এর মধ্যে ব্যবহার করা যায়  

---

# **🔹 React Components – Reusable UI টুকরা**
React-এ সবকিছু **কম্পোনেন্ট-ভিত্তিক**। এটি **UI ভাগ করে** কোড রিপিট না করেও রিইউজ করা যায়।  

## **📌 দুই ধরনের কম্পোনেন্ট আছে:**
1️⃣ **Functional Component** ✅ *(সর্বাধিক ব্যবহৃত)*  
2️⃣ **Class Component** ❌ *(আগে ব্যবহৃত হতো, এখন কম)*  

### **📌 Functional Component Example:**
```jsx
const Greeting = () => {
  return <h1>Hello, React!</h1>;
};
export default Greeting;
```
✅ **এই কম্পোনেন্টকে যে কোনো পেজে ব্যবহার করা যাবে।**  

---

# **🔹 Props – Parent থেকে Child-এ ডাটা পাঠানো**  
Props ব্যবহার করে **কম্পোনেন্টের মধ্যে ডাটা পাস করা যায়।**  

### **📌 Example:**
```jsx
const Welcome = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};

const App = () => {
  return <Welcome name="Shihab" />;
};
export default App;
```
✅ **Props immutable (পরিবর্তন করা যায় না)।**  

---

# **🔹 State – Dynamic Data Handle করার জন্য React-এর Memory**
State হলো **কম্পোনেন্টের ভেতরের ডাটা**, যা পরিবর্তন হলে UI আপডেট হয়।  

### **📌 Example: Counter with `useState`**
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
✅ **State পরিবর্তন হলে UI আপডেট হয়।**  

---

# **🔹 Event Handling – User Interaction Handle করা**  
React-এ **onClick, onChange, onSubmit** ইত্যাদি ইভেন্ট হ্যান্ডলার ব্যবহার করা হয়।  

### **📌 Example:**
```jsx
const App = () => {
  const handleClick = () => {
    alert("Button Clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
};
export default App;
```
✅ **Event Trigger করলে Function Execute হয়।**  

---

# **🔹 Conditional Rendering – শর্ত অনুযায়ী UI দেখানো**  
React-এ **if-else, ternary operator (?)** ব্যবহার করে UI কন্ডিশনালি দেখানো যায়।  

### **📌 Example:**
```jsx
const UserStatus = ({ isLoggedIn }) => {
  return isLoggedIn ? <h2>Welcome Back!</h2> : <h2>Please Login</h2>;
};
```
✅ **Props দিয়ে ভিন্ন UI দেখানো যায়।**  

---

# **🔹 Lists & Keys – Multiple Data Show করা এবং Key Prop ব্যবহার করা**  
React-এ **`.map()` ব্যবহার করে লিস্ট রেন্ডার করা হয়।**  

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
✅ **Key prop দেওয়া বাধ্যতামূলক!**  

---

# **🔹 Fetching Data (API থেকে ডাটা লোড করা)**
React-এ `fetch` এবং `useEffect` ব্যবহার করে **API থেকে ডাটা নেওয়া হয়।**  

### **📌 Example:**
```jsx
import React from 'react';

const fetchUserData = (name) => {
  return fetch(`https://api.example.com/users/${name}`).then(res => res.json());
};

const UserProfile = ({ name }) => {
  const userData = use(fetchUserData(name));

  return (
    <div>
      <h1>{userData.name}</h1>
      <p>Age: {userData.age}</p>
    </div>
  );
};

const App = () => {
  return (
    <>
      <UserProfile name="Shihab" />
      <UserProfile name="Omar" />
      <UserProfile name="Siam" />
    </>
  );
};

export default App;

```
✅ **API থেকে ডাটা লোড করা শেখা অত্যন্ত জরুরি।**  

---

# **🔹 React Router – Multiple Pages Handle করা**  
একাধিক পেজ তৈরি করতে `react-router-dom` ব্যবহার করা হয়।  

### **📌 Install:**
```sh
npm install react-router-dom
```

### **📌 Example:**
```jsx
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";

const Home = () => <h1>Home Page</h1>;
const About = () => <h1>About Page</h1>;

const App = () => {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
};
export default App;
```
✅ **React Router ব্যবহার করে সহজেই নেভিগেশন করা যায়।**  

---

## **📌 Final Summary: React-এর গুরুত্বপূর্ণ কনসেপ্ট**
✔ **JSX** – JavaScript-এর মধ্যে HTML লিখতে দেয়।  
✔ **Components** – Reusable UI টুকরা।  
✔ **Props** – Parent থেকে Child-এ ডাটা পাঠানো।  
✔ **State** – Dynamic data handle করার জন্য।  
✔ **Events** – User interaction handle করা।  
✔ **Lists & Keys** – Multiple data show করা।  
✔ **Conditional Rendering** – কন্ডিশন অনুযায়ী UI দেখানো।  
✔ **Data Fetching** – API থেকে ডাটা লোড করা।  
✔ **React Router** – Multiple pages handle করা।  
