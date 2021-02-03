# Async & Await

> JS is synchronous but you can make it to behave asynchronously by using :
>
> - Asynchronous Callbacks
> - Promises
> - Async & Await

## Async & Await

The `async` keyword designates a function as an async function and this function returns a Promise.

- If the function returns a value -> Promise resolved with the value
- If the function throws an exception -> Promise rejected

> `async function funcName() { ... }`

The `await` keyword can only be used inside of a function with `async` keyword. `await` pauses `async` function until a Promise is resolved.

- Example :

```javascript
// Without async & await
function getData() {
	return axios.get('https://someapi.dev/api/');
}
getData().then((res) => {
	console.log(res.data);
});
```

```javascript
// With async & await
async function getData() {
	const res = await axios.get('https://someapi.dev/api');
	console.log(res.data); // <- run after the Promise is resolved
}
getData();
```

## Sequential / Parallel Requests

Sequential Request : Send requests one at a time and wait for each one to be resolved before request next one.

- Example :

```javascript
async function getDatas() {
	const result1 = await axios.get('https://someapi.dev/api/1');
	const result2 = await axios.get('https://someapi.dev/api/2');
	console.log(result1.data);
	console.log(result2.data);
}
getDatas();
```

Parallel Request : Next requests don't wait for the previous ones to be resolved.

- Example :

```javascript
async function getDatas() {
	const promise1 = axios.get('https://someapi.dev/api/1');
	const promise2 = axios.get('https://someapi.dev/api/2');
	const results = await Promise.all([promise1, promise2]);
	console.log(results[0].data);
	console.log(results[1].data);
}
getDatas();
```

## Handling Error

- Use `.catch()`

```javascript
async function getData() {
	// ...
}
getData().catch((err) => {
	// handel error
});
```

- Use `try` & `catch`

```javascript
async function getData() {
	try {
		// ...
	} catch (err) {
		// handle error
	}
}
getData();
```
