# Getter & Setter

Getters and setters are used to get/set accessor properties.

- Accessor Properties : essentially functions that execute on getting/setting a value but look like regular properties to an external code.
- `get` : a function without arguments, called when a property is read
- `set` : a function with one argument, called when a property is set
- To avoid exceeding max call stack size, avoid using the same name for accessor property as for data property.

- Examples :

```javascript
// validate data before store it
const user = {
	get name() {
		return this._name;
	},
	set name(value) {
		const regex = /^[a-zA-Z ]{2,30}$/;
		if (regex.test(value)) {
      this._name = value;
    } else {
      console.log('Error: Unvalid name');
    }
	}
};
user.name = '@lex'; // Error unvalid name
```
```javascript
// expose a value as read-only
const obj = {
  _readOnlyData: 'this data is read only'
  get readOnlyData() {
    return this._readOnlyData;
  }
}
console.log(obj.readOnlyData); // this data is read only
obj.readOnlyData = 'overwrite'; // <- this won't change the property
console.log(obj.readOnlyData); // this data is read only
```
```javascript
// computed values that are dependent on other data (but not computationally expensive)
class Rectangle {
  constructor(left, right, top, bottom) {
    this.left = left;
    this.right = right;
    this.top = top;
    this.bottom = bottom;
  }
  get area() {
    return (this.right - this.left) * (this.bottom - this.left);
  }
}
const rect1 = new Rectanle(10,20,20,40);
console.log(rect1.area); // 200
```
