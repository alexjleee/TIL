# Unit Testing With Mocha & Chai

> [**Mocha**](https://mochajs.org/) is a JS test framework running both on Node.js and in the browser.

> [**Chai**](https://www.chaijs.com/) is a [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development)/[TDD](https://en.wikipedia.org/wiki/Test-driven_development) _assertion_ library for both Node.js and the browser.

## Set Up For In-Browser Testing

```html
<!-- index.html -->

<!DOCTYPE html>
<html>
  <head>
    <!-- Add Mocha CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/mocha/8.3.2/mocha.css">
    <!-- Add Mocha -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mocha/8.3.2/mocha.js"></script>
    <script>
      // Activates the BDD API 
      // (make 'describe', 'it', 'before', 'beforeEach', 'after' and 'afterEach' global)
      mocha.setup('bdd');
    </script>
    <!-- Add Chai -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/chai/4.3.4/chai.js"></script>
    <script>
      // Make 'assert' global
      let assert = chai.assert;
    </script>
  </head>

  <body>

    <!-- Script to test-->
    <script src="../index.js"></script>

    <!-- Test script to run -->
    <script src="test.js"></script>

    <!-- Container for test results -->
    <div id="mocha"></div>

    <!-- Run tests -->
    <script>
      mocha.run();
    </script>
  </body>
</html>
```

## Set Up For Server-Side Testing

1. Create a directory called `test` and create a test script file inside

    ```
    app.js
    /test
      appTest.js
    ```

2. Install Mocha & Chai

    `$ npm i mocha chai ---save-dev`

3. Configure `package.json`

    ```json
    {
      "scripts": {
        "test": "mocha"
      }
    }
    ```

4. Set up test script

    ```javascript
    // test/appTest.js

    const assert = require('chai').assert;
    const app = require('../app');

    // Grouping tests
    describe('Name of the testing group', function() {
      // Individual test case
      it('Test description', function() {
        // Test goes here
      })
    });
    ```

5. Run the test

    `$ npm test`

