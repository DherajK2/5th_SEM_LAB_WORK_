# Lab Cycle – Experiment 13

## Aim:

Write a Node.js program to read input from the console and store it in a file using the `fs` (file system) module.

***

***

## Source Code – `writeFromConsole.js`

```javascript
const fs = require("fs");
const readline = require("readline");

// Create readline interface
const r1 = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

// Read input from console
r1.question("Enter Some Text: ", (answer) => {

    // Write input to file using fs module
    fs.writeFile("output.txt", answer, (err) => {
        if (err) {
            console.log("Error: File cannot be written");
        } else {
            console.log("Entered data successfully stored in file!");
        }

        // Close readline interface
        r1.close();
    });
});
```


***

## Expected Output

### Console

```text
Enter Some Text: Hello Everyone, I am learning Coding
Entered data successfully stored in file!
```


### `output.txt` File Content

```text
Hello Everyone, I am learning Coding
```


***

## Explanation

- The `readline` module creates an interface to read user input from `stdin` and show prompts on `stdout`.
- `r1.question()` displays a prompt, waits for the user to type text, and passes that text as `answer` to the callback.
- Inside the callback, `fs.writeFile("output.txt", answer, ...)` writes the entered text into `output.txt`; if there is no error, a success message is printed, and the readline interface is closed.

