# Closure

Closures are created when a function is created and it gives access to an outer function's scope from an inner function (even after the outer function has already returned).

```javascript
function outer() {
  const msg = 'Hello';
  return function inner() {
    console.log(msg);
  }
}
inner = outer();
inner(); // Hello
```

## Use Case 1 - Access Variables Outside Callback
```javascript
body = document.body;
function makeBtns(num) {
  for (let i = 1; i <= num; i++) {
    const btn = document.createElement('button');
    btn.innerHTML = `Button ${i}`;
    btn.addEventListener('click', function() {
      alert(`You just clicked button ${i} out of ${num} buttons`);
    });
    body.appendChild(btn);
  }
}
makeBtns(5);
// callback inside the event listener can access variable 'i' and argument 'num' even after the outer function has already been executed
```

## Use Case 2 - Data Privacy

```javascript
function account(initBalance) {
  let balance = initBalance;
  return {
    getBalance: function() {
      return balance;
    },
    deposit: function(amount) {
      balance += amount;
      return balance;
    },
    withdraw: function(amount) {
      balance -= amount;
      return balance;
    }
  }
}

const myAcoount = account(1000);

myAcoount.deposit(100);
myAcoount.withdraw(40);
myAcoount.getBalance(); // 1060
balance; // ReferenceError
// the variable 'balance' cannot be directly accessed from the outside
```

## Use Case 3 - Function Composition

```javascript
function makeHtmlStr(tag) {
  const startTag = `'<${tag}>'`;
  const endTag = `'</${tag}>'`;
  return function(content) {
    return startTag + content + endTag;
  }
}
// make functions using 'makeHtmlStr' function
const makeH1Str = makeHtmlStr('h1');
makeH1Str('This is a H1 header');

const makePStr = makeHtmlStr('p');
makePStr('This is a paragraph');
```
