build-lists: true
footer: IDM 231: Scripting for IDM I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 231

## Scripting for IDM I

### Functions

---

# Objectives

- Introduce Functions
- Discuss Variable Scope

---

# Objective

## Introduce Functions

---

> Functions

^ Browsers require very detailed instructions about what we want them to do. Therefore, complex scripts can run to hundreds (even thousands) of lines. Programmers use functions, methods, and objects to organize their code.

^ _Functions_ consist of a series of statements that have been grouped together because they perform a specific task. A _method_ is the same as a function, except methods are created inside an object.

---

## Function Example

```javascript
01 function updateMessage(msg) {
02   const el = document.getElementById('message');
03   el.textContent = msg;
04 }
05 
06 updateMessage('Hello World');
```

^ Functions let you group a series of statements together to perform a specific task. If different parts of a script repeat the same task, you can reuse the function rather than repeating the same set of statements.

^ When you group tasks together into a function, you need to give your function a name, which should describe the task it is performing. When you ask it to perform the task it's known as **calling** the function.

---

[.code-highlight: 2-3]

## Function Structure

```javascript
01 function updateMessage(msg) {
02   const el = document.getElementById('message');
03   el.textContent = msg;
04 }
05 
06 updateMessage('Hello World');
```

^ The steps the function needs to perform in are packaged up in a code block. A code block consists of one ore more statements contained within curly braces.

---

## Function Parameters

```javascript
01 function updateMessage(name, message) {
02  console.log('Hello ' + name + ', ' + message);
03  // or with ES6
04  console.log(`Hello ${name}, ${message}`);
05 }
06
07 updateMessage('Phil', 'How are you today?');
```

^ Some functions need to be provided with information in order to achieve a given task. Pieces of information passed to a function are known as **parameters**.

---

## Working With Parameters

```javascript
01 function getArea(width, height) {
02  return width * height;
03 }
04
05 let totalArea = getArea(3, 5);
06
07 const wallWidth = 3;
08 const wallHeight = 5;
10 
11 let totalArea = getArea(wallWidth, wall_height);
```

^ Inside the function, the parameters act like variables.

---

## Function Return

```javascript
01 function updateMessage(name, message) {
02  const newMessage = `Hello ${name}, ${message}`;
03  return newMessage;
04 }
05
06 let myMessage = updateMessage('Phil', 'Welcome to my script!');
07
08 console.log(myMessage); // Hello Phil, Welcome to my script!
```

^ When you write a function and you expect it to provide you with an answer, the response is known as a **return value**. Using the `return` keyword, the specified value is returned from inside the function, back to the placeholder that originally called the function. When a return statement is encountered, the execution of the function immediately stops and the current value of the returned variable is extracted. If the function contains more lines of code, they are not executed.

---

## Anatomy of a Function

```javascript
01 function sayHello() {
02   console.log('Hello!');
03 }
```

^ Let's review. You declare a function using the **function** keyword.

^ You give the function a **name** (sometimes called an **identifier**) followed by parentheses.

^ The **statements** that perform the task sit in a code block, inside the curly braces.

---

## Calling a Function

```javascript
01 function sayHello() {
02   console.log('Hello!');
03 }
04 
05 sayHello();
```

^ Once you declare a function, you can execute all the statements between the curly braces with a single line of code. This is know as **calling the function**. This is done by using the function name followed by parentheses. You can call the same function as many times as you want within the same Javascript file.

---

## Getting Values Out of a Function

```javascript
01 function getArea(width, height) {
02   const area = width * height;
03   return area;
04 }
05 
06 let wall = getArea(3, 5); // 15
07 let wall = getArea(8, 5); // 40
```

^ Some functions return information to the code that called them. _wall1_ will be equal to 15, while _wall2_ will hold the value 40. This also demonstrates how the same function can be used to perform the same steps with different values.

---

## Getting Multiple Values Out of a Function

```javascript
01 function getSize(width, height, depth) {
02   const area = width * height;
03   const volume = width * height * depth;
04 
05   // Does this work?
06   // Why or why not?
07   return area;
08   return volume;
09 }
10 
11 let sizes = getSize(3,2,3);
```

^ Someone tell me, how could we get more than one value out of a function?

---

## Return Arrays

[.code-highlight: 5,6,9,10]

```javascript
01 function getSize(width, height, depth) {
02   const area = width * height;
03   const volume = width * height * depth;
04
05   const sizes = [area, volume];
06   return sizes;
07 }
08 
09 let area = getSize(3,2,3)[0];
10 let volume = getSize(3,2,3)[1];
```

^ Functions can return more than one value using an array.

---

## Arrow Functions

[.code-highlight: 1,5]

```javascript
01 const myFunction = function() {
02   // ...
03 }
04 
05 const myFunction = () => {
06   // ...
07 }
```

^ ES6 introduced a new syntax for the anatomy of a function, the _arrow function_. Visually, the arrow function simplifies the syntax, making it shorter, which is a welcome change.

---

### Arrow Functions - Single Statement

```javascript
01 const myFunction = function() {
02   doSomething();
03 }
04 
05 // Becomes
06 
07 const myFunction = () => doSomething();
```

^ If the function of the body contains a single statement, you can omit the brackets and write it all on a single line.

---

### Arrow Function - Parameters

```javascript
01 const myFunction = function(param1, param2) {
02   doSomething(param1, param2);
03 };
04 
05 // Becomes
06 
07 const myFunction = (param1, param2) => doSomthing(param1, param2);
```

^ Parameters are passing in the parentheses.

---

### Arrow Functions - Single Parameter

```javascript
01 const myFunction = param => doSomething(param);
```

^ If you have one (and only one) parameter, you can omit the parentheses completely.

^ Because of the short syntax, arrow functions encourage the use of small functions, which is one of our goals when writing clean, concise scripts.

---

# Objective

## Discuss Variable Scope

---

## Variable Scope

### Local vs Global vs Block

^ The location where you declare a variable will affect where it can be used within your code. If you declare it within a function, it can only be used within that function This is known as the variable's **scope**.

---

### Local Scope

```javascript
01 function getArea(width, height) {
02   const area = width * height;
03   return area;
04 }
05 
06 console.log(area); // ⚠️ ERROR
```

^ When a variable is created inside a function using the var keyword, it can only be used in that function. It is called a local variable or function-level variable. It is said to have local scope or function-level scope. It cannot be accessed outside of the function in which it was declared.

^ In this example, `area` is a local variable, only available within the `getArea` function.

^ `area` is only available within the `getArea()` function. Trying to access it outside of that function will produce an error.

---

### Global Scope

```javascript
01 function getArea(width, height) {
02   const area = width * height;
03   return area;
04 }
05 
06 let wallSize = getArea(3,2);
07 console.log(wallSize); // 6
08 
09 wallSize = 'dog';
10 console.log(wallSize); // dog
```

^ If you create a variable outside of a function, then it can be used anywhere within the script. It is called a **global** variable and has **global scope**.

^ Global variables are stored in memory for as long as the web page is loaded in the browser, which means they take up more memory than local variables.

---

### `var` Does Not Have Block Scope

```javascript
01 var x = 1;
02 
03 function myFunction() {
04   x = 2;
05 }
06 
07 console.log(x); // 2
```

^ Variables declared with the `var` keyword do not have block scope, which means if a variable is introduced within a code block, those variables are scoped to the containing function, and the effects of setting them persist beyond the block itself.

---

### `let` & `const` Do Have Block Scope

```javascript
01 let x = 1;
02 
03 function myFunction() {
04   let x = 2;
05   console.log(x); // 2
06 }
07 
08 console.log(x); // 1
```

^ By contrast, variables declared with `let` and `const` do have block scope. The `x = 2` is limited in scope to the block in which it was defined. (This example is using `let`, but the rules are the same for `const`)

^ _examples/functions/scope.js_
