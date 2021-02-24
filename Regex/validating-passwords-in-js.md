# Validating Passwords in JS
Rules :
  - must contain at least 8 characters
  - must contain at least 1 number
  - must contain at least 1 lowercase letter
  - must contain at least 1 uppercase letter
  - must contain at least 1 special character 

```javascript
const pwRegex = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[~!@#$%^&*()\-_=+[\]{}\\|;:'",.<>/?])[\da-zA-Z~!@#$%^&*()\-_=+[\]{}\\|;:'",.<>/?]{8,}$/;

const passwords = ['12345678', 'Acbd1234', 'Abcd1234!'];

passwords.forEach((pw) => {
  const isMatch = pw.match(pwRegex);
  if (!isMatch) {
    console.log('Invalid!');
  } else {
    console.log('Valid');
  }
});

// Invalid!
// Invalid!
// Valid
```
Password regex explained
  - `^` : beginning of the string
  - `(?=.*\d)` : must contain at least 1 number(digit)
  - `(?=.*[a-z])` : must contain at least 1 lowercase letter
  - `(?=.*[A-Z])` : must contain at least 1 uppercase letter
  - `(?=.*[~!@#$%^&*()\-_=+[\]{}\\|;:'",.<>/?])` : must contain at least 1 special character 
  - `[\da-zA-Z~!@#$%^&*()\-_=+[\]{}\\|;:'",.<>/?]{8,}` : must contain at least 8 characters (numbers, lower/uppercase letters, special characters)
  - `$` : end of the string