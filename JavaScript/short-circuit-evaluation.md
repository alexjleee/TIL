# Short-Circuit Evaluation

## AND(&&) Short-Circuit

If the left operand is falsy, it will short-circuit and the right operand won't be evaluated.

- It can be used to prevent execution of subsequent code in case the left operand is falsy.

```javascript
!response.ok && console.log('There was an error');
// log the message only when the response.ok is false
```

## OR(||) Short-Circuit

If the left operand is truthy, it will short-circuit and the right operand won't be evaluated.

- It can be used to return the first truthy value in the expression.
- It can be used to set a default value.

```javascript
const displayMenu = restaurant.menu || 'Unavailable';
console.log(displayMenu);
// if restaurant.menu exists and is not falsey, return that value. If not, return Unavaulable
```

- It can be used to set a default value for a parameter, but since ES6 you can use default parameters

```javascript
// with OR(||) operator
function makeElement(tag, content) {
	tag = tag || 'div';
	content = content || '';
	const startTag = `'<${tag}>'`;
	const endTag = `'</${tag}>'`;
	return startTag + content + endTag;
}
// with default parameters
function makeElement(tag = 'div', content = '') {
	const startTag = `'<${tag}>'`;
	const endTag = `'</${tag}>'`;
	return startTag + content + endTag;
}
```

## Nullish Coalescing Operator (??)

If the left operand is `null` or `undefined`, the expression won't be evaluated.

```javascript
// fetch restaurant data
const displayRating = restaurant.rating || 'Unavailable';
console.log(displayRating);
// there is a problem when the restaurant.rating is 0 - 0 is a falsy value so it will return Unavailable
```

```javascript
// fetch restaurant data
const displayRating = restaurant.rating ?? 'Unavailable';
console.log(displayRating);
// even when the restaurant.rating is 0, 0 is not null nor undefined so it wil return 0
```
