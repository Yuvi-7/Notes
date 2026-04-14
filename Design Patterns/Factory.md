# 🏭 Factory Pattern (JavaScript / React Notes)

## 📌 Definition

The **Factory Pattern** is a design pattern where a function is used to **create and return objects** instead of using classes or constructors directly.

👉 It abstracts object creation logic and provides a **clean, reusable way** to generate objects.

---

## 🧠 Key Idea

> “Instead of manually creating objects, use a function (factory) to produce them.”

---

## 🔑 Basic Example

```js
const createUser = ({ firstName, lastName }) => ({
  firstName,
  lastName,
  fullName() {
    return `${firstName} ${lastName}`;
  }
});

const user1 = createUser({ firstName: "Yuvraj", lastName: "Gupta" });
const user2 = createUser({ firstName: "Aman", lastName: "Sharma" });
```

---

## ⚙️ Characteristics

* Creates **new instance every time**
* Does **not use `new` keyword**
* Often avoids `this` (uses closures instead)
* Encapsulates object creation logic

---

## 🆚 Factory vs Singleton

| Feature   | Factory Pattern 🏭 | Singleton 🔒          |
| --------- | ------------------ | --------------------- |
| Instances | Multiple           | Only one              |
| Purpose   | Create objects     | Share global instance |
| State     | Independent        | Shared                |
| Usage     | Flexible           | Global state          |

---

## 🧩 When to Use Factory Pattern

* When object creation is **repeated**
* When you need **multiple similar objects**
* When you want to **hide complexity**
* When avoiding `this` and `new`

---

## 🚀 Factory Pattern in React

### 1. Custom Hooks (Most common)

```js
function useUser() {
  const [user, setUser] = useState(null);

  return {
    user,
    login: () => {},
    logout: () => {}
  };
}
```

👉 Each call creates a new “instance” of logic

---

### 2. API / Service Factories

```js
const createApi = (baseURL) => ({
  get: (url) => fetch(baseURL + url),
  post: (url, data) => fetch(baseURL + url, { method: "POST", body: data })
});

const api = createApi("/api");
```

---

### 3. Component Factory

```js
const createButton = (type) => {
  return function Button({ children }) {
    return <button className={type}>{children}</button>;
  };
};
```

---

## ⚠️ Trade-offs

* ❌ Methods are recreated per object (memory cost)
* ❌ No built-in inheritance like classes
* ❌ Can become messy if overused

---

## 🧠 Best Practices

* Prefer **closures over `this`**
* Keep factories **small and focused**
* Use for **logic reuse**, not everything
* Combine with hooks in React

---

## 🔥 Advanced (Private Data with Closure)

```js
const createCounter = () => {
  let count = 0;

  return {
    increment: () => ++count,
    decrement: () => --count,
    getCount: () => count
  };
};
```

👉 `count` is private (cannot be accessed directly)

---

## 🧾 Summary

* Factory Pattern = function that returns objects
* Creates **multiple independent instances**
* Widely used in **React hooks and utilities**
* Opposite of Singleton (which shares one instance)

