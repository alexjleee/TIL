# setTimeout Error Handling

```javascript
function throwTimeoutError() {
	setTimeout(() => {
		throw new Error('Something went wrong!');
	}, 1000);
}

try {
	throwTimeoutError();
} catch (err) {
	console.log('Error!', err);
}
// Uncaught Error
```

Above `try-catch` won't work since `try-catch` is synchronous but `setTimeout()` isn't. By the time the callback is passed to `setTimeout()`, the `try-catch` will be gone already.

To handle errors,

(1) put `try-catch` inside the `setTimeout()`

```javascript
function throwTimeoutError() {
	setTimeout(() => {
		try {
			throw new Error('Something went wrong!');
		} catch (err) {
			console.log('Error!', err);
		}
	}, 1000);
}

throwTimeoutError();
// Error! Error: Something went wrong!
```

or
(2) wrap it with a `Promise`

```javascript
function throwTimeoutError() {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			reject(new Error('Something went wrong!'));
		}, 1000);
	});
}
throwTimeoutError().catch((err) => console.log('Error!', err));
// Error! Error: Something went wrong!
```
