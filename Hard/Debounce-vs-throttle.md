# ⚡ Debounce vs Throttle in JavaScript

## 🔍 What Are Debouncing and Throttling?

Both **debouncing** and **throttling** are techniques to **control the rate at which a function gets executed**, especially for performance optimization when dealing with events like:

- Scrolling
- Resizing
- Button clicks
- Input fields (like search boxes)

---

## 🧠 Why Do We Need Them?

In JavaScript, certain events like `scroll`, `resize`, or `keyup` can fire **many times per second**. If we attach heavy operations (like API calls or DOM updates) to them, it can lead to **performance issues**.

---

## 🧯 Debouncing

### 📖 Definition:

Debouncing ensures that a function is **called only after a certain delay**, and **only if no new event has occurred** during that delay.

### 📦 Use Case:

- Search input suggestions (API call should only be made after user stops typing)
- Resize window handler (fire only after resizing ends)

### ✅ Example:

```js
function debounce(func, delay) {
    let timer;
    return function (...args) {
        clearTimeout(timer);
        timer = setTimeout(() => {
            func.apply(this, args);
        }, delay);
    };
}
```

### 💡 Usage:

```js
function fetchSuggestions(e) {
    console.log("API Call for:", e.target.value);
}

const debouncedFetch = debounce(fetchSuggestions, 500);

document.getElementById("search").addEventListener("input", debouncedFetch);
```

⏱️ This waits **500ms** after the last keystroke before making the API call.

---

## 🚦 Throttling

### 📖 Definition:

Throttling ensures a function is **called at most once in a specified interval**, no matter how many times the event is triggered.

### 📦 Use Case:

- Scroll event listener (e.g., infinite scrolling, scroll position tracking)
- Button click spamming prevention (e.g., payment buttons)

### ✅ Example:

```js
function throttle(func, delay) {
    let lastCall = 0;
    return function (...args) {
        const now = new Date().getTime();
        if (now - lastCall >= delay) {
            lastCall = now;
            func.apply(this, args);
        }
    };
}
```

### 💡 Usage:

```js
function logScroll() {
    console.log("User scrolled at", new Date().toLocaleTimeString());
}

const throttledScroll = throttle(logScroll, 1000);

window.addEventListener("scroll", throttledScroll);
```

🕐 This will log **once every second**, no matter how much the user scrolls.

---

## 🆚 Debounce vs Throttle

| Feature        | Debounce                                 | Throttle                                 |
|----------------|------------------------------------------|------------------------------------------|
| Definition     | Executes after delay with no event       | Executes at regular intervals            |
| Frequency      | Only once per final event                | At most once per interval                |
| Use Cases      | Search box, resize event                 | Scroll event, resizing window            |
| Trigger Style  | Waits for silence                        | Fires periodically                       |

---

## ✅ Summary

- Use **Debouncing** when you want to wait until the user has stopped doing something.
- Use **Throttling** when you want to **limit how often** a function is called while the user is doing something.

---

## 🧪 Bonus Practice

Try implementing:

- A **debounced** version of an input field that fetches data after 800ms of no typing.
- A **throttled** version of a scroll position logger that logs every 2 seconds.

---

## 🔚 Conclusion

Both debouncing and throttling are essential tools for writing **efficient and performance-friendly** JavaScript applications. Use them wisely to make your UI smooth and responsive.

Happy Coding 🚀