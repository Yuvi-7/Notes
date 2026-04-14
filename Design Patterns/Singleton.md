# 🔒 Singleton Pattern (JavaScript / React Notes)

---

## 📌 Definition

A **Singleton** is a design pattern that ensures:

* Only **one instance** of an object exists
* That instance is **globally accessible**

👉 Used when you need a **single shared resource** across your application

---

## 🧠 Key Idea

> “Create once, reuse everywhere”

---

## 🔑 Basic Implementation (JavaScript)

```js
let instance;

class Singleton {
  constructor() {
    if (instance) {
      return instance; // return existing instance
    }
    instance = this;
  }
}

const obj1 = new Singleton();
const obj2 = new Singleton();

console.log(obj1 === obj2); // true ✅
```

---

## ⚙️ Example with State

```js
let instance;
let count = 0;

class Counter {
  constructor() {
    if (instance) {
      return instance;
    }
    instance = this;
  }

  increment() {
    return ++count;
  }

  decrement() {
    return --count;
  }

  getCount() {
    return count;
  }
}

const counter = Object.freeze(new Counter());

export default counter;
```

---

## ❄️ Why use `Object.freeze`?

```js
Object.freeze(counter);
```

👉 Prevents:

* Modifying properties ❌
* Adding new properties ❌

✔️ Keeps the singleton **safe and immutable**

---

## ⚛️ Singleton in React (Real Use Cases)

### 1. Context API

* One global value shared across components

---

### 2. Redux Store

* Single source of truth for application state

---

### 3. API Instance

```js
const api = axios.create({ baseURL: "/api" });
export default api;
```

👉 Same instance used everywhere

---

### 4. Service Modules

```js
export const authService = {
  login() {},
  logout() {}
};
```

👉 Imported once → shared globally

---

## ✅ When to Use

* Global configuration
* API clients
* Logging services
* Shared caches

---

## ❌ When NOT to Use

* Complex state logic
* Frequently changing data
* When multiple instances are needed

---

## ⚠️ Trade-offs

* ❌ Hard to test (shared state)
* ❌ Hidden dependencies
* ❌ Tight coupling
* ❌ Possible bugs in async code

---

## 🆚 Singleton vs Factory

| Feature     | Singleton 🔒  | Factory 🏭      |
| ----------- | ------------- | --------------- |
| Instances   | One           | Many            |
| State       | Shared        | Independent     |
| Purpose     | Global access | Object creation |
| Flexibility | Low           | High            |

---

## 🧠 Best Practices

* Keep Singleton **simple**
* Avoid storing too much logic/state
* Use only when **global sharing is required**
* Combine carefully with React state tools

---

## 🧾 Summary

* Singleton ensures **only one instance exists**
* Used for **shared/global resources**
* Easy to implement but must be used carefully

---

## 🧠 Final Insight

> Singleton = “One instance for the entire app”
> Use it when consistency and shared access matter
