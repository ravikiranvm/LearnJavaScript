# JS30 Day 4: Array Cardio Day 1 - Detailed Notes

This document covers the key concepts and JavaScript methods learned during Day 4 of the JavaScript30 series. It focuses on array manipulation using `filter()`, `map()`, `sort()`, and `reduce()` methods.

---

## 1. Array.prototype.filter()

### Code Example
```js
let inventors1500 = inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600));
```

### What You Learned
- **filter() Method:** Creates a new array with elements that pass the test implemented by a function.
- **Arrow Function:** `inventor => (inventor.year >= 1500 && inventor.year < 1600)` is a shorthand function returning true or false.
- **Conditional Filtering:** Only returns inventors born in the 1500s.

---

## 2. Array.prototype.map()

### Code Example
```js
let FullName = inventors.map(inventor => `${inventor.first} ${inventor.last}`);
```

### What You Learned
- **map() Method:** Transforms each element in an array, returning a new array of the same length.
- **Template Literals:** `${inventor.first} ${inventor.last}` allows dynamic string creation.

---

## 3. Array.prototype.sort()

### Code Example
```js
let ordered = inventors.sort((a, b) => a.year > b.year ? 1 : -1);
```

### What You Learned
- **sort() Method:** Sorts elements of an array in place using a compare function.
- **Ternary Operator:** `(a.year > b.year ? 1 : -1)` simplifies conditional logic.
- **Sorting Logic:** `1` means `a` should come after `b`, and `-1` means `a` should come before `b`.

---

## 4. Array.prototype.reduce()

### Code Example
```js
let toalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);
```

### What You Learned
- **reduce() Method:** Accumulates values in an array into a single result.
- **Initial Value:** `0` as the starting point for accumulation.
- **Age Calculation:** `(inventor.passed - inventor.year)` calculates how long each inventor lived.

---

## 5. Sorting by Years Lived

### Code Example
```js
let yearsLived = inventors.sort((a, b) => (a.passed - a.year) > (b.passed - b.year) ? -1 : 1);
```

### What You Learned
- **Custom Sorting:** Sorts inventors by lifespan instead of birth year.

---

## 6. Sorting People by Last Name

### Code Example
```js
let names = people.sort((a, b) => {
  let [aLast, aFirst] = a.split(', ');
  let [bLast, bFirst] = b.split(', ');
  return aLast > bLast ? 1 : -1;
});
```

### What You Learned
- **String Split:** `a.split(', ')` splits the full name into an array of `[last, first]`.
- **Destructuring Assignment:** `[aLast, aFirst]` extracts array elements into variables.

---

## 7. Counting Instances with Reduce

### Code Example
```js
let instances = data.reduce((obj, item) => {
  if (!obj[item]){
    obj[item] = 0;
  } 
  obj[item]++;
  return obj;
}, {});
```

### What You Learned
- **Object as Accumulator:** `obj` is an object (like a Python dictionary) used to count occurrences.
- **Conditional Initialization:** `if (!obj[item]) obj[item] = 0;` ensures counting starts at 0.

---

## Overall Takeaways
- **Functional Programming Concepts:** Higher-order array methods promote clean and readable code.
- **ES6+ Features:** Destructuring, arrow functions, and template literals are powerful tools for concise coding.
- **Practical Use Cases:** Sorting, filtering, transforming, and reducing data are common real-world tasks.

These notes should serve as a useful reference as you continue learning JavaScript and revisit these array methods in the future!

