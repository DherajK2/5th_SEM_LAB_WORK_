# Lab Cycle – Experiment 15

## Aim:

Illustrate how to:

1. Add an event listener in Node.js.
2. Emit an event to trigger the listener.
3. Remove the event listener so it no longer responds.

***

***

## Source Code – `eventExample.js`

```javascript
const EventEmitter = require('events');
const event = new EventEmitter();

// Listener function
function greet(name){
    console.log("Hello " + name);
}

// Add event listener
event.on("Welcome", greet);

// Emit event (listener executes)
event.emit("Welcome", "Dheraj K");
event.emit("Welcome", "Charles");

// Remove event listener
event.off("Welcome", greet);

// This will not execute since listener is removed
event.emit("Welcome", "Bob");
```


***

## How It Works

- `EventEmitter` is a core Node.js class used to create and handle custom events.
- `event.on("Welcome", greet)` registers `greet` as a listener for the `"Welcome"` event.
- `event.emit("Welcome", "Dheraj K")` and `event.emit("Welcome", "Charles")` trigger the listener and print greetings.
- `event.off("Welcome", greet)` removes the listener, so the final `emit` for `"Bob"` does not produce any output.

***

## How to Run

```bash
node eventExample.js
```

Expected console output:

```text
Hello Dheraj K
Hello Charles
```

(No output for `"Bob"` because the listener was removed.)

