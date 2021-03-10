# What Exactly Is The DOM

> The **Document Object Model (DOM)** is a cross-platform and language-independent **interface** that treats an XML or HTML document as a **tree structure** wherein each **node** is an **object** representing a part of the document. (from [Wikipedia](https://en.wikipedia.org/wiki/Document_Object_Model))

- When a page is loaded, the browser generates a DOM from the HTML (or XML) document.

- The DOM is an API that contains useful methods and properties to interact with the DOM tree.

- The DOM allows JS to interact with the HTML. JS uses the DOM to access the document and its elements.
  - create, add, modify and remove HTML elements, styles, classes and attributes
  - listen and respond to events

### Example Of The DOM Tree

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>About DOM</title>
  </head>
  <body>
    <!-- a comment here-->
    <h1>What Exactly Is The DOM?</h1>
  </body>
</html>
```

- Document
  - Element `<html>`
    - Element `<head>`
      - Element `<title>`
        - Text `About DOM`
    - Element `<body>`
      - Comment `a comment here`
      - Element `<h1>`
        - Text `What Exactly Is The DOM?`

## Data Types (Interfaces) Of The DOM
- EventTarget
  - Node
    - Document
    - Element
      - HTMLElement
        - HTMLDivElement, HTMLButtonElement, ... (each HTML element has its own type of HTMLElement)
    - Text (text between tags)
    - Comment
  - Window

All the child types inherit methods and properties of their parent types.

### Frequently Used Methods & Properties Of Each Type
- EventTarget
  - `.addEventListener()`
  - `.dispatchEvent()`
  - `.removeEventListener()`
  - Any type of node in the DOM inherits the event methods from this DOM interface.
  - In practice, you don't manually create an `EventTarget` object.
- Node
  - `.textContent`
  - `.childNodes`
  - `.parentNode`
  - `.cloneNode()`
  - `.appendChild()`
  - `.removeChild()`
  - `.insertBefore()`
- Window
  - It is the **global object** and has methods and properties related to the window containing the DOM document.
  - `.document`
  - `.window`
  - `.innerWidth` & `.innerHeight`
  - `.scrollX` & `.scrollY`
- Document
  - `.querySelector()`
  - `.querySelectorAll()`
  - `.getElement[s]By...()`
- Element
  - `.querySelector()`
  - `.querySelectorAll()`
  - `.getElement[s]By...()`
  - `.innerHTML`
  - `.classList`
  - `.children`
  - `.parentElement`
  - `.append()`
  - `.remove()`
  - `.setAttribute()` & `.getAttribute()`
  - `.scrollIntoView()`