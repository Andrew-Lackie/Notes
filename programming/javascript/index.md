# JavaScript

## Basic Syntax

### Comments

```javascript

var number = 5; // in-line comment

/*
This is a 
multi
line
comment */

```

### Data Types:

#### Undefined, null, boolean, string, symbol, number, and object

```javascript

var a; // Declared variable

a = "hi" // Assigned variable

var b = 2; 

console.log(b) // Will equal 2

b = 8; 

console.log(b) // Will equal 8

let ourName = "freecodecamp" // Only used in the scope where it is declared

const pi = 3.14 // Can never Change

var ourArray = ["John", 10]

```
### Built in Functions

#### Indexes from 0
```javascript

var x = "Andrew"

x.length // Gives length of the string

var ourArray = ["hi", "J", 10]

ourArray.push(["ten", 11]) // Appends the values

ourArray.pop() // Removes the last element
```
### Functions

```javascript

function function(a, b){
	console.log(a - b);
}

function(10, 5)
```

### If statement

```javascript

function function(isTrue){
	if (isTrue){
		return "Yes, true."
	}
	return "No, false."
}
```
