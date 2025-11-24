# Lab Cycle - Experiment 12

## Aim:

Write a Node.js program to:
1. Create an HTTP server that listens on port 8000.
2. Respond with “Welcome to Nodejs” when the root URL (/) is accessed.
3. Return a 404 status with a custom message for all other routes.

***
---
## Source Code
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    if (req.url === '/') {
        res.writeHead(200, { 'Content-Type': 'text/plain' }); // fixed 'text/palin' -> 'text/plain'
        res.end('Welcome To Node.js');
    } else {
        res.writeHead(404, { 'Content-Type': 'text/plain' }); // changed status code to 404
        res.end('404 Not Found - Invalid Route');
    }
});

// Run the server on port 8000
server.listen(8000, () => {
    console.log('Server running on http://localhost:8000');
});


//Output 
// Server running on http://localhost:8000
```
