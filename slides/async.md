build-lists: true
footer: IDM 231: Scripting for IDM I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 231

## Scripting for IDM I

### Asynchronous Functions

---

# Objective

## Asynchronicity in Programming

^ Computers are asynchronous by design. Asynchronous means that things can happen independently of the main program flow.

^ In the current consumer computers, every program runs for a specific time slot, and then it stops its execution to let another program continue its execution. This thing runs in a cycle so fast that's impossible to notice, and we think our computers run many programs simultaneously, but this is an illusion (except on multiprocessor machines).

^ Normally, programming languages are synchronous, with ways of working with asynchronicity. JavaScript is synchronouse by default, meaning lines of code are executed in a series, one after another.

^ But JavaScript's main job, at least in the beginning, was to respond to user actions like `onClick`, `onMouseHover` etc. the browser provides a way for the synchronous programming model to handle this kind of functionality.

---

## Callbacks

```javascript
01 const myButton = document.getElementById('button');
02 
03 myButton.addEventListener('click', () => {
04   // button clicked
05 });
```

^ You can't know when a user is going to click a  button, so you define an event handler for the click event. This event handler accepts a function which can be called when the event is triggered.

^ This is the **callback**. A callback is a simple function that is passed as a value to another function and will only be executed when the event happens.

---

### `window.load`

```javascript
01 window.addEventListener('load', () => {
02   // window loaded
03   // do what you want
04 });
```

^ It's common to wrap all your client code in a `load` event listener on the `window` object, which runs the callback function only when the page is ready.

---

### The Problem With Callbacks

```javascript
01 window.addEventListener('load', () => {
02   document.getElementById('button').addEventListener('click', () => {
03     setTimeout(() => {
04       items.forEach(item => {
05         //your code here
06       })
07     }, 2000);
08   });
09 })
```

^ Callbacks are great for simple cases, but every callback adds a level of nesting and if you have a lot of callbacks, the code starts to be complicated very quickly.

---

### Alternatives to Callbacks

- Promises
- Async/Await

---

## Promises

- resolved
- rejected

^ A promise is defined as a proxy for a value that will eventually become defined. Once a promise has been called, it will start in a _pending state_. This means the caller function continues the execution, while it waits for the promise to do its own processing, and give the caller function some feedback.

^ The caller function waits for it to either return the promise in a _resolved_ state or a _rejected_ state.

---

### Creating a Promise

```javascript
01 let done = true;
02 
03 const isItDoneYet = new Promise(
04   (resolve, reject) => {
05     if (done) {
06       const workDone = 'Here is the thing I built';
07       resolve(workDone);
08     } else {
09       const why = 'Still working on something else';
10       reject(why);
11     }
12   }
13 )
```

^ The Promise API exposes a Promise constructor, which you initialize using `new Promise()`. The promise checks the global constant and if it's true, we return a resolved promise, otherwise a rejected promise. We communicate back a value, in this case a string but it could be anything we want.

---

### Consuming a Promise

```javascript
01 const isItDoneYet = new Promise(
02   //...
03 );
04 
05 const checkIfItsDone = () => {
06   isItDoneYet.then((ok) => {
07     console.log(ok)
08   })
09   .catch((err) => {
10     console.error(err)
11   })
12 };
```

^ Running `checkIfItsDone()` will execute `isItDoneYet()` promise and wait for it to resolve, using the `then` callback and if there's an error it will handle it in the `catch` callback.

---

> Async & Await

^ Async functions are a combination of promises and generators, basically a higher level abstraction over promises.

---

## How it Works

```javascript
01 const doSomethingAsync = () => {
02   return new Promise((resolve) => {
03     setTimeout(() => resolve('I did something'), 3000)
04   })
05 }
06 
07 const doSomething = async () => {
08   console.log(await doSomethingAsync())
09 }
```

^ When you want to call this function, you prepend `await`, and the calling code will stop until the promise is resolved or rejected.

^ _examples/async\_await/basics.js_

^ _examples/async\_await/README.md_
