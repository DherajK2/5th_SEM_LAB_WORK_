# ✅ Experiment 14: Custom Module in Node.js (File Operations)

## 🎯 Aim

To apply the concept of **custom modules in Node.js** by creating a module that can:

- Write data to a file  
- Read data from a file  
- Append data to a file  

…and then use this custom module inside another file (`app.js`) to perform file operations.

---

## 🛠️ Source Code

### 📄 fileOperations.js

```javascript
const fs = require('fs');

function writeFile(filename, data) {
    fs.writeFileSync(filename, data);
    console.log("Data written successfully");
}

function readFile(filename) {
    const data = fs.readFileSync(filename, "utf-8");
    console.log("File content:", data);
}

function appendFile(filename, data) {
    fs.appendFileSync(filename, data);
    console.log("Data appended successfully");
}

module.exports = { writeFile, readFile, appendFile };
```
---

📄 app.js
```javascript
const fileOps = require('./fileOperations.js');

fileOps.writeFile("sample.txt", "Hello");
fileOps.appendFile("sample.txt", "\nWelcome to Node.js");
fileOps.readFile("sample.txt");
```
---



## ✅ Output
Data written successfully
Data appended successfully
File content: Hello
Welcome to Node.js


A new file named sample.txt will be created with the following content:

Hello
Welcome to Node.js

📌 Result

Thus, the concept of Custom Modules in Node.js was successfully implemented and file operations were performed using the custom module.

🎤 Viva Questions

What is a custom module in Node.js?

Which module is used for file handling in Node.js?

What is the use of module.exports?

What is the purpose of require() in Node.js?

Difference between writeFileSync() and appendFileSync()?

What happens if the file does not exist while using readFileSync()?

Why do we use separate modules in Node.js?

What is synchronous and asynchronous file handling?

Can we have multiple functions in one module?

What is the extension used for Node.js files?
