# Encapsulation

> Encapsulation is a process of binding the data with the methods that operate on the data (usually in a class).

Why do you need encapsulation & data privacy?
- To prevent code from outside of a class to accidentally manipulate the data inside the class. 
- To change internal methods without worrying about breaking the external code.

## Encapsulation in JS

1. Follow convention and signal the other developer (and yourself) that the properties shouldn't be overwritten from the outside.
```javascript
class User {
	constructor(fName, lName, age) {
		this.fName = fName;
		this.lName = lName;
		this._age = age;
	}
	get age() {
		return this._age;
	}
	set age(val) {
		if (val <= 0) {
			throw Error('must be grater than 0');
		}
		this._age = val;
	}
}
```
2. Use ordinary variables in the constructor and capture them in closures.
```javascript
class User {
	constructor(fName, lName, age) {
		this.fName = fName;
		this.lName = lName;
		let _age = age;
		this.getAge = function() {
			return _age;
		}
	}
}
```
3. Private class fields (stage 3)
- Browser support is limited but you can use Babel.
```javascript
class PrivateMessage {
  #msg
  constructor() {
    this.#msg = 'this is a private field';
  }
  #privateMethod() {
    return 'this is a private method';
  }
  getPrivateMessage() {
    return `${this.#msg} and ${this.#privateMethod()}`;
  }
}
// #msg and #privateMEthod() cannot be accessed from the outside
```