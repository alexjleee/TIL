# Base64 Encoding & Decoding

## What is Base64

- Binary to text(ASCII) encoding scheme
- Represent binary data in ASCII string format
- Only use 64 characters to represent the data: A-Z a-z 0-9 + / (and = for padding, so 65 characters in total)
- Encoding Process
  1. Recieve input in the form of 8-bit bytes
  2. Organize the input into 24-bit groups (three 8-bit bytes)
  3. Recroup each 24-bit group into four 6-bit groups
  4. Each 6-bit group is converted into a single character of the Base64 alphabets

- [Base64 Encoding & Decoding Tool](https://www.base64encode.org/)

## How To Encode & Decode Base64 In JS

- `btoa()` : Binary to ASCII : Encode a string into a base64 ASCII string form
- `atob()` : ASCII to Binary : decode a base64

```javascript
let str = 'Hello';

let encodedStr = btoa(str);
console.log(encodedStr); // "SGVsbG8="

let decodedStr = atob(encodedStr);
console.log(decodedStr); // "Hello"
```

## Useage

1. To store/transfer binary data without corruption of the content
  - It is URL-safe. It is used in encoding data in Data URLs since it consists only of ASCII characters.

2. To embed image (or even sound) files in HTML or CSS instead of depending on external files.
  - [Base64 Image Converter](https://www.base64-image.de/)
  - It is often used in emails.
  - Bear in mind, Base64 encoding causes increase in size (about 33~36%).

3. WARNING! It is NOT for _encrypting_!
