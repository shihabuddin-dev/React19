## **🔹 What is State in React?**  
👉 **State হলো Component-এর Dynamic Data, যা পরিবর্তন হলে UI আপডেট হয়।**  
👉 **State পরিবর্তন করা যায়, Props পরিবর্তন করা যায় না।**  
👉 **React 19-এ Functional Component + Hooks (`useState`) ব্যবহার করে State Handle করা হয়।**  
👉 **State পরিবর্তন হলে React স্বয়ংক্রিয়ভাবে Component-কে রি-রেন্ডার করে।**  

---

## **📌 How State Works?**  

### **✅ Example 1: Creating State with `useState`**
```jsx
import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0); // State তৈরি করা হলো

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Increase</button>
      <button onClick={() => setCount(count - 1)}>Decrease</button>
    </div>
  );
};

export default Counter;
```
✅ **State (`count`) পরিবর্তন হলে UI স্বয়ংক্রিয়ভাবে আপডেট হয়।**  

---

## **📌 Multiple State Variables**
👉 **একাধিক `useState` ব্যবহার করে ভিন্ন ভিন্ন State Handle করা যায়।**  

### **✅ Example 2: Multiple State Variables**
```jsx
import { useState } from "react";

const UserProfile = () => {
  const [name, setName] = useState("Shihab");
  const [age, setAge] = useState(25);

  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <button onClick={() => setAge(age + 1)}>Increase Age</button>
    </div>
  );
};

export default UserProfile;
```
✅ **Multiple State ব্যবহারের মাধ্যমে Dynamic UI তৈরি করা হয়েছে।**  

---

## **📌 State with Objects**
👉 **State-এ Object ব্যবহার করা যায় এবং `setState` দিয়ে পুরো Object আপডেট করতে হয়।**  

### **✅ Example 3: Using Object in State**
```jsx
import { useState } from "react";

const UserProfile = () => {
  const [user, setUser] = useState({ name: "Shihab", age: 25 });

  const increaseAge = () => {
    setUser({ ...user, age: user.age + 1 }); // আগের State কপি করে নতুন ডাটা আপডেট
  };

  return (
    <div>
      <h2>Name: {user.name}</h2>
      <p>Age: {user.age}</p>
      <button onClick={increaseAge}>Increase Age</button>
    </div>
  );
};

export default UserProfile;
```
✅ **State Update করলে আগের Value হারিয়ে না যায়, তাই `...user` ব্যবহার করা হয়েছে।**  

---

## **📌 State with Arrays**
👉 **State-এ Array ব্যবহার করে `.map()`, `.filter()`, এবং `.push()` দিয়ে ডাটা পরিবর্তন করা যায়।**  

### **✅ Example 4: Managing List in State**
```jsx
import { useState } from "react";

const TaskList = () => {
  const [tasks, setTasks] = useState(["Learn React", "Build Projects"]);

  const addTask = () => {
    setTasks([...tasks, "Master React"]); // আগের Array কপি করে নতুন Item Add
  };

  return (
    <div>
      <h2>Tasks:</h2>
      <ul>
        {tasks.map((task, index) => (
          <li key={index}>{task}</li>
        ))}
      </ul>
      <button onClick={addTask}>Add Task</button>
    </div>
  );
};

export default TaskList;
```
✅ **State Update করলে আগের Array হারিয়ে না যায়, তাই `...tasks` ব্যবহার করা হয়েছে।**  

---

## **📌 Using State with Forms**
👉 **Form-এর Input Field-এর Value Handle করতে `useState` ব্যবহার করা হয়।**  

### **✅ Example 5: Handling Form Input**
```jsx
import { useState } from "react";

const LoginForm = () => {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Email: ${email}, Password: ${password}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        placeholder="Enter email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />
      <input
        type="password"
        placeholder="Enter password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
      <button type="submit">Login</button>
    </form>
  );
};

export default LoginForm;
```
✅ **State দিয়ে Form-এর Input Value নিয়ন্ত্রণ করা হয়েছে।**  

---

## **📌 State Update with Previous State**
👉 **State-এর আগের Value ব্যবহার করতে `prevState` প্যারামিটার ব্যবহার করা হয়।**  

### **✅ Example 6: Updating State Based on Previous Value**
```jsx
import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  const increase = () => {
    setCount((prevCount) => prevCount + 1); // আগের Value ব্যবহার করে Update
  };

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increase}>Increase</button>
    </div>
  );
};

export default Counter;
```
✅ **State Update করার সময় `prevState` ব্যবহার করা হয়েছে।**  

---

## **📌 Conditional Rendering with State**
👉 **State-এর ভিত্তিতে UI কন্ডিশন অনুযায়ী পরিবর্তন করা যায়।**  

### **✅ Example 7: Show/Hide Element with State**
```jsx
import { useState } from "react";

const ToggleComponent = () => {
  const [show, setShow] = useState(true);

  return (
    <div>
      <button onClick={() => setShow(!show)}>Toggle</button>
      {show && <h2>Hello, React!</h2>}
    </div>
  );
};

export default ToggleComponent;
```
✅ **Button ক্লিক করলে UI পরিবর্তন হয়।**  

---

### **✅ Example: Fetching Users with `async/await` in React 19**  
👉 **React 19-এ `use` হুক ব্যবহার করে `async/await` সহ API থেকে Data Fetch করার Best Practice:**  

```jsx
import { use } from "react";

const fetchUsers = async () => {
  const response = await fetch("https://jsonplaceholder.typicode.com/users");
  const data = await response.json();
  return data;
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

### **📌 কী করা হয়েছে?**  
✔ `fetchUsers()` ফাংশনে **`async/await`** ব্যবহার করা হয়েছে।  
✔ `use(fetchUsers())` ব্যবহার করে **React 19-এর Standard Data Fetching পদ্ধতি** অনুসরণ করা হয়েছে।  
✔ **এটি Suspense-Ready**, অর্থাৎ `Suspense` দিয়ে Loading UI তৈরি করা যাবে।  

---

## **📌 Conclusion**
✔ **State Dynamic Data Handle করে।**  
✔ **`useState` হুক দিয়ে Functional Component-এ State ব্যবহার করা হয়।**  
✔ **State পরিবর্তন হলে UI স্বয়ংক্রিয়ভাবে আপডেট হয়।**  
✔ **State-এ Object, Array, Function, এবং Event পাঠানো যায়।**  
✔ **React 19-এ `use` হুক দিয়ে Data Fetching করা আরও সহজ হয়েছে।**  