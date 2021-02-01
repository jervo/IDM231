build-lists: true
footer: IDM 231: Scripting for IDM I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 231

## Scripting for IDM I

### Loops

^ Loops check a condition. If it returns **true**, a code block will run. Then the condition will be checked again and if it still returns **true**, the code block will run again. It repeats until the condition returns **false**.

---

# Objectives

- Introduce the Loop Concept
- Review Types of Loops

---

# Objective

## Introduce the Loop Concept

---

![loop start](http://digm.drexel.edu/crs/IDM231/cdn/instructor_materials/images/05-loop_start.png)

^ The first time the loop is run, the variable `i` (the counter) is assigned a value of zero.

^ Every time the loop is run, the condition is checked. Is the variable `i` less than 10?

^ Then the code inside the loop (the statement between the curly braces) is run.

---

![loop end](http://digm.drexel.edu/crs/IDM231/cdn/instructor_materials/images/05-loop_end.png)

^ The variable `i` can be used inside the loop. Here it is used to write a number to the console.

^ When the statements have been finished, the variable `i` is incremented by 1.

^ When the condition is no longer **true**, the loop ends. The script moves on to the next line of code.

---

# Objective

## Review Types of Loops

---

## For Loop

```javascript
01 for (let i = 0; i < 10; i++) {
02   console.log(i);
03 }
```

^ There are different types of loops. If you need to run code a specific number of times, use a `for` loop. In a `for` loop, the condition is usually a counter which is used to tell how many times the loop should run.

---

### Loop Counters

```javascript, [.highlight: 1, 5-7]
01 for (let i = 0; i < 10; i++) {
02   console.log(i);
03 }

let i = 0;
i < 10;
i++
```

^ A `for` loop uses a counter as a condition. This instructs the code to run a specific number of times. Here you can see the condition is made of up three statements.

^ **Initialization**: create a variable and set it to 0. This variable is commonly called `i`, and acts as a counter.

^ **Condition**: the loop should continue to run until the counter reaches a certain number.

^ **Update**: every time the loop has run the statements in the curly braces, it adds one to the counter.

---

### While Loop

```javascript
01 const cars = ['BMW', 'Volvo', 'Saab', 'Ford'];
02 let i = 0;
03 
04 while (cars[i]) {
05   console.log(cars[i]);
06   i++;
07 }
```

^ If you do not know how many times the code should run, you can use a `while` loop. Here the condition can be something other than a counter and the code will continue to loop for as long as the condition is **true**.

---

### `forEach` Loop

```javascript
01 const cars = ['BMW', 'Volvo', 'Saab', 'Ford'];
02 
03 cars.forEach(function(car) {
04   console.log('car: ', car);
05 });
```

^ Another style of loop that is common, especially when you don't necessarily know the total number of items being looped over is the `forEach` loop. Then `forEach()` method executes a provided function once for each array element.

---

#### forEach Loop With Arrow Function Syntax

```javascript
01 const cars = ['BMW', 'Volvo', 'Saab', 'Ford'];
02 
03 cars.forEach(car => {
04   console.log('car: ', car);
05 });
```

---

### `for...of` Statement

```javascript
01 let numbers = [10, 20, 30];
02 
03 for (let value of numbers) {
04   console.log(value)
05 }
```

^ The `for...of` statement creates a loop iterating over iterable objects (strings, arrays, node lists etc).

---

### `for...in` Statement

```javascript
01 const myObject = {a: 1, b: 2, c: 3 };
02 
03 for (const property in myObject) {
04   console.log(`myObject.${property}: ${myObject[property]}`);
05 }
```

^ The `for...in` statement loops over the properties of an object. This syntax is not recommended for use with arrays. Its most practical use is for debugging purposes, being an easy way to check the properties of an object.

---

### `map`

```javascript
01 const numbers = [4, 9, 16, 25];
02 const sqrt = numbers.map(number => number*number);
```

---

## So Many Options

- `while`
- `do-while`
- `for`
- `forEach()`
- `for...in`
- `for...of`
- `map()`

^ With so many options, it may seem overwhelming and difficult to choose which type of loop is best. The answer will differ based on the situation. Use whatever syntax best suits your needs, and keep things as simple as possible.

^ _examples/decisions/loops.html_
