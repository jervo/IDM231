build-lists: true
footer: IDM 231: Scripting for IDM I
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 231

## Scripting for IDM I

### Working With JSON

---

# Objectives

- Introduce JSON Format
- Discuss Working With JSON

---

# Objective

## Introduce JSON Format

^ JavaScript Object Notation (pronounced jason), is one of several data formats for transferring and storing data.

---

### Object

```javascript
01 {
02   first: 'Grace',
03   last: 'Hopper'
04 }
```

---

### CSV

```
first,last
Grace,Hopper
```

---

## XML

```xml
01 <person>
02   <first>Grace</first>
03   <last>Hopper</last>
04 </person>
```

---

### JSON Data

```json
01 {
02   "first": "Grace",
03   "last": "Hopper"
04 }
```

---

## What JSON Is

- Read and understood well by humans & computers
- More flexible than CSV
- Less verbose than XML
- Easy to work with in JavaScript

^ Of those examples, JSON is preferred for JavaScript. It's easy to work with JSON in JavaScript because JSON is a subset of JavaScript. JSON is not a programming language.

---

## Rules of JSON

- six data types
- undefined & functions are not supported
- key/value pairs
- double quotes
- arrays use brackets [ ]
- objects us braces { }
- no single quotes

^ There are six data types: strings, numbers, booleans, arrays, objects & null

^ The undefined data type, and functions are not supported

^ All data types are represented as key/value pairs in double quotes

^ Arrays are represented by brackets and objects by braces

^ Single quotes are not supported

---

```json
01 {
02   "employee": {
03     "id": 1001,
04     "startDate": "7/18/2016",
05     "endDate": null,
06     "isActive": true,
07     "reviewScores": [88,95,96,89],
08     "region": {
09       "name": "Northwest",
10       "joined": "8/20/2016"
11     }
12   }
13 }
```

---

# Objective

## Discuss Working With JSON

## JSON `stringify()` Method

```javascript
01 const task = 'Go to the store';
02 const json = JSON.stringify(task);

// "Go to the store"
```

^ The `stringify` method converts the JavaScript object that's passed to it into a JSON string.

---

```javascript
01 const task = {
02   task: 'Go to the store'
03 };
04 const json = JSON.stringify(task);

// {"task": "Go to the store"}
```

---

```javascript
01 const tasks = [];
02 tasks.push('Go to the store');
03 tasks.push('Pick up the laundry');
04 const json = JSON.stringify(tasks);

// ["Go to the store", "Pick up the laundry"]
```

---

## JSON `parse()` Method

```javascript
01 const json = "{\"Go to the store\", \"Do the laundry\"}";
02 const tasks = JSON.parse(json);

// ["Go to the store", "Do the laundry"]
```

^ The `parse` method uses the information in the JSON string to deserialize the data structure.

^ _(examples/json)_
