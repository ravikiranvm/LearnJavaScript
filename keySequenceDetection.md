# JavaScript30 - Day 12: Key Sequence Detection

## 🚀 **Concepts Covered:**
- **Arrays in JavaScript**
- **Event Listeners (`keyup` event)**
- **Array Methods (`push`, `splice`, `join`)**
- **String Methods (`includes`)**
- **Easter Eggs with `cornify_add()`**

---

## 🧠 **What You Learned:**

### 1. **Key Sequence Detection:**
- The goal is to detect a specific sequence of keys pressed by the user (`'ravi'` in this case).
- When the secret sequence is entered, an action is triggered (`cornify_add()` is called).

### 2. **`pressed` Array:**
- An empty array `pressed` is initialized to store the sequence of keys pressed by the user.

### 3. **Listening for Key Presses:**
- `document.addEventListener('keyup', (e) => { ... })` is used to detect when a key is released.
- The callback function `(e) => {...}` receives an event object `e` that contains information about the key pressed (`e.key`).

### 4. **Adding Keys to the Array:**
- `pressed.push(e.key)` adds the latest key to the `pressed` array.

### 5. **Maintaining Array Length:**
- `pressed.splice(-secret.length -1, pressed.length - secret.length)` ensures the array only keeps the last `n` keys, where `n` is the length of the `secret` string.
- This prevents the array from growing indefinitely and only keeps the relevant keys for pattern matching.

### 6. **Detecting the Secret Sequence:**
- `pressed.join('').includes(secret)` converts the `pressed` array into a string and checks if it contains the `secret` sequence.
- If the secret is found, `cornify_add()` is called.
- `cornify_add()` is a fun library that adds random unicorns and rainbows to the page as an "Easter egg."

### 7. **Logging the Array:**
- `console.log(pressed)` helps visualize the array's state after each key press, useful for debugging.

---

## 💡 **Takeaways:**
- Arrays and string manipulation in JavaScript are powerful for detecting patterns and managing dynamic data.
- `splice()` is not just for removing elements but also for controlling array length dynamically.
- `includes()` is great for pattern matching within strings.
- `keyup` vs `keydown`: `keyup` triggers when the key is released, giving a better user experience for typing interactions.

