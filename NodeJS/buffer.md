# Buffer

## What Is Buffer

**Buffer** is an area of memory where data is stored temporarily. It is designed to handle raw _binary_ data. 

## How To Access The Content Of A Buffer

Since a buffer is an array of bytes, you need to parse it in order to access the original content.

```javascript
const buf = Buffer.from('Hello');
console.log(buf);
// <Buffer 48 65 6c 6c 6f>
console.log(buf.toString());
// Hello
```

## Use Case
```javascript
// bodyParser function
const bodyParser = (req, res, next) => {
	if (req.method === 'POST') {
		req.on('data', (data) => {
			// data is a buffer -> needs to be parsed
			const parsed = data.toString('utf8').split('&');
			const formData = {};
			for (let pair of parsed) {
				const [key, value] = pair.split('=');
				formData[key] = value;
			}
        req.body = formData;
        next();
		});
	} else {
    next();
  }
};
```