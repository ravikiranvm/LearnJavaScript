# Day 6: JavaScript30 — City Search Project

## Overview
On Day 6 of the JavaScript30 series, we built a dynamic search feature that allows users to search for cities and states in real-time. The data for this project is fetched from an external JSON endpoint containing information about U.S. cities, including their names, states, and populations.

---

## Code Explanation

```javascript
const endpoint = 'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json';
```
- **`endpoint`**: A URL that points to a JSON file containing an array of city data objects. Each object includes the city name, state, and population.

```javascript
const cities = [];
fetch(endpoint).then(blob => blob.json())
                .then(data => cities.push(...data));
```
- **`cities`**: An empty array to store the city data.
- **`fetch`**: Makes a network request to the endpoint and returns a **`Promise`**.
- **`.then(blob => blob.json())`**: Converts the raw response (`blob`) into a JSON object.
- **`.then(data => cities.push(...data))`**: Uses the **spread operator (`...`)** to push each city object into the **`cities`** array.

### **Finding Matches**

```javascript
function findMatches(wordToMatch, cities) {
  return cities.filter(place => {
    const regex = new RegExp(wordToMatch, 'gi');
    return place.city.match(regex) || place.state.match(regex)
  });
}
```
- **`findMatches`**: Takes the search input and returns an array of matching cities or states.
- **`filter`**: Returns a new array containing elements that pass the test function.
- **`RegExp`**: Dynamically creates a regular expression to match the input text (**`wordToMatch`**) in a case-insensitive (**`i`**) and global (**`g`**) manner.
- **`.match`**: Checks if the city or state name contains the input text.

### **Displaying the Matches**

```javascript
function displayMatches() {
  const matchArray = findMatches(this.value, cities);

  const html = matchArray.map(place => {
    return `
      <li>
        <span class="name">${place.city}, ${place.state}</span>
        <span class="population">${place.population}</span>
      </li>
    `;
  }).join('');
  suggestions.innerHTML = html;
}
```
- **`displayMatches`**: Generates the HTML to display the filtered results.
- **`this.value`**: Refers to the current value of the search input field.
- **`.map()`**: Transforms each city object into an HTML `<li>` element.
- **`.join('')`**: Combines the array of HTML strings into a single string.
- **`suggestions.innerHTML = html`**: Updates the DOM to display the suggestions.

### **Connecting to the DOM**

```javascript
const searchInput = document.querySelector('.search');
const suggestions = document.querySelector('.suggestions');
```
- **`querySelector`**: Selects elements from the DOM using CSS selectors.
- **`searchInput`**: References the search input field.
- **`suggestions`**: References the `<ul>` where results will be displayed.

### **Event Listeners**

```javascript
searchInput.addEventListener('change', displayMatches);
searchInput.addEventListener('keyup', displayMatches);
```
- **`addEventListener`**: Attaches events to elements.
- **`change`**: Triggers when the input field loses focus after a change.
- **`keyup`**: Triggers every time a key is released, enabling real-time search.

---

## Key Concepts Learned
1. **Fetching Data from an API** using the `fetch` method and handling promises.
2. **Manipulating the DOM** by dynamically updating HTML content.
3. **Regular Expressions (`RegExp`)** for dynamic search functionality.
4. **Array Methods (`filter`, `map`, `join`)** to transform and display data.
5. **Event Handling** to create an interactive user experience.
6. **Template Literals (`${}`)** for embedding expressions within HTML strings.

---

## Potential Use Cases
- Creating live search features for websites and applications.
- Building autocomplete functionality.
- Implementing dynamic filtering of data lists.
- Learning more about asynchronous programming and promise chaining.

