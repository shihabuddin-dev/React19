## **🔹 What is Conditional Rendering in React?**  
✅ **Conditional Rendering** মানে হলো **শর্ত সাপেক্ষে UI-তে কিছু দেখানো বা না দেখানো**।  
✅ **React-এ JavaScript-এর শর্তযুক্ত (`if-else`, `&&`, `ternary (? :)`) লজিক ব্যবহার করা হয়।**  
✅ **এটি ডাটা অনুযায়ী UI পরিবর্তন করতে সাহায্য করে।**  

---

## **📌 Ways to Implement Conditional Rendering**  

### **✅ Method 1: Using `if-else` Statement**  
👉 **একটি শর্ত চেক করে JSX Return করা হয়।**  

```jsx
const UserStatus = ({ isLoggedIn }) => {
  if (isLoggedIn) {
    return <h2>Welcome, User!</h2>;
  } else {
    return <h2>Please Login</h2>;
  }
};

export default UserStatus;
```
✅ **`isLoggedIn` true হলে "Welcome, User!" দেখাবে, নাহলে "Please Login" দেখাবে।**  

---

### **✅ Method 2: Using Ternary Operator (`? :`)**  
👉 **একটি ছোট `if-else` এর জন্য Ternary Operator ব্যবহার করা হয়।**  

```jsx
const UserStatus = ({ isLoggedIn }) => {
  return (
    <h2>{isLoggedIn ? "Welcome, User!" : "Please Login"}</h2>
  );
};

export default UserStatus;
```
✅ **একই `if-else` এর Short Version!**  

---

### **✅ Method 3: Using Logical AND (`&&`) Operator**  
👉 **যদি শর্ত true হয়, তাহলে JSX Render হবে।**  

```jsx
const Notification = ({ messages }) => {
  return (
    <div>
      <h2>Notifications</h2>
      {messages.length > 0 && <p>You have {messages.length} new messages!</p>}
    </div>
  );
};

export default Notification;
```
✅ **যদি `messages.length > 0` হয়, তাহলে "You have X new messages!" দেখাবে।**  
✅ **না হলে কিছুই দেখাবে না।**  

---

### **✅ Method 4: Using `||` (OR) Operator**  
👉 **কোনো Value না থাকলে Default Message দেখানো যায়।**  

```jsx
const UserName = ({ name }) => {
  return <h2>Hello, {name || "Guest"}!</h2>;
};

export default UserName;
```
✅ **যদি `name` না থাকে, তাহলে "Guest" দেখাবে।**  

---

### **✅ Method 5: Using `&&` Inside JSX**  
👉 **React-এর মধ্যে `&&` ব্যবহার করা যায়।**  

```jsx
const ShowMessage = ({ isAdmin }) => {
  return (
    <div>
      <h2>Welcome to the Dashboard</h2>
      {isAdmin && <button>Admin Panel</button>}
    </div>
  );
};

export default ShowMessage;
```
✅ **`isAdmin` true হলে "Admin Panel" বাটন দেখাবে, নাহলে দেখাবে না।**  

---

## **📌 Handling Conditional Rendering with Components**  
👉 **শর্ত সাপেক্ষে ভিন্ন ভিন্ন Component দেখানো যেতে পারে।**  

### **✅ Example 1: Showing Different Components Based on Condition**
```jsx
const UserGreeting = () => <h2>Welcome Back!</h2>;
const GuestGreeting = () => <h2>Please Sign Up</h2>;

const Greeting = ({ isLoggedIn }) => {
  return isLoggedIn ? <UserGreeting /> : <GuestGreeting />;
};

export default Greeting;
```
✅ **`isLoggedIn` true হলে `UserGreeting`, নাহলে `GuestGreeting` দেখাবে।**  

---

### **✅ Example 2: Toggle UI with Conditional Rendering**
👉 **একটি Toggle Button ব্যবহার করে UI পরিবর্তন করা যেতে পারে।**  

```jsx
import { useState } from "react";

const ToggleComponent = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>
        {show ? "Hide" : "Show"} Message
      </button>
      {show && <h2>Hello, React!</h2>}
    </div>
  );
};

export default ToggleComponent;
```
✅ **"Show Message" বাটনে ক্লিক করলে মেসেজ দেখাবে, আবার "Hide Message" করলে মেসেজ লুকাবে।**  

---

## **📌 Conditional Rendering in Lists**  
👉 **শর্ত সাপেক্ষে শুধুমাত্র কিছু Item দেখানো যেতে পারে।**  

### **✅ Example 3: Filter Active Users**
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
✅ **শুধু Active Users দেখাবে, Inactive Users দেখাবে না।**  

---

## **📌 Conclusion**  
✔ **`if-else`, `ternary`, `&&`, এবং `||` দিয়ে Conditional Rendering করা যায়।**  
✔ **Component ভিত্তিক Conditional Rendering করা যায়।**  
✔ **API লোডের সময় `Loading...` দেখানো যায়।**  
✔ **Toggle Button ব্যবহার করে UI পরিবর্তন করা যায়।**  
✔ **List Filter করে কিছু নির্দিষ্ট Data দেখানো যায়।**  
