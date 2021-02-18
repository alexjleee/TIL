# Debounce Function

Debounce function improves the performance of the code by preventing a function from being repeatedly called. Instead, it forces a function to be called only after it stops being called for a certain amount of time.

- Commonly used on `resize`, `scroll`, `keyup/keydown` and `input` events.

For example, if you are trying to add an event listener to an input to search the API on input change. If you don't use debounce, API request will be sent every time the user press a key. With debounce function, you can delay the processing of the input event until the user has stopped typing for a certain amount of time.

```javascript
// accept a function as an argument, wrap it with debounce function and return it
const debounce = (func, delay) => {
	let timeoutId;
	// rest parameter syntax : accept indefinite number of arguments as an array
	return (...args) => {
		if (timeoutId) {
			clearTimeout(timeoutId);
		}
		timeoutId = setTimeout(() => {
			func.apply(null, args);
		}, delay);
	};
};

input.addEventListener('input', debounce(onInput, 1000));
// onInput would be a function that fetches data from an API using the value that is typed in the input
```

- `debounce` is a higher-order function that returns a function. It creates a closure so the returned function can access `timeoutId`.
