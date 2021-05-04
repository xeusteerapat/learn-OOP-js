# Object in Javascript

Almost everything in Javascript is an object. For example, functions, arrays, regular expressions, dates, and even data types like boolean and strings, if declared with the keyword new, can be considered an object.

## Example

Let's say you have 3 shapes: square, rectangle and circle and you want to calculate the areas of all 3 shapes. What would you begin? The common approach would be to write `functions` to compute the areas. Another approach would be using Object-Oriented paradigm by creating `objects` for each shape, each object has its own set of properties like this:

- data values
- functions

![Shapes](shape.png)

Length, width and radius as data values and we require a function to calculate the area as a part of its properties.

## Creating Object Literal

An object literal can be created:

- using `{...}`
- using `new` keyword
- based on existing object by using `create()` method

```javascript
// using {}
const myObject = {  
  // defined properties separated by a comma.
  propertyName1 : propertyValue1,
  propertyName2 : propertyValue2,
  functionName() {}
}

// new keyword
const myObject2 = new Object() // we'll get empty Object

// Object.create()
const myObject3 = Object.create(existingObject)
```

Another example with employee object

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',

  displayName() {
    console.log('My name is Teerapat')
  }
}

employee.displayName()
console.log('Age is:', employee.age)
console.log('My role is:', employee.position)
/* 
Name is Teerapat
Age is: 35
Designation is: Software Developer
*/
```

## Accessing Object Properties

- Dot Operator
- Square Bracket

```javascript
const shape = {
  name : 'square',
  sides : 4
}

// dot operator
console.log("Name is:", shape.name)
console.log("Number of sides are:", shape.sides)

// square bracket
console.log("Name is:", shape['name'])
console.log("Number of sides are:", shape['sides'])
```

## Iterating over Object Properties

using `for...in` syntax

```javascript
const employee = {
  firstName: 'Teerapat', 
  lastName : 'Prommarak',
  age: 35,
  sex: 'male',
  position: 'Software Developer'
}

for (x in employee) {
  console.log(x)
}

/* 
firstName
lastName
age
sex
position
*/
```

## Calling Functions

using `objectName.functionName()` or `objectName['functionName']()`

```javascript
const shape = {
  displaySides() {
    console.log("Square has 4 sides")
  },
  displayName() {
  console.log("Shape is Square")
  }
}

//calling function using dot operator
shape.displayName()
shape.displaySides()

//calling function using square brackets
shape['displayName']()
shape['displaySides']()
```

## Adding, Setting and Deleting Properties

Adding properties

```javascript
const employee = {
  name: 'Xeus',
  age: 35
}

// using dot notation
employee.position = 'Software Engineer';
```

Setting properties

```javascript
const employee = {
  name: 'Xeus',
  age: 35
}

employee.name = 'Teerapat';

// or using square brackets
employee['name'] = 'Teerapat';
```

Deleting properties

```javascript
delete employee.name;
```

## Methods in Object

In case the property is a `function`, it is referred to as an **object method**.

### `this` keyword

Let's consider `employee` object and we want to return value of `employee.position`

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',
  display() {
    return position
  }
}

console.log(employee.display())
```

We'll get an error `ReferenceError: position is not defined`. The reason that we cannot access `position` properties because we do not provide **Reference** to the object whose property we are trying to access. To solve this issue we have to refer to object itself by using `this` keyword, `this` is point to the current object. In this case is refer to the `employee` object like the example below:

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',
  display() {
    // this refers to the employee object
    return this.position
  }
}

console.log(employee.display())
// Software Developer
```

And we also can set the value by using `this`:

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',
  setNewPosition(newPosition) {
    this.position = newPosition
  }
}

console.log('My old position: ', employee.position)
// Software Developer

// update the value
employee.setNewPosition('Solution Architect')

console.log('My new position: ', employee.position)
// Solution Architect
```

## Get & Set

Here is how syntax look like:

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',
  get display() {
    // this refers to the employee object
    return this.position
  }
}

console.log(employee.display) // no need parentheses
// Software Developer
```

So what is different? Just remove parentheses? Using `get` changes the way the method `display()` is called. It is now called in exactly the same way as how a property is called: `employee.display`, whereas without get, it is called as a function: `employee.display()`.

How about `set` keyword

```javascript
const employee = {
  name: 'Teerapat',
  age: 35,
  position: 'Software Developer',
  set setNewPosition(newPosition) {
    this.position = newPosition
  }
}

console.log('My old position: ', employee.position)
// Software Developer

// update the value
employee.setNewPosition = 'Solution Architect'

console.log('My new position: ', employee.position)
// Solution Architect
```

Using the `set` keyword changes the way `setNewPosition` is used in order to set the `position` value.

Both `get` and `set` allow functions to be accesses and changed as data values outside the object.

## Recap

- `Object.create()` Creates an object based on an existing object.
- The values can be updated by using dot notation or square brackets
- Properties, including both data values and functions, can be deleted or removed from an object using the delete operator.
- `this` keyword is points to the current object whose property is being accessed.
- `get` and `set` keywords allow the function to be accessed as a property.
