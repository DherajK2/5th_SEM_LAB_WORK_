# Lab Cycle – Experiment 16

## Aim:

Explain and demonstrate various debugging and logging methods in Node.js to:

1. Measure execution time of code blocks.
2. Group related log messages hierarchically.
3. Use assertions to conditionally display error messages.
4. Display data in a tabular format.
5. Log debugging details for analysis.

***

***

## Source Code – `debugDemo.js`

```javascript
// Start measuring total execution time
console.time("Execution Time:");

// Grouping related log messages
console.group("User 1 Details");
console.log("Name : Bob");
console.log("Age : 20");
console.groupEnd();

// Assertion checks
const x = 10;
console.assert(x < 20, "x is lesser than 20");      // Passes, no output
console.assert(x > 20, "x is not lesser than 20"); // Fails, shows error

// Displaying data in table format
const student = [
    { name: "Mr Bean", age: 20 },
    { name: "Teddy", age: 5 },
    { name: "John", age: 10 }
];

// Full table
console.table(student);

// Display only selected column
console.table(student, ['name']);

// Debugging message for development analysis
console.debug("This is a debugging message");

// Stop timer and display execution time
console.timeEnd("Execution Time:");
```


***

## Expected Output (Console)

```text
User 1 Details
  Name : Bob
  Age : 20

Assertion failed: x is not lesser than 20

┌─────────┬───────────┬─────┐
│ (index) │   name    │ age │
├─────────┼───────────┼─────┤
│    0    │ 'Mr Bean' │ 20  │
│    1    │  'Teddy'  │  5  │
│    2    │  'John'   │ 10  │
└─────────┴───────────┴─────┘

┌─────────┬───────────┐
│ (index) │   name    │
├─────────┼───────────┤
│    0    │ 'Mr Bean' │
│    1    │  'Teddy'  │
│    2    │  'John'   │
└─────────┴───────────┘

This is a debugging message
Execution Time:: <some milliseconds>
```

(The exact execution time will vary each run.)

***

## Explanation

- `console.time()` and `console.timeEnd()` measure how long the script section takes to execute.
- `console.group()` and `console.groupEnd()` visually nest related log messages under *User 1 Details*.
- `console.assert()` only prints when a condition is false, so only the second assertion shows an error.
- `console.table()` prints the `student` array as a formatted table, first with all columns, then with only the `name` column.
- `console.debug()` prints an extra debugging line useful during development.

***

## How to Run

```bash
node debugDemo.js
```

