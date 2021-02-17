# Rounding Numbers

> Don't use `toFixed()` just for rounding a number! (inefficient!)

You can use `Math.round()` if you are rounding the number to an integer.

```javascript
Math.round(12.3456789); // 12
```

You might think you can use `toFixed()` to round the number to certain decimal digits.

```javascript
(12.3456789).toFixed(2); // "12.35"
```

But notice that `toFixed()` returns a **string**, not a number.

To solve this problem you have to convert it back to a number.

```javascript
parseFloat((12.3456789).toFixed(2));
// or
+(12.3456789).toFixed(2);
```

However, this is not an efficient way since it will convert the number to a string and parse it back to a number. It is slow and theoretically incorrect.

So, better solution is:

```javascript
// Multiply & Divide
Math.round(12.3456789 * 1e2) / 1e2;
// if you want to round it to n digits, 1en instead of 1e2
```

- `e` in numbers : floating-point number representation
  - `1e2 = 1 * 100 = 100`
  - `2.5e5 = 2.5 * 100000 = 250000`
  - `5e-3 = 5 * 0.001 = 0.005`
