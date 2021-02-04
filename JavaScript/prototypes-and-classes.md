# Prototypes & Classes

JS is a functional prototype-based programming language. The `class` keyword introduced in ES6 is a syntactical sugar over prototype-based inheritance providing simpler way to create objects and deal with inheritance.

## Object Prototypes

All JS objects can have a **prototype object**, from which they _inherit_ methods and properties.

- `.prototype` : actual prototype object where methods and properties are added to
- `__proto__` : reference to the prototype object
  Prototype object has a `constructor` property that refers to the constructor function that created the instance object.

## Constructor Function & 'New' Keyword

- Constructor functions are the functions that are used as a template for creating objects.
- `new` operator creates an instance of an object type that has a constructor function.
- Example :

```javascript
function Hero(name, level) {
	this.name = name;
	this.level = level;
	// 'this' inside the constructor function refers to the instance (object)
}
Hero.prototype.info = function () {
	const { name, level } = this;
	return `${name}, level ${level}`;
};

const hero1 = new Hero('Athena', 8);
const hero2 = new Hero('Ares', 7);

hero1;
// Hero {name: "Athena", level: 8}
  // __proto__: Object
    // info: f()
    // constructor: f Hero(name, level)
    // __proto__: Object

hero1.info(); // Athena, level 8
hero1.info === hero2.info; // true
```

## JS Classes & Inheritance

- `class` : create a new class using prototype-based inheritance
- `extends` : create a child of another class(parent class)
- `super` : used to call the constructor of the parent class
- Example :

```javascript
class Hero {
	constructor(name, level) {
		this.name = name;
		this.level = level;
	}
	info() {
		const {name, level} = this;
		return `${name}, level ${level}`;
	}
}

class Warrior extends Hero {
	constructor(name, level, weapon) {
		// access the parent's properties with 'super' keyword
		super(name, level);
		// add its own property
		this.weapon = weapon;
	}
	// this info() method will overwrite the info() method of the parent class
	info() {
		const {name, level} = this;
		return `${name}, a warrior, level ${level}`;
	}
	// add its own method
	attack() {
		const { name, level, weapon } = this;
		return `${name} attacks with ${weapon.name} : damage ${level * weapon.atk}`;
	}
}

const hero1 = new Warrior('Athena', 8, { name: 'Golden Spear', atk: 100 });

hero1;
// Warrior {name: "Athena", level: 8, weapon: {...}}
	// __proto__: Hero
		// attack: f attack()
		// constructor: class Warrior
		// info: f info()
    // __proto__: Object

hero1.info(); // Athena, a warrior, level 8
hero1.attack(); // Athena attacks with Golden Spear : damage 800
```
