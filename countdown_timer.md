# Countdown Clock - Detailed Notes

## 🎯 **Project Goal:**
To create a countdown timer that displays the remaining time both on the webpage and in the browser's title.

---

## 🛠️ **Code:**
```javascript
let countdown;
const timerDisplay = document.querySelector('.display__time-left');

function timer(seconds) {
    const now = Date.now();
    const then = now + seconds * 1000;
    displayTimeLeft(seconds);
    
    countdown = setInterval(() => {
        let secondsLeft = Math.round((then - Date.now()) / 1000);
    
        if (secondsLeft < 0) {
            clearInterval(countdown);
            return;
        }
        displayTimeLeft(secondsLeft);
    }, 1000);
}

function displayTimeLeft(seconds) {
    const minutes = Math.floor(seconds / 60);
    const remainderSeconds = seconds % 60;
    
    const display = `${minutes}:${remainderSeconds < 10 ? '0' : ''}${remainderSeconds}`;
    timerDisplay.textContent = display;
    document.title = display;
}
```

---

## 📝 **Step-by-Step Explanation:**

### 1. **Variable Initialization:**
```javascript
let countdown;
```
- **Purpose:** To store the interval ID returned by `setInterval()`, allowing us to clear the interval later with `clearInterval()`.
- **Learned:** The `let` keyword is used to declare a variable with block scope.

### 2. **DOM Selection:**
```javascript
const timerDisplay = document.querySelector('.display__time-left');
```
- **Purpose:** Selects the HTML element with the class `display__time-left` to display the remaining time.
- **Learned:**
  - **`.querySelector()`** method is used to select **DOM elements** using **CSS selectors**.
  - **`.textContent`** is a property that sets or returns the text content of a node.

### 3. **`timer()` Function:**
#### **3.1 Get Current Time:**
```javascript
const now = Date.now();
```
- **Purpose:** Returns the **current timestamp** in milliseconds since **January 1, 1970**.

#### **3.2 Calculate End Time:**
```javascript
const then = now + seconds * 1000;
```
- **Purpose:** Calculates the **future time** when the timer should **end**.

#### **3.3 Initial Display Update:**
```javascript
displayTimeLeft(seconds);
```
- **Purpose:** Immediately **displays** the **initial value** of the timer before the interval starts.

### 4. **Start Countdown Using `setInterval()`:**
```javascript
countdown = setInterval(() => {
```
- **Purpose:** Executes the provided **callback function** every **1000 milliseconds (1 second)**.

#### **4.1 Calculate Remaining Time:**
```javascript
let secondsLeft = Math.round((then - Date.now()) / 1000);
```
- **Purpose:** Calculates **remaining seconds** by subtracting the **current time** from the **end time**.
- **Learned:**
  - **`.round()`** method is used to **round** numbers to the **nearest integer**.

#### **4.2 Stop Timer When Done:**
```javascript
if (secondsLeft < 0) {
    clearInterval(countdown);
    return;
}
```
- **Purpose:**
  - **Stops** the timer when the countdown reaches **zero**.
  - **`clearInterval()`** method **cancels** the **repeated execution** of the function.
  - **`return`** statement **exits** the function early, preventing further execution.

#### **4.3 Update Display with Remaining Time:**
```javascript
displayTimeLeft(secondsLeft);
```
- **Purpose:** Updates the **display** with the **remaining time**.

---

## **5. `displayTimeLeft()` Function:**
#### **5.1 Calculate Minutes and Seconds:**
```javascript
const minutes = Math.floor(seconds / 60);
const remainderSeconds = seconds % 60;
```
- **Purpose:**
  - **`Math.floor()`**: Returns the **largest integer** less than or equal to the **quotient**, giving us **minutes**.
  - **Modulus (`%`)**: Calculates **remaining seconds** after **minute conversion**.

#### **5.2 Format Time with Leading Zero:**
```javascript
const display = `${minutes}:${remainderSeconds < 10 ? '0' : ''}${remainderSeconds}`;
```
- **Purpose:**
  - **Template literals (` `` `)**: Enable **embedded expressions** in strings.
  - **Ternary Operator (`?:`)**: Adds a **leading zero** when seconds are **less than 10**.

#### **5.3 Update DOM and Page Title:**
```javascript
timerDisplay.textContent = display;
document.title = display;
```
- **Purpose:**
  - Updates the **webpage** and the **browser tab** with the **remaining time**.
  - **`document.title`**: Sets the **text** displayed in the **browser tab**.

---

## 📚 **Key JavaScript Concepts Learned:**
- **Intervals:** `setInterval()` and `clearInterval()`.
- **Date & Time:** `Date.now()`.
- **Math Methods:** `Math.floor()` and `Math.round()`.
- **Template Literals:** For **string interpolation**.
- **Ternary Operators:** For **conditional formatting**.
- **DOM Manipulation:** `.querySelector()` and `.textContent`.

---

## ✅ **Takeaway:**
- The project helped in **understanding timers**, **displaying dynamic content**, and **managing intervals** efficiently.
- The use of **JavaScript functions** and **intervals** is crucial for **dynamic web applications**.

