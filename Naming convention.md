### Naming Convention Challenge in JavaScript

In this challenge, you will practice using naming conventions in JavaScript. Proper naming conventions can make your code more readable, maintainable, and understandable by other developers.

#### Example

```javascript
// Example code with improper naming conventions
var aa = "Hello";
var bB = "World";

function PrintMessage() {
  console.log(aa + " " + bB);
}

PrintMessage();
```

#### Releases

For each release, you will be given a task to complete. Follow the instructions and use proper naming conventions to complete the task.

##### Release 1

Declare a variable named `userAge` and assign it the value of your age.

##### Release 2

Declare a function named `calculateDogYears` that takes one parameter, `dogYears`, and returns the equivalent human years. One dog year is equal to seven human years.

##### Release 3

Declare an object named `person` with the properties `name` and `age`. Set the value of `name` to your name and the value of `age` to your age.

##### Release 4

Declare an array named `fruits` with the values "apple", "banana", and "orange".

##### Release 5

Declare a class named `Car` with the properties `make`, `model`, and `year`. Write a constructor function that initializes the properties with the values passed in as arguments.

### Solution

```javascript
// Release 1
const userAge = 25;

// Release 2
function calculateDogYears(dogYears) {
  return dogYears * 7;
}

// Release 3
const person = {
  name: "John",
  age: 25,
};

// Release 4
const fruits = ["apple", "banana", "orange"];

// Release 5
class Car {
  constructor(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }
}
```

**Note:** This is just one way to solve the challenge. There can be multiple correct solutions, as long as they follow proper naming conventions.





## JavaScript Naming Convention Challenge

In this challenge, you will practice using advanced naming conventions in JavaScript. Proper naming conventions can make your code more readable, maintainable, and understandable by other developers. This challenge is designed to test your understanding of advanced naming conventions in JavaScript.

### Example

Here is an example of code with improper naming conventions:

```javascript
// Improper naming conventions
var a = "Hello";
var b = "World";

function x() {
  console.log(a + " " + b);
}

x();
```

### Releases

For each release, you will be given a task to complete. Follow the instructions and use proper naming conventions to complete the task.

#### Release 1

Declare a constant named `PI` and assign it the value of the mathematical constant pi.

#### Release 2

Declare a function named `sumArray` that takes an array of numbers as a parameter and returns the sum of all the numbers in the array.

#### Release 3

Declare an object named `person` with the properties `firstName` and `lastName`. Set the value of `firstName` to your first name and the value of `lastName` to your last name. Use the object shorthand notation.

#### Release 4

Declare a variable named `favoriteBooks` and assign it an array of objects. Each object should have the properties `title` and `author`. Choose at least two books that you like and include them in the array.

#### Release 5

Create a class named `Person` with the properties `name`, `age`, and `address`. Write a constructor function that initializes the properties with the values passed in as arguments. Use the `this` keyword to set the properties.

### Solution

Here's an example of how you could solve the challenge:

```javascript
// Release 1
const PI = Math.PI;

// Release 2
function sumArray(numbers) {
  return numbers.reduce((acc, val) => acc + val, 0);
}

// Release 3
const person = {
  firstName: "Alice",
  lastName: "Smith"
};

// Release 4
const favoriteBooks = [
  { title: "The Hitchhiker's Guide to the Galaxy", author: "Douglas Adams" },
  { title: "The Lord of the Rings", author: "J.R.R. Tolkien" }
];

// Release 5
class Person {
  constructor(name, age, address) {
    this.name = name;
    this.age = age;
    this.address = address;
  }
}
```

Note that this is just one possible solution for each release, and there may be other correct answers that also follow proper naming conventions.
