# Storing Data Inside DOM Element

## Custom `data-` Attributes

`data-` attributes allow you to store data on the HTML elements.

```html
<article id="rating" data-tomato-rating="96">
	<h5>Rotten Tomatoes</h5>
	<h6>Tomatometer</h6>
	<p>96% - 518 Reviews</p>
	<h6>Audience Score</h6>
	<p>79% - 50,000+ Ratings</p>
</article>
```

- Naming Rule : No uppercase, only lowercase and hyphen(-)

- The value stored in a `data-` attribute is always a _string_

And you can read/write the values of the attributes in JS.

```javascript
const rating = document.querySelector('#rating');

// getAttribute & setAttribute
console.log(rating.getAttribute('data-tomato-rating')); // "96"
rating.setAttribute('data-tomato-rating', '97');

// OR

// dataset
const ratingVal = parseInt(rating.dataset.tomatoRating);
console.log (100 - ratingVal);
// since the data stored inside the data attribute is a string,
// you need to parse it into a number to do calculation
```

- For `dataset`, type only the name without `data-` and it should be _camelCased_

Like any other HTML attributes, you can use access `data-` attributes from CSS
```css
article[data-value-name='some value'] {
  color: red;
}
```

DO NOT
  - use it to store sensitive information
  - use it to store data that should be visible and accessible
  - store too much data
