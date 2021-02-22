build-lists: true
footer: IDM 231: Scripting for IDM I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 231

## Scripting for IDM I

### Timers

---

# Objective

## Discuss Timers

---

## `setTimeout()`

```javascript
01 setTimeout(() => {
02   // run after 2 seconds
03 }, 2000);
```

^ When writing JavaScript code, you might want to delay the execution of a function. We'll explore how to schedule functions in the future.

^ With `setTimeout()`, you specify a callback function to execute later, and a value expressing how later you want it to run in milliseconds.

^ This syntax defines a new function. You can call whatever other functions you want in there, or you can pass an existing function name with parameters.

---

```javascript
01 const myFunction = (firstParam, secondParam) => {
02   // do something
03 }
04 
05 setTimeout(myFunction, 2000, firstParam, secondParam);
```

---

```javascript
01 const id = setTimeout(() => {
02   // run after 2 seconds
03 }, 2000)
04 
05 // I changed my mind
06 clearTimeout(id);
```

^ `setTimeout` returns the timer id. This is generally not used, but you can store this id and clear it if you want to delete the scheduled function execution.

---

### Zero Delay

```javascript
01 setTimeout(() => {
02   console.log('after');
03 }, 0)
04 
05 console.log('before');
06 
07 // before after
```

^ If you specify a timeout delay to 0, the callback will execute as soon as possible, but after the current function execution.

^ This is useful to avoid blocking the CPU on intensive tasks and letting other functions execute while performing heavy calculations.

---

## `setInterval()`

```javascript
01 setInterval(() => {
02   // runs every 2 seconds
03 }, 2000);
```

^ `setInterval` is a function similar to `setTimeout`, with a difference: instead of running the callback function once, it will run it forever, at the specific time interval you specify in milliseconds.

---

```javascript
01 const interval = setInterval(() => {
02   // runs every 2 seconds
03   if (App.somethingIWant === 'arrived') {
04     clearInterval(interval);
05     // run code
06     console.log('Your package has arrived');
07     return;
08   }
09   // otherwise do nothing
10 }, 2000);
```
