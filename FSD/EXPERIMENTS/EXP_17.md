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


---


## Output

- **Console Output**  
- `Server running on http://localhost:8000`  

- **Browser Output**  
- For `/` → `Welcome to Nodejs`  
- For `/abc` → `404 Not Found - Invalid Route`  

Status code **200** indicates a successful response, while **404** indicates that the requested resource was not found.[web:30][web:12]  

---

## Explanation

### a) HTTP Module and createServer

- The `http` module is a core Node.js module used to create web servers that handle HTTP requests and responses.[web:8][web:31]  
- The `http.createServer((req, res) => { ... })` callback runs for every incoming request, providing `req` (request) and `res` (response) objects.[web:23][web:25]  

### b) Routing with req.url

- `req.url` contains the path part of the request, such as `/`, `/about`, etc.[web:23]  
- An `if` condition checks if `req.url === '/'` for the root path; otherwise, the request is treated as an invalid route.  

### c) Headers, Status Codes, and Response

- `res.writeHead(200, { 'Content-Type': 'text/plain' })` sets the status code to 200 and the `Content-Type` header to indicate that the body is plain text.[web:8][web:29]  
- `res.writeHead(404, { 'Content-Type': 'text/plain' })` sets a 404 client error status for unknown routes, signaling that the resource is not found.[web:12][web:30]  
- `res.end()` sends the response body and ends the HTTP response.[web:23][web:29]  

---

## Viva Questions

1. **What is the purpose of `http.createServer()` in Node.js?**  
- It creates an HTTP server that can receive requests and send responses over the HTTP protocol.[web:21][web:31]  

2. **What does the `req` object represent?**  
- It represents the incoming HTTP request, containing details like method, URL, and headers.[web:25][web:23]  

3. **What is the role of `res.writeHead()`?**  
- It sets the HTTP status code and response headers before sending the body.[web:8][web:29][web:26]  

4. **What does HTTP status code 404 indicate?**  
- It indicates that the server cannot find the requested resource at the specified URL.[web:12][web:30]  

5. **Why do we specify `Content-Type: text/plain`?**  
- To tell the client that the response body is plain text so it can be rendered correctly.[web:13][web:8]  

---

## Note

- Always close responses using `res.end()` to complete the HTTP transaction cleanly.[web:23][web:29]  
- Using proper status codes like 200 and 404 makes it easier for clients and tools to understand the result of a request.[web:30][web:35]  
- The HTTP module is sufficient for simple servers; frameworks like Express build on top of it for larger applications.[web:31][web:25]  

---

## Conclusion

This experiment explains how to create a simple HTTP server in Node.js that listens on a specific port, serves a custom message at the root route, and returns an appropriate 404 response with a custom message for all other routes using core HTTP features.[web:21][web:23][web:30]  


