## **🔹 What are Lists & Keys in React?**  
✅ **Lists:**  
- React-এ **Lists** হলো **একই ধরনের একাধিক ডাটা একসাথে দেখানোর একটি উপায়**।  
- **`map()`** ব্যবহার করে List-এর Data **loop-এর মাধ্যমে render** করা হয়।  

✅ **Keys:**  
- **Key হলো একটি Unique Identifier**, যা React কে বলে দেয় **কোনো Item পরিবর্তিত, যোগ, বা মুছে ফেলা হয়েছে কি না**।  
- **Keys ব্যবহার করলে React Virtual DOM efficiently Update করতে পারে।**  
- **Key হিসেবে `id` ব্যবহার করা ভালো, কিন্তু `index` ব্যবহার করাও সম্ভব।**  

---

## **📌 How to Render Lists in React?**  

### **✅ Example 1: Rendering a Simple List**
```jsx
const NamesList = () => {
  const names = ["Shihab", "Omar", "Siam"];

  return (
    <ul>
      {names.map((name, index) => (
        <li key={index}>{name}</li>
      ))}
    </ul>
  );
};

export default NamesList;
```
✅ **এখানে `map()` ব্যবহার করে `names` array থেকে List Render করা হয়েছে।**  
✅ **Key হিসেবে `index` ব্যবহার করা হয়েছে (যদি `id` না থাকে)।**  

---

## **📌 Using Unique Keys for Lists**  
👉 **কখনও সম্ভব হলে `id` কে Key হিসেবে ব্যবহার করা উচিত, কারণ এটি Unique থাকে।**  

### **✅ Example 2: Rendering a List with Unique Keys**
```jsx
const UsersList = () => {
  const users = [
    { id: 1, name: "Shihab" },
    { id: 2, name: "Omar" },
    { id: 3, name: "Siam" },
  ];

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};

export default UsersList;
```
✅ **এখানে `id` কে Key হিসেবে ব্যবহার করা হয়েছে, যা Best Practice।**  

---

## **📌 Rendering List of Components**  
👉 **একটি `User` Component তৈরি করে সেটিকে List-এর মধ্যে ব্যবহার করা যায়।**  

### **✅ Example 3: Rendering List of Components**
```jsx
const User = ({ name }) => {
  return <li>{name}</li>;
};

const UsersList = () => {
  const users = [
    { id: 1, name: "Shihab" },
    { id: 2, name: "Omar" },
    { id: 3, name: "Siam" },
  ];

  return (
    <ul>
      {users.map((user) => (
        <User key={user.id} name={user.name} />
      ))}
    </ul>
  );
};

export default UsersList;
```
✅ **এখানে `User` নামে একটি Component তৈরি করে সেটিকে List-এর মধ্যে ব্যবহার করা হয়েছে।**  

---

## **📌 Fetching & Displaying Data from API with Lists & Keys**  
👉 **API থেকে Data নিয়ে List আকারে দেখানো যায়।**  

### **✅ Example 4: Fetching Data from API & Displaying as List**
```jsx
import { useState, useEffect } from "react";

const UsersList = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const fetchUsers = async () => {
      const response = await fetch("https://jsonplaceholder.typicode.com/users");
      const data = await response.json();
      setUsers(data);
    };
    fetchUsers();
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};

export default UsersList;
```
✅ **এখানে `useEffect` ব্যবহার করে API থেকে Data Fetch করে List আকারে দেখানো হয়েছে।**  

---

## **📌 Using Index as a Key (Not Recommended)**
👉 **Index ব্যবহার করা যেতে পারে, তবে শুধুমাত্র তখনই যখন Data পরিবর্তিত হবে না।**  
👉 **যদি Data পরিবর্তন হয়, তাহলে Key হিসেবে `id` ব্যবহার করা Best Practice।**  

### **❌ Example 5: Using Index as Key (Not Recommended)**
```jsx
const NamesList = () => {
  const names = ["Shihab", "Omar", "Siam"];

  return (
    <ul>
      {names.map((name, index) => (
        <li key={index}>{name}</li>
      ))}
    </ul>
  );
};

export default NamesList;
```
❌ **এটি তখনই ব্যবহার করা উচিত যখন List-এর Items কখনও পরিবর্তিত হবে না।**  

---

## **📌 Conditional Rendering with Lists**
👉 **কিছু শর্ত সাপেক্ষে কোনো List-এর কিছু অংশ দেখানো বা না দেখানো যেতে পারে।**  

### **✅ Example 6: Conditional Rendering in List**
```jsx
const UsersList = () => {
  const users = [
    { id: 1, name: "Shihab", active: true },
    { id: 2, name: "Omar", active: false },
    { id: 3, name: "Siam", active: true },
  ];

  return (
    <ul>
      {users
        .filter((user) => user.active) // শুধু Active Users দেখাবে
        .map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
    </ul>
  );
};

export default UsersList;
```
✅ **এখানে শুধুমাত্র Active Users দেখানো হয়েছে।**  

---

## **📌 Conclusion**  
✔ **`map()` ব্যবহার করে List Rendering করা হয়।**  
✔ **Key হিসেবে `id` ব্যবহার করা Best Practice।**  
✔ **Class Component ও Functional Component দুটোতেই Lists & Keys কাজ করে।**  
✔ **API থেকে Data এনে List-এ দেখানো যায়।**  
✔ **Conditional Rendering-এর মাধ্যমে কিছু অংশ দেখানো বা লুকানো যায়।**  