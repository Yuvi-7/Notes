# 👀 Observer Pattern (JavaScript / React Notes)

---

## 📌 Definition

The **Observer Pattern** is a design pattern where:

* One object (**Subject / Observable**) maintains a list of dependents
* It **notifies all observers automatically** when its state changes

👉 Used for **event-driven communication**

---

## 🧠 Key Idea

> “One change → notify many listeners”

---

## 🧩 Core Components

### 1. Subject (Observable)

* Holds list of observers
* Sends updates

### 2. Observers (Subscribers)

* Functions or objects
* React to updates

---

## 🔑 Basic Implementation

```js id="gq4j0v"
class Observable {
  constructor() {
    this.observers = [];
  }

  subscribe(fn) {
    this.observers.push(fn);
  }

  unsubscribe(fn) {
    this.observers = this.observers.filter(
      (observer) => observer !== fn
    );
  }

  notify(data) {
    this.observers.forEach((observer) => observer(data));
  }
}
```

---

## 🔌 Example Usage

```js id="bbzqax"
const observable = new Observable();

function user1(data) {
  console.log("User1:", data);
}

function user2(data) {
  console.log("User2:", data);
}

observable.subscribe(user1);
observable.subscribe(user2);

observable.notify("New update!");
```

---

## 🔄 Flow

1. Observers subscribe
2. Event occurs
3. Subject calls `notify()`
4. All observers receive update

---

## 🎯 Real-Life Analogy

* YouTube channel → Subject
* Subscribers → Observers
* New video → Notification

---

## ⚛️ Observer Pattern in React

### 1. State Updates

```js id="z3xqpi"
setState()
```

👉 Components re-render (observers react)

---

### 2. Event Listeners

```js id="i0a2r1"
button.addEventListener("click", handler);
```

---

### 3. Libraries like Redux

* Store → Subject
* Components → Observers

---

## ✅ Advantages

* Loose coupling between components
* Scalable (add/remove observers anytime)
* One-to-many communication
* Easy to extend

---

## ❌ Disadvantages

* Hard to debug (many listeners)
* Memory leaks if not unsubscribed
* Performance issues with too many observers

---

## ⚠️ Best Practices

* Always **unsubscribe** when not needed
* Avoid too many observers
* Use meaningful event data
* Prefer `Set` over array (avoid duplicates)

---

## 🚀 Improved Version (Using Set)

```js id="pr3pfa"
class Observable {
  constructor() {
    this.observers = new Set();
  }

  subscribe(fn) {
    this.observers.add(fn);
    return () => this.unsubscribe(fn); // cleanup
  }

  unsubscribe(fn) {
    this.observers.delete(fn);
  }

  notify(data) {
    this.observers.forEach((fn) => fn(data));
  }
}
```

---

## 🆚 Observer vs Other Patterns

| Pattern      | Purpose                   |
| ------------ | ------------------------- |
| Observer 👀  | Notify multiple listeners |
| Singleton 🔒 | One shared instance       |
| Factory 🏭   | Create objects            |

---

## 🧠 Use Cases

* Event systems
* Notifications (toast, alerts)
* State management
* Pub/Sub systems
* Real-time updates

---

## 🧾 Summary

* Observer = **event-based communication pattern**
* One subject → many observers
* Used heavily in React and frontend apps

---

## 🧠 Final Insight

> Observer Pattern = “Subscribe → Notify → React”

---
