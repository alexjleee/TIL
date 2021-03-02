# Using URL Hash In JS

## What Is Hash (#)

In URL, the part that comes after the hashtag (#), hash or also called _URL fragment_, refers to a section within the page.

Hash also can be used to pass a value with the URL and load the web page based on that value.

### URL Structure
`https://www.example.com/index.html/?param=value#fragment`

- Domain : `https://www.example.com` -> IP address
- Path : `/index.html/` -> refers to a file or directory on the web server
- Query String : `?param=value` -> communicate values to the server (server-side)
- Fragment (Hash) : `#fragment` -> pass a value to the browser (client-side)

## How To Get Hash From URL in JS

```javascript
// (1) Hash of the current URL
const hash = window.location.hash;

// (2) Hash of a given URL
const exampleUrl = 'https://www.example.com/index.html/#fragment';
const hash = new URL(exampleUrl).hash;

// to remove '#' at the beginning of the 'hash' string
const hashValue = hash.replace('#', '');
```

## How To Change Hash From URL in JS

```javascript
// (1) Hash of the current URL
const urlObj = new URL(document.URL);
urlObj.hash = '#changedfragment';
const newUrl = urlObj.href;
document.location.href = newUrl;

// (2) Hash of a given URL
const exampleUrl = 'https://www.example.com/index.html/#fragment';
const urlObj = new URL(exampleURL);
urlObj.hash = '#changedfragment';
const newUrl = urlObj.href;
// "https://www.example.com/index.html/#changedfragment"
```

## How To Detect Hash Changing in JS

```javascript
window.addEventListener('hashchange', function () {
	const newHash = new URL(document.URL).hash;
	console.log(`The hash has changed to "${newHash}"`);
});
```
