# Lab Cycle - Experiment 11
---
## Question)
-Write a react program to create a list of departments and iterate through all the
elements of the list and return an unordered list with each department as a list item
using a function component.

---

## Aim:

Create a React functional component that:

- Maintains a list of departments.
- Iterates through all list elements.

```
- Returns an unordered list (`<ul>`) with each department as a list item (`<li>`).
```


***

## Source Code

### DepartmentList.js

```javascript
import React from "react";

function DepartmentList() {
  const departments = ["Computer Science", "Information Technology", "Electronics"];

  return (
    <div>
      <h2>Department List</h2>
      <ul>
        {departments.map((dept, index) => (
          <li key={index}>{dept}</li>
        ))}
      </ul>
    </div>
  );
}

export default DepartmentList;
```


***

### App.js

```javascript
import React from 'react';
import DepartmentList from './DepartmentList';

function App() {
  return (
    <div>
      <DepartmentList />
    </div>
  );
}

export default App;
```


***

## Output

### Initial Render

- Displays the heading **"Department List"**.
- Renders an unordered list with list items:
    - **Computer Science**
    - **Information Technology**
    - **Electronics**

***

---

![Initial Screen](./images/EXP_11.1.png)

---


## Explanation

### a) Array of Departments

- A constant array `departments` stores the list of department names.


### b) Array Mapping

- The `.map()` method is used to iterate over `departments`.
- Each array element (`dept`) is rendered as an `<li>` element with a unique `key` (index).


### c) JSX Rendering

- The list items are embedded inside `<ul>` in JSX.
- React dynamically renders list items based on array data during re-rendering or state changes.


### d) Key Prop

- Using `key={index}` helps React efficiently update list items when data changes.

***

## Viva Questions

1. **What is the purpose of the `map()` function in React?**
    - To iterate over array elements and generate React elements dynamically for rendering.
2. **Why is the `key` prop necessary in list items?**
    - To help React identify which items have changed, been added, or removed for efficient re-rendering.
3. **Can you use other data types in list rendering?**
    - Yes, but React expects each item to have a unique key, especially when rendering lists.
4. **What happens if you omit the `key` prop?**
    - React throws a warning, and list rendering may be less efficient or incorrect during updates.
5. **What are React hooks, and are they used here?**
    - Hooks like `useState`, `useEffect`; not used in this simple static list, but important for dynamic data.

***

## Note:

- The list is static here but can easily be made dynamic with state (`useState`) if needed.
- Array `.map()` is essential for rendering multiple elements based on data sources.

***

## Conclusion:

This experiment demonstrates iterating over an array to generate list items dynamically, a core concept in React for rendering collections of data efficiently and cleanly.

***
