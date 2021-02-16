# SVG Animation

> You can animate SVG easily by manipulating the attributes dynamically through JS.

## Useful SVG Attributes for Animation

### `stroke-dasharray` and `stroke-dashoffset`

- `stroke-dasharray` : define the pattern of dashes and gaps in a stroke
  - For example, `stroke-dasharray: 40 20` will create a stroke with 40px-long dashes with 20px gaps
- `stroke-dashoffset` : offset the beginning of the dash array

### `offset-path` and `offset-distance`

- `offset-path` : specify the offset path where the element gets positioned
- `offset-distance` : specify a position along an offset-path

Example : [Circular Timer Animation](https://codepen.io/alexjleee/pen/wvodoMV)
