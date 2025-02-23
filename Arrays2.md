# Day 7: JavaScript30 — Array Cardio Day (Part 2)

## Overview
On Day 7 of the JavaScript30 series, we continued exploring array methods, focusing on **`.some()`**, **`.every()`**, **`.find()`**, and **`.findIndex()`**. These methods are powerful for evaluating and manipulating arrays, making data handling in JavaScript more efficient.

---

## Code Explanation

```javascript
const people = [
  { name: 'Wes', year: 1988 },
  { name: 'Kait', year: 1986 },
  { name: 'Irv', year: 1970 },
  { name: 'Lux', year: 2015 }
];

const comments = [
  { text: 'Love this!', id: 523423 },
  { text: 'Super good', id: 823423 },
  { text: 'You are the best', id: 2039842 },
  { text: 'Ramen is my fav food ever', id: 123523 },
  { text: 'Nice Nice Nice!', id: 542328 }
];
```
- **`people` array**: Contains objects with names and birth years.
- **`comments` array**: Contains objects with text comments and unique IDs.

---

### **1. `.some()` Method**

```javascript
const isAdult = people.some(person => (new Date().getFullYear()) - (person.year) >= 19);
console.log({isAdult});
```
- **`.some()`**: Returns **`true`** if at least one element passes the test function, otherwise **`false`**.
- **Arrow Function**: Computes age by comparing the current year to the birth year.
- **Example Output**: `{isAdult: true}` if at least one person is 19 or older.

---

### **2. `.every()` Method**

```javascript
const allAdults = people.every(person => (new Date().getFullYear) - person.year >= 19);
console.log(allAdults);
```
- **`.every()`**: Returns **`true`** only if **all** elements pass the test function.
- **Common Mistake**: There is a typo in the code: **`(new Date().getFullYear)`** is missing **`()`**, it should be **`(new Date().getFullYear())`**.
- **Example Output**: **`false`** if at least one person is under 19.

---

### **3. `.find()` Method**

```javascript
const findComment = comments.find(comment => (comment.id === 823423));
console.log(findComment.text);
```
- **`.find()`**: Returns the **first element** that matches the condition, or **`undefined`** if not found.
- **Example Output**: **`'Super good'`** since it is the text of the comment with ID **`823423`**.

---

### **4. `.findIndex()` Method & Deleting an Element**

```javascript
const index = comments.findIndex(comment => comment.id === 823423);
console.log(index);
console.table(comments);
comments.splice(index, 1);
console.table(comments);
```
- **`.findIndex()`**: Returns the **index** of the first matching element or **`-1`** if not found.
- **`.splice()`**: Removes an element at the specified index.
- **Example Output**:
  - Displays the index **`1`** for the matched comment.
  - Before deletion, all comments are shown in a table.
  - After **`.splice()`**, the comment with ID **`823423`** is removed from the array.

---

## Key Concepts Learned

1. **Array Methods for Validation**:
   - **`.some()`** for partial validation.
   - **`.every()`** for full validation.

2. **Finding and Deleting Array Elements**:
   - **`.find()`** for retrieving an element.
   - **`.findIndex()`** combined with **`.splice()`** for deletion.

3. **Common Pitfalls**:
   - Forgetting to invoke methods with **`()** (e.g., **`getFullYear`**).

4. **Debugging Techniques**:
   - Using **`console.log`** and **`console.table`** to visualize array data.

---

## Potential Use Cases
- Validating form inputs (e.g., checking if any input field is empty with **`.some()`**).
- Checking eligibility or validation rules (e.g., age verification with **`.every()`**).
- Retrieving specific items from data sets (e.g., finding a user by ID with **`.find()`**).
- Safely removing items from arrays (e.g., deleting comments, products, or data entries).

