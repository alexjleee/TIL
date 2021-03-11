# Event Handling

> An event a signal that something has happened.

cf. Events are always happening regardless of whether we are listening for them or not.

## Event Types
1. Mouse Events
  - `click` : fires when a full click action (pressed & released) occurs on an element
  - `mousedown` / `mouseup` : fires when the mouse button is pressed/released on an element
  - `mousemove` : fires when the mouse cursor moves inside an element
    - If the mouse cursor moves too fast, some intermediate elements may be skipped.
  - `mouseover` / `mouseout` : fires when the mouse cursor is over/left an element
    - they are triggered even when the mouse cursor moves between an element and its child (because the child element obscures the visible area of the element)
  - `mouseenter` / `mouseleave` : fires when the mouse cursor enters/leaves an element
    - they do _NOT_ bubble up - can't use **event delegation**
    - they are _NOT_ triggered even when the mouse cursor moves between an element and its child
  cf. `mouseover` / `mouseout` and `mouseenter` / `mouseleave` have an additional property: `relatedTarget`, referring the element that the cursor is coming from/to

2. Keyboard Events
  - `keydown` / `keyup` : fires when a key is pressed/released

3. Form Events
  - `submit` : fires when the user submits a `<from>`
  - `change` : fires when an input loses the focus and its value has been changed

4. HTML Frame/Object Events
  - `resize` : fires when the document view is resized
  - `scroll` : fires when the element/document view is scrolled

## How To Handle Events

1. HTML attribute `on<event>`
2. `on<event>` DOM property
3. `addEventListener`
  - Why should you use `addEventListener` instead of `on<event>`?
    - It allows you to add multiple event listeners to one event (since there's only one `on<event>` property, the latter will overwrite the former)
      ```javascript
      el.onclick = () => alert('alert message');
      el.onclick = () => alert('this will overwrite the former handler');
      // you won't be able to see the first message, only the second one
      ```
      ```javascript
      el.addEventListener('click', () => alert('alert message'));
      el.addEventListener('click', () => alert('alert message 2'));
      // the handlers will run in order so you will see both messages
      ```
    - You can remove an event handler in case we don't need it anymore

    cf. How to remove an event handler
      ```javascript
      const alertFunc = function(e) => {
        alert('alert message');
        el.removeEventListener('click', alertFunc);
      };
      el.addEventListener('click', alertFunc);
      // `removeEventListener` requires the same function that you used on `addEventListener`
      ```
      


