# JS Data Structures

> How to decide which data structure to use

## 1. Simple List vs. Key-Value Pairs

Need key-value pairs => `Object`, `Map`

Need just a simple list => `Array`, `Set`

## 2. Array vs. Set

`Array`
- when you need an ordered(indexed) list
- when you need a list containing duplicates
- when you need to manipulate the values in a list

`Set`
- when you need a list without duplicates
- when you need to search/add/delete the values fast

## 3. Object vs. Maps

`Object`
- when you need to work with JSON
- when you need to include methods

`Map`
- when you need to use data types other than `String` (or `Symbol`) for keys
- when you need to iterate (according to the insertion order) or compute the size
- when you need to do a lot of adding/removing pairs
- when you need to store a large set of data