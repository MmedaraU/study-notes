# Table of Contents
- [Table of Contents](#table-of-contents)
- [References](#references)
- [Introduction](#introduction)
- [Comments](#comments)
- [Data Types](#data-types)
  - [String](#string)
    - [String Operations](#string-operations)
      - [Concatenation](#concatenation)
    - [String Property](#string-property)
    - [String Methods](#string-methods)
      - [The `charAt()` method](#the-charat-method)
      - [The `indexOf()` method](#the-indexof-method)
      - [The `lastIndexOf()` method](#the-lastindexof-method)
      - [The `split()` method](#the-split-method)
    - [The `substring()` method](#the-substring-method)
      - [The `toLowerCase()` and `toUpperCase` methods](#the-tolowercase-and-touppercase-methods)
- [Scope](#scope)
  - [Global scope](#global-scope)
  - [Local Scope](#local-scope)
- [Variables](#variables)
  - [Rules for naming a variable](#rules-for-naming-a-variable)
- [Arrays](#arrays)
  - [Working with Arrays](#working-with-arrays)
    - [Adding to an array](#adding-to-an-array)
  - [Array methods](#array-methods)
- [Objects](#objects)
  - [Adding to an Object](#adding-to-an-object)
  - [Reading from an object](#reading-from-an-object)
  - [Nested Objects](#nested-objects)
    - [Reading from a nested object](#reading-from-a-nested-object)
    - [Assigning object items](#assigning-object-items)
- [Type Conversion](#type-conversion)
- [Operations](#operations)
  - [Assignment Operators](#assignment-operators)
  - [Mathematical Operators](#mathematical-operators)
  - [Comparison Operators](#comparison-operators)
  - [Logical Operators](#logical-operators)
  - [Ternary Operator](#ternary-operator)
- [Flow of Control Statements](#flow-of-control-statements)
  - [The `if` and `if...else` statements](#the-if-and-ifelse-statements)
  - [The `switch` statement](#the-switch-statement)
- [Loops](#loops)
  - [The `while` loop](#the-while-loop)
  - [The `do...while` loop](#the-dowhile-loop)
  - [The `for` loop](#the-for-loop)
  - [The `for...in` loop](#the-forin-loop)
- [Jumps](#jumps)
  - [The `break` statement](#the-break-statement)
  - [The `continue` statement](#the-continue-statement)
  - [The `return` statement](#the-return-statement)
- [Functions](#functions)
- [The Browser Object Model](#the-browser-object-model)

# References
> **Jump Start JavaScript** by *Ara Pehlivanian and Don Nyugen*
> 
> **JavaScript Weekend Crash Course** by *Steven Disbrow*  


# Introduction

Properties are variables that hold information about the data in the object. They give you details about the data in an object. Example
```js
string.length() //length is the property`
```

Methods are functions that belong to an object. They allow you perform tasks using the data in the object.
# Comments
```js
// This is a single-line comment
/* This is a multi-line comment */
```

# Data Types
1. number 
2. string
3. Boolean
4. null  
    Used when you want to declare a variable and intentionally express the absence of a value.
5. undefined  
    Represents the state of a variable that has been declared without a value assigned to it.
6. object 

## String
### String Operations
#### Concatenation
Joining two or more strings together. Uses the plus `+` sign
```js
var stringOne, stringTwo;
var concatString = stringOne + stringTwo;

// Second way
// x += y : x = x + y
stringOne += stringTwo;
```
### String Property
The `length` property returns the length of the string.
### String Methods
Strings are implemented as objects. Methods are functions that belong to an object. They allow you perform tasks using the data in the object.

#### The `charAt()` method
Allows you extract a single character from a specified position in a String object.
`string.charAt([index])`

#### The `indexOf()` method
Searches a String for the first instance of a substring. Returns `-1` if substring is not found. Spaces are also counted. The `indexOf()` method is case-sensitive.

```js
item = "Stroller and Sunshade";
item.indexOf("Sun"); // Returns 14
```

#### The `lastIndexOf()` method
Searches a String for the last instance of a substring. Searches from the end of the string. You can specify what index the search should start from.

#### The `split()` method
Splits a string into an array

### The `substring()` method
Extracts a new String from an existing String.
```js
string.substring(indexOne, indexTwo);
```

`indexOne` is the starting position of the string you want to extract.  
`indexTwo` is the position after the last character to be included in the string, else it won't be included. It is optional.

#### The `toLowerCase()` and `toUpperCase` methods
Change string to lowercase and uppercase characters respectively.

# Scope
A concept that determines if a variable or function defined in one part of the program is accessible in another part.

## Global scope
Functions or variables with a global scope are accessible form anywhere in the file.

## Local Scope
Local variables are defined in a function and can only be accessed from the function in which they are defined.

# Variables
Variables are the most basic form of data storage in JavaScript.  
```js
//Single declaration
var task = "Write the first chapter.";

// Multiple declarations
var task = "Write the first chapter.",
    complete = true;

```
JavaScript is case-sensitive so `task` and `Task` will be treated as different variables.  
The semi-colon `;` indicates the end of a line of code.  
It is best to keep variable declarations and initializations separate so errors encountered when debugging can be easily sorted out.
```js
var task, complete;

task = "Write the first chapter.";
complete = true;
```

## Rules for naming a variable
1. Variable names are case sensitive.
2. Variable names must start with an alphabet, a dollar sign or an underscore and can contain numbers, letters, a dollar sign or an underscore.
3. Spaces and other special characters are not allowed.
4. Variable names can be as long you want, but it is advisable to keep them under 50 characters long.

# Arrays
Arrays are used to store a collection of data.
```js
// Creating an array
var myArray = new Array();
/*OR*/
var myArray = [] /*This is an array literal*/
```
The array literal represents an empty array. It's less verbose and safer to use than the `new Array()` syntax, because the `Array` constructor can be overwritten and replaced with malicious code.

Arrays can contain any data type and they can be mixed
```js
var things = [1, "apple", undefined, 42, "thanks", null, []];
```
## Working with Arrays
### Adding to an array
An empty array can be created and then added to in several ways

```js
// By indices
var myArray = [];
myArray[0] = "Hello";
myArray[1] = "World";
```
Using indices can lead to one-off errors.

```js
// Using named indices
var myArray = [];
myArray["fruit"] = "apple";
myArray["vehicle"] = "tank";
```
This creates an associative array where items are stored by a named index rather than a numbered index. Cannot be retrieved with a numbered index. Uses a special `for` loop
```js
/* Loops through array and presents the value at each index*/
// x = indexName, written as x though
// array[x] = value at indexName
for (x in array) {console.log(array[x])};
```

```js
// Using the push method
var myArray = [];
myArray.push("hello");
```
The `push()` method adds a new item at the end of the existing array.

## Array methods
1. The `Array()` constructor method  
    ```js
    //With no parameters - creates an empty array
    new Array()

    // With a length parameter - creates the specified number of empty slots
    new Array(length)

    // With multiple parameters
    // The array slots are filled with the items passed as parameters
    new Array(item1, item2, etc.)
    ```
2. The `pop()` method  
    Removes the last element and returns the rest of the array.
3. The `push()` method  
    Adds an element to the end of the array and returns the new array.
4. The `reverse()` method  
    Reverses the order of items in the array.
5. The `shift()` method  
    Removes the first item and returns the array.
6. The `sort()` method  
    Sorts array items in ascending order or in the order that you specify within a `sort()` function. Every item is converted to strings and arranged.  
    The sorting function is called again and again until all elements are sorted.
    ```js
    function simpleSort(item1, item2) {
        var result = 0;
        if (item1 > item2)
        result = 1;

        if (item1 < item2)
            result = -1;

        if (item1 == item2) 
            result = 0;

        return result;
        }

        items = new Array("Diapers", "Baby Wipes", "Rattle", "Car Seat", "Stroller");
        items.sort(simpleSort);
    ```
7. The `splice()` method  
    Lets you remove an item or items and/or add a new item or items in its place.  
    ```js
    array.splice(indexToStartFrom, howManyItemsToRemove, [newItem(s)]);
    ```
8. The `unshift()` method  
    Adds one or more items to the beginning of the array.

9.  The `concat()` method  
    Combines multiple arrays into one.  
    ```js
    //arrayN = array1 + array2 + array3
    arrayN = array1.concat(array2, array3)
    ```

10. The `join()` method  
    Takes the values in an array and joins them into a string. You can specify what the separator, but the default is a comma.  
    `array.join(",")`

11. The `slice()` method  
    Copies a part of an array and returns it.
    `arr.slice(startingIndex)`

12. The `toString()` method  
    Returns a string with the items in the array. Exactly the same as using the `join()` method without specifying a delimiter.

13. The `indexOf()` method
    *Check [The `indexOf()` method](#the-indexof-method)* 

14. The `lastIndexOf()` method
    *Check [The `lastIndexOf()` method](#the-lastindexof-method)*


# Objects
Like arrays, they are containers for collections of data. Though arrays are actually a type of object.
```js
// Initializing an object
var myObject = new Object();
var myObject = {}; //Safer and preferable
```

Objects use a key/value pair system.
```js
profile = {
    firstName: "Hugo",
    lastName: "Reyes"
};
```

## Adding to an Object
```js
// Bracket Notation
var obj = {};
obj["firstName"] = "Hugo";
obj["lastName"] = "Reyes";

// Dot notation
var obj = {};
obj.firstName = "Hugo";
obj.lastName = "Reyes";
```

## Reading from an object
Arrays cannot be read using a numeric index, just a named one.
```js
// Bracket Notation
alert("Hello, my name is " + obj[firstName] + " " + [obj.lastName] + ".");

// Dot notation
alert("Hello, my name is " + obj.firstName + " " + obj.lastName + ".");
```

## Nested Objects
```js
var person;

person = {
    name: {
        first: "Mmedara",
        last: "Umana"
    }
}
```
### Reading from a nested object
```js
person.name.first; //returns "Mmedara"
person.name.last; //returns "Umana"
```

### Assigning object items
```js
var person;

person = {};
person.name = {};
person.name.first = "Mmedara";
person.name.first = "Umana";
```

# Type Conversion

# Operations
## Assignment Operators
```js
var content = "Hi";

// Second Way
// x += y : x = x + y
x = 10; y = 5;
x += y; // x = 15
```
## Mathematical Operators
1. Increment by 1 `++`
2. Decrement by 1 `--`
3. Addition `+`
4. Subtraction `-`
5. Multiplication `*`
6. Division `/`
7. Modulus `%`

## Comparison Operators
Used to compare values and return `true` or `false` based on how they compare.

1. Equal `==`
2. Not equal `!=`
3. Strict equal `===`
4. Strict not equal `!==`
5. Greater than `<`
6. Greater than or equal to `>=`
7. Less than `<`
8. Less than or equal to `<=`

## Logical Operators
1. AND operator `&&`
2. OR operator `||`
3. NOT operator `!`
4. 

## Ternary Operator
Used to shorten the `if..else` statement
```js
// If...else statement
if (hours < 10) {
  hours = "0" + hours;
} else {
  hours = hours.toString();
}

// Ternary Operator
result = (conditon) ? (evaluate if true) : (evaluate if false);
hours = (hours < 10) ? "0" + hours : hours.toString();
```


# Flow of Control Statements
## The `if` and `if...else` statements
Lets you decide if a block of code will execute.
```js
//if statement
if (condition) {
    do thing;
    do another thing;
    }

//if...else statement
if (conditon) {
    do thing;
} else {
    do other thing;
}

// nested if...else statements
if (condition) {
    if (..){}else{}
} else {
    if (..){}else{}
}
```

## The `switch` statement
Allows you choose between the known values of a variable and execute a corresponding cede block.
```js
// General expression
switch(variable) {
    case One: {
        do thing;
        break;
    }
        case Two: {
        do another thing;
        break;
    }
        default: {
        do default thing;
    }
}

// Example
strollerPrice = 199;

switch (strollerPrice) {
  case 49: {
    document.write("Wow! This is cheap!");
    break;
  }
  case 99: {
    document.write("Very affordable");
    break;
  }
  case 149: {
    document.write("A bit pricey, but nice!");
    break;
  }
  default: {
    document.write("This is a high-end model!");
  }
}
```

# Loops
A *loop statement* is used when we want to repeat some programming statements until a specified condition is reached.

## The `while` loop
```js
while (condition) {
    statement
}

// Example
var tasksToDo = 3;

while (tasksToDo > 0) {
  console.log("There are " + tasksToDo + " tasks to do.")
  tasksToDo--;
}
```

## The `do...while` loop
Used when a statement has to be executed at least once.
```js
do {
    statement
} while (expression);

// Example
var tasksToDo = 3;

do {
  console.log("There are " + tasksToDo + " tasks to do.");
  tasksToDo--;
} while (tasksToDo > 0);
```

The condition can be any expression that evaluates to true or false. The statement is executed if the condition evaluates to true.


## The `for` loop
Used to run a code block a number of times.
```js
for (initialization; condition; end-expression) {
    statement
}

for (var i = 0; i < 3; i++) {
    console.log(i);
}

// Multiple Tests
// Testing that i is less than 10 and divisible by 2
for (var i = 0; i < 10 && i % 2 === 0; i+=4) {
    console.log(i);
}

// Multiple Initializations
for (var i = 0, j = 0; i < 3; i++, j+=2) {
    console.log(i, j);
}

//Other end expressions
// Prints random numbers until it gets a value of o.9 or greater
for (var i = 0; i < 0.9; i = Math.random()) {
    console.log(i);
}
```

## The `for...in` loop

# Jumps
A *jump statement* allows code to exit loops. It is used to move to another part of the script.
* `break`
* `continue`
* labeled statements
* `return`
  
`return` is used for exiting functions, while the rest are used with loops.

## The `break` statement
Used to exit from a loop.
```js
var tasks = [
  { name: "Buy milk", complete: false },
  { name: "Trash", complete: false },
  { name: "Pay bills", complete: true },
];
var firstComplete;

for (var i = 0; i < tasks.length; i++) {
  if (tasks[i].complete) {
    firstComplete = tasks[i];
    break;
  }
}
console.log(firstComplete);
```

## The `continue` statement
Skips to the next iteration in the loop. In a `while` loop, the condition is tested again. In a `for` loop, the end expression is run and the loop continues
```js
// Prints tasks that are complete

var tasks = [
  { name: "Buy milk", complete: false },
  { name: "Trash", complete: false },
  { name: "Pay bills", complete: true },
  { name: "Repairs", complete: false },
  { name: "Plumber", complete: true },
];
var firstComplete;

for (var i = 0; i < tasks.length; i++) {
  if (!tasks[i].complete) {
    continue;
  }
    console.log(i, tasks[i].name);
}
```

## The `return` statement
```js
// General expression
return expression;

return;
```
Can only be used within a function and is used to delineate the return value of a function. If omitted, the return value is undefined.


# Functions
Functions are only executed when you call them.
```js
function fnName (parameters) {do something}
```

# The Browser Object Model
