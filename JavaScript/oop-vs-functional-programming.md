# OOP vs. Functional Programming

> **Programming paradigms** are how you organise your code. JS is a multi-paradigm language, you can write _object-oriented_ or _functional_ code or even both. Both paradigms help you to write clear and understandable code that is easy to maintain and extend.

## Object-Oriented Programming

> **OOP** means that you organise your code in _logical entities_ (objects containing data in form of fields, logic in form of methods).

Core concepts of OOP

- **Encapsulation** : The data and logic that are related are bound together.
- **Abstraction** : When a method is called, the complexity and the implementation detail are hidden.
- **Inheritance** : A child class extends properties and methods from its parent class.
- **Polymorphism** : 
  - Overriding : If there are methods in the parent class and its child class with the same name, the one in the child class overrides the one of the parent class.
  - Overloading : There can be more than two methods with same name but with different number of argument or with different data type.

## Functional Programming

> **Functional Programming** means that you organise your code in (pure) _functions_ with clearly defined tasks and pass data via parameters. The data and the behaviors(functions) should be kept separated.

- The function should perform single task.
- The function should be **pure**.
- The function should have `return` statement.
- The function should be immutable - should not change the original state.

### What is a _pure_ function? 
- If the input value is the same, it must return the same value.
- No side effects! - it does not modify its outer world.

## Example

- Goal : Get input values for username and password and check if they are valid. If so, create a new user and print a greeting message in the console.

```html

<form id="user-input">
  <label for="username">Username: </label>
  <input type="text" id="username" />
  <br />
  <label for="password">Password: </label>
  <input type="password" id="password" />
  <br />
  <button type="submit">Create User</button>
</form>

```

1. OOP

```javascript
// Validation
class Validator {
  // static methods and properties can be called without instantiating the class
  static REQUIRED = 'REQUIRED';
  static MIN_LENGTH = 'MIN_LENGTH';
  static MAX_LENGTH = 'MAX_LENGTH';

  static validate(value, flag, compareValue) {
    switch (flag) {
      case this.REQUIRED:
        return value.trim().length > 0;
      case this.MAX_LENGTH:
        return value.trim().length <= compareValue;
      case this.MIN_LENGTH:
        return value.trim().length >= compareValue;
      default:
        break;
    }
  }
}

// User handling
class User {
  constructor(username, password) {
    this.username = username;
    this.password = password;
  }

  greet() {
    console.log(`Hi, ${this.username}`);
  }
}

// Form handling
class UserInputForm {
  constructor() {
    this.form = document.getElementById('user-input');
    this.usernameInput = document.getElementById('username');
    this.passwordInput = document.getElementById('password');

    this.form.addEventListener('submit', this.signupHandler.bind(this));
  }

  signupHandler(e) {
    e.preventDefault();

    const enteredUsername = this.usernameInput.value;
    const enteredPassword = this.passwordInput.value;

    if (!Validator.validate(enteredUsername, Validator.REQUIRED) || !Validator.validate(enteredUsername, Validator.MAX_LENGTH, 15) || !Validator.validate(enteredPassword, Validator.MIN_LENGTH, 8)) {
      alert('Invalid input');
      return;
    }

    const newUser = new User(enteredUsername, enteredPassword);
    newUser.greet();
  }
}

// Instanciating UserInputForm class
new UserInputForm();
```

2. Functional Programming

```javascript
// Global variables
const REQUIRED = 'REQUIRED';
const MAX_LENGTH = 'MAX_LENGTH';
const MIN_LENGTH = 'MIN_LENGTH';

// Get input value
function getInputValue(inputId) {
  return document.getElementById(inputId).value;
}

// Validation
function validate(value, flag, compareValue) {
  switch (flag) {
    case REQUIRED:
      return value.trim().length > 0;
    case MAX_LENGTH:
      return value.trim().length <= compareValue;
    case MIN_LENGTH:
      return value.trim().length >= compareValue;
    default:
      break;
  }
}

// Create user
function createUser(username, password) {
  if (!validate(username, REQUIRED) || !validate(username, MAX_LENGTH, 15) || !validate(password, MIN_LENGTH, 8)) {
    throw new Error('Invalid input');
  }
  return {
    username: username,
    password: password
  }
}

// Greet user
function greetUser(user) {
  console.log(`Hi, ${user.username}`);
}

// Signup handling
function signupHandler(e) {
  e.preventDefault();

  const enteredUsername = getInputValue('username');
  const enteredPassword = getInputValue('password');

  try {
    const newUser = createUser(enteredUsername, enteredPassword);
    greetUser(newUser);
  } catch (err) {
    alert(err.message);
  }
}

// Attach submit handler to a form
function addSubmitHandler(formId, submitHandler) {
  const form = document.getElementById(formId);
  form.addEventListener('submit', submitHandler);
}

// Call addSubmitHandler function when the app is initialised
addSubmitHandler('user-input', signupHandler);
```