# Event Propagation

The events in JS propagates through the DOM tree from the root to the target and back.

The event propagation can be divided into 3 phases: **capturing phase**, **target phase** and **bubbling phase**.

## 1. Capturing Phase

Event is actually generated at the root of the document (at the top of the DOM tree).

Then the event travels down from the document root to the target element, passing through all the parent elements of the target element.

You can manually set event listeners to listen to events in the capturing phase instead of the bubbling phase.
By default, events are only handled in the target/bubbling phase.
  - ```el.addEventListener('click', listener, true)``` : In this `addEventListener` syntax, the third argument (which is optional and by default `false`) is `capture`, which is a boolean indicating whether the handler is set on the capturing phase.

## 2. Target Phase

As soon as the event reaches the target element, the target phase begins.

All the event handlers, assigned to the target for the type of event, are executed during this phase.

## 3. Bubbling Phase

After the target phase, the event travels back to the document root.

The event passes through all the parent elements of the target element, just like in the capturing phase. If any of the parent elements has event handlers assigned for the type of event, they are executed during this phase.

cf. Most of the events bubbles but there are a few exceptions such as `focus`.

```html
<ul>
  <li><a>Home</a></li>
  <li><a>About</a></li>
  <li><a>Contact</a></li>
</ul>
```

```javascript
document.querySelectorAll('a').forEach((el) => {
  el.addEventListener('click', (e) => {
    console.log('target: ' + e.target.tagName);
    console.log('current target: ' + e.currentTarget.tagName);
  })
});
document.querySelectorAll('li').forEach((el) => {
  el.addEventListener('click', (e) => {
    console.log('target: ' + e.target.tagName);
    console.log('current target: ' + e.currentTarget.tagName);
  })
});
document.querySelectorAll('ul').forEach((el) => {
  el.addEventListener('click', (e) => {
    console.log('target: ' + e.target.tagName);
    console.log('current target: ' + e.currentTarget.tagName);
  })
});

// If you click any anchor,

// target: A
// current target: A
  // => (target phase) event handler on 'a' is executed
// target: A
// current target: LI
  // => (bubbling phase) event handler on 'li' is executed
// target: A
// current target: UL
  // => (bubbling phase) event handler on 'ul' is executed
```

`event.target` (where the event actually happened) doesn't change through the bubbling phase. On the other hand, `event.currentTarget` is the element on which the currently running handler is.