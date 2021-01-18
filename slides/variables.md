build-lists: true
footer: IDM 221: Web Authoring I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 221

## Web Design I

### Variables

---

# Objectives

- Discuss Declaring Variables
- Discuss Variable Types
- Discuss Expressions
- Introduce Arrays
- Introduce the Console

---

# Objective

## Discuss Declaring Variables

---

## Area of a Wall

$$
width * height = area
$$

1. Remember the value for width
1. Remember the value for height
1. Multiply width by height to get the area
1. Return the result to the user

^ Think about calculating the area of a wall; in math the area of a rectangle is obtained by multiplying two numbers: width times height.

^ You may be able to do calculations like this in your head, but when writing a script to do this calculation, you need to give the computer very detailed instructions. You might tell it to perform the following four steps in order: (_click through list_)

^ In this case, you would use variables to "remember" the values for width and height. This also illustrates how a script contains very explicit instructions about exactly what you want the computer to do. You can compare variables to short-term memory, because once you leave the page, the browser will forget any information it holds.

---

## Naming Rules: Variables

1. Must begin with a letter, dollar sign ($), or an underscore ( \_ )
1. Can not contain dashes or periods
1. Can not use _keywords_ or _reserved_ words
1. Are case sensitive
1. Should describe the info they will represent
1. Should use _camelCase_ or _under\_scores_ for multi word variables

---

## Declaring A Variable

```javascript
01 const one = 1;
02 
03 let two = 2;
04 two = 'two';
05 
06 var three = 'III'
```

^ A variable is a literal assigned to an identifier, so you can reference and use it later in the program. Variables do not have any type attached, so you can assign a variable to one type and then reassign it to another type without an error.

^ There are three ways to declare a variable, using one of the three keywords `const`, `let` or `var`. Those three differ in how you can interact with the variable later on.

---

### `var`

```javascript
01 var a = 0;
02 
03 var a = 1, b = 2;
04 
05 function hello() {
06   var c = 3;
07   console.log(a);
08   // the rest of the function
09 }
```

^ Originally `var` was the only construct available for defining variables. You can declare multiple variables at once in the same statement. The **scope** is the portion of the code where the variable is visible. A variable initialized with `var` outside of any function is assigned to the global object. Any variable defined inside a function is assigned only to that function.

---

### `let`

```javascript
01 let a = 0;
02 
03 function hello() {
04   let a = 'a';
05 }
```

^ `let` is a new feature introduced in ES2015. It is essentially a block scoped version of `var`. Modern JavaScript developers might use `let` only and completely disregard `var`.

---

### `const`

```javascript
01 const a = 'test'
```

^ Variables declared with `var` or `let` can be changed later in the program, and reassigned. Once a `const` is initialized, its value can never be changed, and it can't be reassigned to a different value.

^ Modern JavaScript developers might choose to always use `const` for variables that don't need to be reassigned later in the program.

---

# Objective

## Discuss Variable Types

---

## Types

- numbers
- strings
- booleans
- null
- undefined

---

### Numbers

Integers:

- 10
- 5354576
- 0xCC // hex

Floats:

- 3.14
- .1234
- 5.2e4 // 5.2 * 10^4

^ A numeric literal is a number represented in the source code. It can be an integer or a floating point number.

---

### Strings

```javascript
01 const sample = 'A string';
02 
03 const sample = "Another string";
04 
05 const whatIDo = 'I\'m a developer';
06 
07 const sample = 'A' + 'string';
```

^ A string type is a sequence of characters, enclosed in quotes or double quotes. A backslash is useful when you need to enter a quote inside a string enclosed in quotes. Strings can be joined using the `+` operator.

---

### Template Strings

```javascript
01 const sample = ` a string`;
02
03 const sample = `a string with ${something}`;
04
05 const sample = `a string with ${something + somethingElse}`
06 
07 const something = 'apple sauce';
08
09 const sample = `a string
   with
   ${something}`;
```

^ Template string literals allow a more powerful way to define strings, where you can perform substitution, and embedding the result of an expression, as well as having multiline strings easily.

---

### Booleans

```javascript
01 const openDoor = true;
02 
03 const openDoor = false;
```

^ There are two reserved words for booleans: `true` and `false`. There are many comparison operators that can be used to return one or the other. Later we'll see control structures using booleans to determine the flow of the program (if, while etc)

---

### `null`

```javascript
null
```

^ `null` is a special value that indicates the absence of a value.

---

### `undefined`

```javascript
// detect if a value is undefined
typeof variable === 'undefined';
```

^ `undefined` indicates that a variable has not been initialized and the value is absent.

---

## Object Types

```javascript
01 function hello() {}
02
03 const myObject = {};
04 
05 const myArray = [];
```

^ Anything that's not a primitive type is an object type.

---

# Objective

## Discuss Expressions

---

## Expressions

- arithmetic expressions
- string expressions
- primary expressions
- array & object initializers expressions

^ Expressions are units of code that can be evaluated and resolve to a value.

---

### Arithmetic Expressions

1 / 2

i++

i -= 2

i * 2

^ All expressions that evaluate to a number.

---

### Arithmetic Operators

| Name | Operator | Purpose |
| ---- | -------- | ------- |
| addition | + | Adds values |
| subtraction | - | subtracts values |
| division | / | divides two values |
| multiplication | * | multiples values |
| exponent | ** | first to the power of second operand |
| increment | ++ | adds one to the current number |
| decrement | -- | subtracts one from the current number |
| modulus | % | divides two numbers & returns remainder |

^ JavaScript contains the following mathematical operators, which you can use with numbers. You may remember some from math class.

---

#### Order of Operations

$$
2 + 4 + 10
$$

$$
2 + 4 * 10
$$

^ The calculation from left to right: total = 2 + 4 + 10 = 16.

^ But in the second example, the total is 42, not 60 because multiplication and division happen before addition and subtraction.

---

#### Use Parenthesis

$$ (2 + 4) * 10 $$

^ To change the order in which operations are performed, place the calculation you want done first in parentheses.

---

> Please Excuse My Dear Aunt Sally

^ Parentheses, Exponents, Multiplication, Division, Addition, Subtraction

^ Don't forget LEFT to RIGHT i.e. 4 - 2 + 1 = 3 NOT 1

---

### String Expressions

'A' + 'string'

'A' +== 'string'

^ Any expression that evaluates to a string.

---

[.build-lists: false]

### Primary Expressions

- true
- undefined
- function
- class

^ Variable references, literals and constants, and language keywords.

---

### Array & Object Initializers Expressions

- [ ] // array literal
- { } // object literal
- [1,2,3]
- {a : 1, b: 2}

---

### Logical Expressions

```javascript
a && b
a || b
!a
```

^ Logical expressions make us of logical operators and resolve to a boolean value.

---

# Objective

## Introduce Arrays

---

## Arrays

### Initialize an Array

```javascript
01 const a = [];
02 const a = [1,2,3];
03 const Array.of(1,2,4);
04 const Array(6).fill(1) // init an array of 6 items with value 1
05
06 // old syntax (don't use)
07 const a = new Array();
08 const a = new Array(1,2,3);
```

---

### Get Length of an Array

```javascript
01 const a = [1,2,3];
02
03 const myArrayLength = a.length;
```

---

### Values in an Array

```javascript
01 const colors = ['white', 'black', 'custom'];
02 //               0        1        2
03
04 console.log(colors[0]); // white
05 console.log(colors[1]); // black
06 console.log(colors[2]); // custom
```

^ Values in an array are accessed as if they are in a numbered list. It is important to know that the numbering of this list starts at zero (not one).

^ Each item in an array is automatically given a number called an index. This can be used to access specific items in the array. Consider the following array which holds three colors:

^ Confusingly, index values start at 0 (not 1), so the following table shows items from the array and their corresponding index values:

---

### Changing Array Values

```javascript
01 const colors = ['white', 'black', 'custom'];
02
03 colors[3] = 'beige';
04
05 console.log(colors[3]); // beige
```

^ To access a value from an array, after the array name you specify the index number for that value inside square brackets. You can change the value of an item an array by selecting it and assigning it a new value just as you would any other variable (using the equals sign and the new value for that item).

---

### Adding to an Array

```javascript
01 // add at the end
02 myArray.push(4);
03
04 // add at the beginning
05 myArray.unshift(0);
06
07 // Using ES6
08 let arrayOne = ['1','2','3'];
09 let arrayTwo = [...arrayOne, '4'];
```

---

### Remove an Item From an Array

```javascript
01 // from the end
02 myArray.pop();
03
04 // from the beginning
05 a.shift();
06
07 // at a specific position
08 myArray.splice(0, 2); // get the first 2 items
09 myArray.splice(3, 2); // get the 2 items starting from index 3
```

---

### Join Multiple Arrays

```javascript
01 const a = [1,2];
02 const b = [3,4];
03 a.concat(b); // 1,2,3,4
04 // OR
05 const c = [...a, ...b]; // 1,2,3,4
```

---

### Lookup the Array for an Element

```javascript
01 myArray.indexOf(); // first matching item or -1
02 myArray.lastIndexOf(); // last matching item or -1
03
04 myArray.find((element, index, array) => {
05   // return true or false
06 });
07
08 myArray.includes(value); // returns true or false
```

---

### Sort an Array

```javascript
01 const a = [1,2,3,10,11];
02 a.sort();   // 1,10,11,2,3
03 a.reverse(); // 3,2,11,10,1
```

---

### Copy an Existing Array

```javascript
01 const a = [1, 2, 3];
02 //
03 const b = Array.from(a);
04 // ES6
05 const b = [...a];
```

---

# Objective

## Introduce the Console

---

## Console

```javascript
01 console.log('hello world');
02 
03 console.log(myVariable);
04 
05 console.log('myVariable: ' + myVariable);
```

^ Browsers that have a console have a console object, which has several methods that your script can use to display data in the console. The `console.log()` method can write data from a script to the console. Such notes can tell you how far a script has run and what values it has received. Console messages are logged to the console window inside of the browsers Devtools.
