# JavaScript Crash Course
Note: this crash course uses some ES6 syntax and features.
## Index
* Data types
* Variables
* Operators
* Arrays
* Logic
* Loops
* Functions
* Objects
* Classes
## Data types
Java script supports the following data types:
* Undefined: This value is used in undefined variables.
* Null
* Number
* String
* Boolean
* Symbol: Objects with a unique value.
* Object
### Strings
Strings can be defined using single or double quotes. Defining them using a ticks allows us to use interpolation:
```js
let a = 5; // Semicolons are optional in JavaScript
let myStr = `This restaurant has ${a} stars`
console.log(myStr);  // console.log() is used to print to the console
// Output: This restaurant has 5 stars
```
The `+` operator can be used to concatenate strings with other strings or other data types:
```js
console.log('This restaurant has' + 5 + 'stars');
```
We can get the length of a string by accessing its length property:
```js
let myStr = 'four';
console.log(myStr.length);
// Output: 4
```
Strings can be indexed using brackets (with indices starting in 0):
```js
let myString = 'Hello World';
let firstLetter = myString[0];
let lastLetter = myString[myString.length - 1];
```
More information on strings and their methods: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
## Variables
Variables can be declared using the `let` keyword:
```js
let a;  // Variable declaration
let b = 5;  // Variable declaration and intialization.
b = 'hello'; // A variable's data type may change.
```
Constants (unmutable variables) can be declared using the `const` keyword:
```js
const a = 10;
a = 20; // Throws an error.
```
A global variable can be declared using the `var` keyword:
```js
var a = 10;
```
A variable declared using `var`can be accessed throughout the program, even if declared inside a function, one declared using `let` can only be accessed within its
block's scope. When a variable is declared using `var` it can be redeclared (which is unsafe) later in the program without
causing an error. `let` doesn't allow this.
## Operators
* `+`: Addition.
* `-`: Substraction.
* `/`: Division.
* `*`: Multiplication.
*`%`: Modulus, used to get the remainder of a division.
* `++`: Increment a variable's value by one.
* `--`: Decrement a variable's value by one.
* `+=`: Addition shorthand.
* `-=`: Substraction shorthand.
* `/=`: Division shorthand.
* `*=`: Multiplication shorthand.
* `>`: Greater than.
* `>=`: Greater or equal.
* `<`: Less than.
* `<`: Less or equal.
* `=`: Assignment operator.
* `==`: Equality operator.
* `===`: Strict equality operator.
* `&&`: Logical and.
* `||`: Logical or.
* `!`: Logical not.
### Shorthands
When incrementing or decrementing the value of a variable, the following shorthands can be used:
```js
let a = 10;
a += 4;  // This is the same as a = a + 4;
a *= 2;  // This is the same as a = a * 2;
a /= 2;  // This is the same as a = a / 2;
a -= 2;  // This is the same as a = a - 2;
console.log(a);
// Output: 12
```
## Arrays
An array can be declared with the following synatx:
```js
let myArray = [1, true, 'hello'];  // Arrays can hold mixed types
let otherArray = new Array();      // Alternative syntax
```
Arrays are dynamic (can be growed or shrinked) and mutable, even if declared using `const` (this only prevents the reassingment 
of a variable, the values of the array can still be changed). I will cover how to make an unmutable array in the Objects section.

You can access and modify the elements of an array using brackets, indices start in 0:
```js
let arr = [1, 2, 4];
arr[2] = 3;
console.log(arr[0]); // Output: 1
console.log(arr);    // Output: [1, 2, 3]
```
You can add an elements to the end of an array using the `push` method. Elements can be added to the beggining using the `unshift` method:
```js
let arr = [2, 3, 4];
arr.unshift(1);
arr.push(5);
arr.push(6, 7);  // Both push and unshift can take multiple parameters
console.log(arr); // Output: [1, 2, 3, 4, 5, 6, 7]
```
You can remove an elements from the end of an array using the `pop` method. Elements can be removed from the beggining using the `shift` method:
```js
let arr = [10, 1, 2, 3, 14];
arr.pop();
arr.shift();
console.log(arr);  // Output: [1, 2, 3]
```
You can remove elements from anywhere in the array using the `splice()` method, which takes two parameters: the index and how many elements to remove.
```js
let arr = [1, 2, 3, 4];
let newArr = arr.splice(0, 2);
console.log(arr);     // Output: [3, 4];
console.log(newArr);  // Output: [1, 2];
```
You can copy elements from an array using the `slice()` method. This method also takes two parameters, the index where the
copy should start (inclusive) and the one where it should end (exclusive):
```js
let arr = [1, 2, 3, 4];
let newArr = arr.slice(0, 3);
console.log(newArr);  // Output: [1, 2];
console.log(arr);     // Output: [1, 2, 3, 4];
```
Finally, an array can be deconstructed on the spot by using the `...` operator (which can be useful as a way to passing it as an argument to a function):
```js
let fragment = [3, 4, 5];
let arr = [1, 2, ...fragment, 6, 7];
console.log(arr);
// Output: [1, 2, 3, 4, 5, 6, 7];
```
## Logic
Logic can be added to a program using `if`, `else` and `else if`:
```js
let myString = '5';
if (myString === 5) {
  // This block won't be executed because we are using the strict
  // equality operator (===) which checks if types match.
  console.log('It\'s true!);
} else if (myString == 5) {
  // On an else if we check if an additional condition is true in
  // case the previous one wasn't.
  // This will be true because the standard equality operator (==)
  // doesn't check if types match.
  console.log('It\'s true!');
} else {
  // This block would be executed if all previous conditions were evaluated to false.
  console.log('It\'s false);
}
```
We can check if multiple conditions are true using the logical AND operator (`&&`):
```js
let a = true;
let b = false;

if (a === true && b === true) {
  // This block won't be executed
} else if (a === true && b === false) {
  // This block will be executed
  console.log('Success');
}
```
We can check if one of two conditions is true using the logical OR operator (`||`):
```js
let a = true;
let b = false;

if (a === true || b === true) {
  // This block will be executed
  console.log('Success');
}
```
We can reverse an evaluation using the logical NOT operator (`!`). This will reverse the situation, if a condition would've
evaluated to true it will evaluate to false and vice versa:
```js
let a = false;

if (!a === true) {
  // This block will be executed
  console.log('Success');
}
```
## Loops
A `while` loop executes until a specified condition evaluates to false. It can be created using the following syntax:
```js
while (condition) {
  // do something
}
```
A `for` loop is similar to a `while` loop, it has a different syntax which allows you to declare an initial expression and an increment expression:
```js
for (initial condition; condition; increment) {
  // do something
}
```
For example:
```js
let arr = [1, 2, 3];
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
// Output: 1  2  3
```
A `do while` loop is the same as a `while` loop, except it executes the code block first and evaluates the condition after, this way the code block will be executed at least once.
```js
do {
  // do something
} while (condition);
```
A `for in` loop allows us to easily loop through enumerable properties of objects. JavaScript will execute the code block for each member of the object. This kind of loop should not be used to iterate through arrays.
```js
for (variableName in object) {
  // do something
  // you can access the current member
  // using the variable defined in the loop
}
```
A `for of` loop is similar to the `for in` loop, except it allows us to iterate through arrays and other iterable objects.

```js
for (variableName of object) {
  // do something
  // you can access the current member
  // using the variable defined in the loop
}
```
For example:
```js
let arr = [1, 2, 3, 4];
for (let i of arr) {
  console.log(i);
}
// Output: 1 2 3 4
```
## Functions
Traditionally functions are defined using the following syntax:
```js
function functionName(arguments) {
  function body
  return statement;
}
```
Example:
```js
function sum(a, b) {
  let result = a + b;
  return result;
```
You can use the property `arguments.length` to get the number of arguments passed to the function.
ES6 introduced arrow functions, which have a different syntax, and allows us to create anonymous and single line functions:
```js
const sum = (a, b) => a + b;  // The "function body" goes after the arrow. The return keyword isn't necessary
                              // and the parenthesis can be ommited if only 1 argument is being used.
// Function with a body
const logNTimes = (str, n) => {
  for (let i = 0; i < n; i++) {
    console.log(str);
  }
```
## Objects
                              
