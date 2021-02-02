# Making HTTP Request

## AJAX

Asynchronous Javascript And XML

- But these days JSON is more commonly used than XML
- Communication between the browser and the server happens behind the scene (not inbtetween page loads) and the user stays on the same page.
- JSON (JavaScript Object Notation) is a format for storing and transporting data (for servers and browsers). It looks much like JS, so it is easy to convert between JSON and JS.

## 1. XMLHttpRequest

- Old way of sending requests via JS
- It is an object in the browser that has methods to fetch data from an API. It can fetch not only XML but also any sort of data.
- Donnot support Promise
- Example :

```javascript
// First request
const firstReq = new XMLHttpRequest();

// if first request successful
firstReq.addEventListener('load', function () {
	console.log('First request successful');
	const data = JSON.parse(this.responseText);
	// 'this' = swReq = XMLHttpRequest {... response: "{...}", responseText: "{...}", ...}
	console.log(data);
	// Second request (dependent on the first request)
	const secondURL = data.next;
	const secondReq = new XMLHttpRequest();

	// if second request successful
	secondReq.addEventListener('load', function () {
		console.log('Second request successful');
		const data = JSON.parse(this.responseText);
		console.log(data);
	});

	// if second request unsuccessful
	secondReq.addEventListener('error', function (e) {
		console.log('Error', e);
	});

	// Open second request
	secondReq.open('GET', secondURL);
	// Send second request
	secondReq.send();
});

// if first request unsuccessful
firstReq.addEventListener('error', function (e) {
	console.log('Error', e);
});

// Open first request
firstReq.open('GET', 'https://someapi.dev/api/');
// Send first request
firstReq.send();
```

## 2. Fetch

- Newer way of sending requests via JS
- Support Promise (`fetch` returns a Promise)
- Not supported in IE
- Example :

```javascript
const checkAndParse = (res) => {
	if (!res.ok) {
		// throw an error so 'catch' can catch
		throw new Error(`Status Code Error: ${res.status}`);
	} else {
		console.log('Request successful');
		// response object is a readable stream
		// to read the stream use 'response.json()' which returns a Promise
		return res.json();
	}
};

const printData = (data) => {
	console.log(data);
	// return a resolved promise
	return Promise.resolve(data.next);
};

const fetchData = (url = 'https://someapi.dev/api/') => {
	return fetch(url);
};

fetchData()
	.then(checkAndParse)
	.then(printData)
	.then(fetchData)
	.then(checkAndParse)
	.then(printData)
	.catch((err) => {
		console.log(err);
	});
// the Promise returned from 'fetch()' won't reject on HTTP error status (that's why you need to throw error)
```

## 3. AXIOS

- External library for making HTTP requests
- [github/axios](https://github.com/axios/axios)
- Make XMLHttpRequests from the browser & from Node.js
- Support Promise
- Unlike `fetch`, you don't need to parse JSON nor check the status code.
- Example :

```javascript
const fetchNext = (url = 'https://someapi.dev/api/') => {
	return axios.get(url);
};

const printData = ({ data }) => {
	console.log(data);
	return Promise.resolve(data.next);
};

fetchNext()
	.then(printData)
	.then(fetchNext)
	.then(printData)
	.catch((err) => {
		console.log(err);
	});
```
