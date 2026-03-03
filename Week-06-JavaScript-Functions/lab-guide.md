## Week 6 – JavaScript Functions (Lab Guide)

### 1. What is a function?

A function is a reusable block of code. We use it to avoid repeating ourselves and to organise our programs.

Example (function declaration):

```js
function showMessage() {
  alert('Hello from Week 6!');
}

showMessage();
```

**Tasks**

1. Create a function `sayHello()` that alerts `"Hello from Week 6!"` and call it three times.
2. Change the message in one place (inside the function) and confirm all three calls show the new message.

---

### 2. Local and outer variables

A variable declared inside a function is only visible inside that function (local variable).

```js
function showMessage() {
  let message = 'Hello';
  alert(message);
}

showMessage();
// alert(message); // would cause an error
```

A function can also use variables declared outside it (outer variables):

```js
let userName = 'Ann';

function showUser() {
  alert('User: ' + userName);
}

showUser(); // "User: Ann"
```

If you create a local variable with the same name, it shadows the outer one:

```js
let userName = 'Ann';

function showUser() {
  let userName = 'Kate';
  alert('Inner: ' + userName);
}

showUser();        // "Inner: Kate"
alert(userName);   // "Ann"
```

**Tasks**

1. Reproduce the examples above in the browser console.
2. Explain (in comments) which `userName` is used in each alert.

---

### 3. Parameters and default values

We pass data into functions using parameters:

```js
function showMessage(from, text) {
  alert(from + ': ' + text);
}

showMessage('Ann', 'Hello!');
showMessage('Bob', 'Hi there');
```

If a parameter is missing, it is `undefined`. We can use default values:

```js
function showMessage(from, text = 'no text given') {
  alert(from + ': ' + text);
}

showMessage('Ann');                // "Ann: no text given"
showMessage('Ann', 'Hi there');    // "Ann: Hi there"
```

**Tasks**

1. Write a function `greet(name = 'Guest')` that alerts `"Hello, <name>!"`.
2. Call `greet('Ann')` and `greet()` and check the outputs.

---

### 4. Returning values

Functions can return a result:

```js
function sum(a, b) {
  return a + b;
}

let result = sum(3, 4); // 7
alert(result);
```

A `return` without a value simply exits the function. If a function has no `return`, it returns `undefined`.

```js
function doNothing() {}

alert(doNothing()); // undefined
```

**Tasks**

1. Write a function `multiply(a, b)` that returns the product of `a` and `b`.
2. Write a function `isAdult(age)` that returns `true` if `age >= 18`, otherwise `false`.

---

### 5. Function expressions and callbacks

Function declaration:

```js
function sayHi() {
  alert('Hi');
}
```

Function expression:

```js
let sayHi = function() {
  alert('Hi');
};
```

Callbacks – functions passed as arguments:

```js
function ask(question, yes, no) {
  if (confirm(question)) yes();
  else no();
}

ask(
  'Do you agree?',
  function() { alert('You agreed.'); },
  function() { alert('You canceled.'); }
);
```

**Tasks**

1. Rewrite `sayHi` as a function expression and call it.
2. Create an `askFavoriteColor` function that:
   - asks `"Do you like blue?"`
   - alerts `"Blue fan!"` if yes
   - alerts `"Not a blue fan."` if no

---

### 6. Declaration vs Expression and hoisting (read-only)

- Function declarations are available in their scope before they are written (hoisted).
- Function expressions are created only when execution reaches them.

You do not need to code anything here; just be aware of the difference.

