# Lab Cycle - Experiment 6

## Aim:
Write a JavaScript program to create an array of student objects, convert their marks to CGPA using the `map()` method, and display a list of students with a CGPA of 9 or higher. Also, show the total count of students with CGPA 9 and above using the `filter()` and `reduce()` methods.

---

## JavaScript Code:

```javascript
const students = [
  { name: "Henry", marks: 78 },
  { name: "Mario", marks: 90 },
  { name: "John", marks: 45 },
  { name: "Vijay", marks: 67 },
  { name: "Siddu", marks: 97 }
];

// Convert marks to CGPA (with 2 decimal places) using parseFloat
const studentsWithCGPA = students.map(student => ({
  name: student.name,
  cgpa: student.marks / 10 // ensures CGPA is a number
}));

// Filter top students with CGPA >= 9
const topStudents = studentsWithCGPA.filter(student => student.cgpa >= 9);

// Count of top students
const countTopStudents = topStudents.reduce((count, _) => count + 1, 0);

// Output
console.log("Top students with CGPA >= 9:");
topStudents.forEach(student => {
  console.log(`${student.name} - CGPA: ${student.cgpa.toFixed(2)}`);
});

console.log(`Number of top students with CGPA >= 9: ${countTopStudents}`);
```

## Output:
```
Top students with CGPA >= 9:
Mario - CGPA: 9.00
Siddu - CGPA: 9.70
Number of top students with CGPA >= 9: 2

```

---

## Explanation:

- **`map()`**: For converting marks to CGPA by dividing marks by 10.
- **`filter()`**: For Filtering students with CGPA ≥ 9.
- **`reduce()`**: For counting how many students have CGPA ≥ 9.
- **`.toFixed(2)`**: Used during output to format CGPA to two decimal places. This ensures consistent display like `9.00` instead of just `9`.

---

## Viva :
- **`map()`**:  
  - `map()` is a **higher-order array method** in JavaScript.  
  - It is used to **transform** each element of an array and return a **new array** with the transformed values.  
  - In this program, it converts each student's `marks` into `CGPA` by dividing the marks by 10.

- **`filter()`**:  
  - `filter()` is another **higher-order array method**.  
  - It is used to **select elements** from an array that satisfy a given condition.  
  - In this case, it filters out the students who have a CGPA **greater than or equal to 9**.

- **`reduce()`**:  
  - `reduce()` is used to **reduce the array to a single value** (e.g., a total, sum, or count).  
  - It takes a function and an initial value, and applies the function to each element to accumulate a result.  
  - Here, it is used to **count** the number of top-performing students.

- **`.toFixed(2)`**:  
  - This is a **number method** in JavaScript.  
  - It formats a number to **2 decimal places** and returns it as a **string**.  
  - For example, if CGPA is `9`, `.toFixed(2)` converts it to `"9.00"` for cleaner output.

---

## Note :
-`filter()`, `map()` creates a new array
---
