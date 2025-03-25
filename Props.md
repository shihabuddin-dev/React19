## **🔹 What is Props in React?**
👉 **Props (Properties)** হলো **Parent Component থেকে Child Component-এ Data পাঠানোর উপায়**।  
👉 **Props Immutable** (পরিবর্তন করা যায় না)।  
👉 **React 19-এর Standard Functional Component-এ Props ব্যবহার করা হয়।**  

---

## **📌 How Props Work?**  

### **✅ Example 1: Sending Props from Parent to Child**  
```jsx
const UserProfile = ({ name, age }) => {
  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
    </div>
  );
};

const App = () => {
  return (
    <div>
      <UserProfile name="Shihab" age={25} />
      <UserProfile name="Omar" age={27} />
      <UserProfile name="Siam" age={23} />
    </div>
  );
};

export default App;
```
✅ **Props ব্যবহার করে Parent থেকে Child Component-এ Data পাঠানো হয়েছে।**  

---

## **📌 Props with Default Values**
👉 **Props না দিলেও Default Value সেট করা যায়।**  

### **✅ Example 2: Default Props Value**
```jsx
const WelcomeMessage = ({ name = "Guest" }) => {
  return <h2>Welcome, {name}!</h2>;
};

const App = () => {
  return (
    <div>
      <WelcomeMessage name="Shihab" />
      <WelcomeMessage />
    </div>
  );
};

export default App;
```
✅ **`name` না পাঠালে Default Value `"Guest"` দেখাবে।**  

---

## **📌 Props as an Object**
👉 **একাধিক Props Object আকারে পাঠানো যায়।**  

### **✅ Example 3: Sending Props as an Object**
```jsx
const user = { name: "Shihab", age: 25, location: "Dhaka" };

const UserProfile = ({ userInfo }) => {
  return (
    <div>
      <h2>Name: {userInfo.name}</h2>
      <p>Age: {userInfo.age}</p>
      <p>Location: {userInfo.location}</p>
    </div>
  );
};

const App = () => {
  return (
    <div>
      <UserProfile userInfo={user} />
    </div>
  );
};

export default App;
```
✅ **একটি Object Props হিসেবে পাঠানো হয়েছে।**  

---

## **📌 Props with Arrays**
👉 **Props-এ Array পাঠিয়ে `.map()` ব্যবহার করে লিস্ট রেন্ডার করা যায়।**  

### **✅ Example 4: Sending Array as Props**
```jsx
const UserList = ({ users }) => {
  return (
    <ul>
      {users.map((user, index) => (
        <li key={index}>{user}</li>
      ))}
    </ul>
  );
};

const App = () => {
  const userNames = ["Shihab", "Omar", "Siam"];

  return (
    <div>
      <UserList users={userNames} />
    </div>
  );
};

export default App;
```
✅ **Array Props হিসেবে পাঠানো হয়েছে এবং `.map()` ব্যবহার করে রেন্ডার করা হয়েছে।**  

---

## **📌 Props with Event Handling**
👉 **Props ব্যবহার করে Parent Component থেকে Event Function পাঠানো যায়।**  

### **✅ Example 5: Passing Event Handler as Props**
```jsx
const Button = ({ handleClick }) => {
  return <button onClick={handleClick}>Click Me</button>;
};

const App = () => {
  const showMessage = () => {
    alert("Button Clicked!");
  };

  return (
    <div>
      <Button handleClick={showMessage} />
    </div>
  );
};

export default App;
```
✅ **Parent থেকে Event Handler পাঠিয়ে Child Component-এ ব্যবহার করা হয়েছে।**  

---

## **📌 Props Destructuring**
👉 **Props-কে `{}` ব্যবহার করে সহজে এক্সেস করা যায়।**  

### **✅ Example 6: Props Destructuring**
```jsx
const UserInfo = ({ name, age }) => {
  return (
    <h2>
      {name} is {age} years old.
    </h2>
  );
};

const App = () => {
  return <UserInfo name="Shihab" age={25} />;
};

export default App;
```
✅ **Props-কে `({ name, age })` দিয়ে Destructure করা হয়েছে।**  

---

## **📌 Children Props (Passing JSX as Props)**
👉 **Component-এর ভিতরে Content পাঠাতে `props.children` ব্যবহার করা হয়।**  

### **✅ Example 7: Using `props.children`**
```jsx
const Card = ({ children }) => {
  return <div className="card">{children}</div>;
};

const App = () => {
  return (
    <Card>
      <h2>This is inside a Card!</h2>
      <p>React Props are powerful.</p>
    </Card>
  );
};

export default App;
```
✅ **`props.children` ব্যবহার করে Component-এর ভিতরে Content পাঠানো হয়েছে।**  

---

## **📌 Conclusion**
✔ **Props Parent থেকে Child-এ Data পাঠানোর জন্য ব্যবহার করা হয়।**  
✔ **Props Immutable (পরিবর্তন করা যায় না)।**  
✔ **Props-এ Object, Array, Function এবং JSX পাঠানো যায়।**  
✔ **Props Destructuring ব্যবহার করে কোড সহজ করা যায়।**  
✔ **`props.children` দিয়ে Component-এর ভিতরে Content পাঠানো যায়।**  

