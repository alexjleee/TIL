# Events Module

> Node.js built-in `events` module allows you to create, fire and listen for custom events.

Node.js is _event-driven_. The `events` module is the core of the event-driven architecture of Node.js.

The `event` module has `EventEmitter` class, which contains functions to take care of events. 

An `EventEmitter` object has two main functions:
- Emit named events
- Register/Unregister event listeners to the named events

In Node.js many built-in modules inherit this `EventEmitter` class. For example, streams extend `EventEmitter` and use predefined events like `open`, `end`, and `data`.
- Example : 
  ```javascript
  const fs = require('fs');

  const readStream = fs.createReadStream(__dirname + '/data.txt', 'utf8');

  readStream.on('data', (chunk) => {
    console.log('new chunk received');
    console.log(chunk);
  });
  ```

## How To Use Events Module

```javascript
// (1) include events module
const EventEmitter = require('events');
// 'EventEmitter' starts with a capital letter because it is a class

// (2) create a new event emitter instance
const emitter = new EventEmitter();

// (3) '.on(eventName, listener)' : register event listener
emitter.on('event', (msg) => {
  console.log(msg);
});

// (4) '.emit(eventName[, args])' : trigger the event
emitter.emit('event', 'An event emitted.');

// You must register event listeners before triggering the event!
```

## More Methods Of EventEmitter

- `.off(eventName, listener)` : remove the specified listener from the specified event
- `.once(eventName, listener)` : register a **one-time** listener