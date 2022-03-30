## The Assignment Operator `=`
Assign values (both primitive, objects, and expressions) to variables.
```js
var a = 1; // a = 1
```

## The Addition Operator `+`
Add two numbers together.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a + b; // c = 3
```

## The Subtraction Operator `-`
Subtract one number from another.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a - b; // c = -1
```

## The Multiplication Operator `*`
Multiply two numbers together.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a * b; // c = 2
```

## The Division Operator `/`
Divide one number by another.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a / b; // c = 0.5
```

## The Exponentation Operator `**`
Exponentiate one number by another.
```js
var a = 2; // a = 2
var b = 3; // b = 3
var c = a ** b; // c = 8
```

## The Modulus Operator `%`
Find the remainder of one number divided by another.
```js
var a = 5; // a = 5
var b = 2; // b = 2
var c = a % b; // c = 1
```

## The Increment Operator `++`
Increment a number by one.
```js
var a = 1; // a = 1
var b = ++a; // b = 2
```

## The Decrement Operator `--`
Decrement a number by one.
```js
var a = 1; // a = 1
var b = --a; // b = 0
```

## The Logical AND Operator `&&`
Logical AND operator. Returns the first operand if it is truthy, otherwise returns the second operand.
```js
var a = true; // a = true
var b = false; // b = false
var c = a && b; // c = false
```
## The Logical OR Operator `||`
Logical OR operator. Returns the first operand if it is truthy, otherwise returns the second operand.
```js
var a = true; // a = true
var b = false; // b = false
var c = a || b; // c = true
```

## The Logical NOT Operator `!`
Logical NOT operator. Returns the opposite of the operand.
```js
var a = true; // a = true
var b = !a; // b = false
```

## The Equality Operator `==`
Equality operator. Returns true if the operands are equal, otherwise returns false. Not strict equality, so the type of the values does not need to be the same.
```js
var a = 1; // a = 1
var b = 1; // b = 1
var c = a == b; // c = true
```

## The Strict Equality Operator `===`
Strict equality operator. Returns true if the operands are equal, otherwise returns false. The type of the values must be the same.
```js
var a = 1; // a = 1
var b = "1"; // b = "1"
var c = a === b; // c = false
```

## The Inequality Operator `!=`
Inequality operator. Returns true if the operands are not equal, otherwise returns false. Not strict equality, so the type of the values does not need to be the same.
```js
var a = 1; // a = 1
var b = 1; // b = 1
var c = a != b; // c = false
```

## The Strict Inequality Operator `!==`
Strict inequality operator. Returns true if the operands are not equal, otherwise returns false. The type of the values must be the same.
```js
var a = 1; // a = 1
var b = "1"; // b = "1"
var c = a !== b; // c = true
```

### The Ternary Operator `?`
Ternary operator. Returns the first operand if it is truthy, otherwise returns the second operand.
```js
var a = true; // a = true
var b = false; // b = false
var c = a ? b : a; // c = false
```

## The Addition Assignment Operator `+=`
Addition assignment operator. Adds the second operand to the first and returns the result.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a += b; // c = 3
```

## The Subtraction Assignment Operator `-=`
Subtraction assignment operator. Subtracts the second operand from the first and returns the result.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a -= b; // c = -1
```

## The Multiplication Assignment Operator `*=`
Multiplication assignment operator. Multiplies the second operand by the first and returns the result.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a *= b; // c = 2
```

## The Division Assignment Operator `/=`
Division assignment operator. Divides the second operand by the first and returns the result.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a /= b; // c = 0.5
```

## The Exponentation Assignment Operator `**=`
Exponentation assignment operator. Exponentiates the second operand by the first and returns the result.
```js
var a = 2; // a = 2
var b = 3; // b = 3
var c = a **= b; // c = 8
```

## The Modulus Assignment Operator `%=`
Modulus assignment operator. Finds the remainder of the second operand divided by the first and returns the result.
```js
var a = 5; // a = 5
var b = 2; // b = 2
var c = a %= b; // c = 1
```

## JavaScript String Operators
### The Concatenation Operator `+`
Concatenate two strings together.
```js
var a = "Hello"; // a = "Hello"
var b = "World"; // b = "World"
var c = a + b; // c = "HelloWorld"
```

### The String Concatenation Operator `+=`
Concatenate a string to another string.
```js
var a = "Hello"; // a = "Hello"
var b = "World"; // b = "World"
var c = a += b; // c = "HelloWorld"
```

## Adding Strings and Numbers
If you want to add a number to a string, you can use the addition operator, this will convert the number to a string first.
```js
var a = "Hello"; // a = "Hello"
var b = 1; // b = 1
var c = a + b; // c = "Hello1"
```

If you try to add a _number-like_ string to a number, JavaScript will convert the string to a number first.
```js
var a = 1; // a = 1
var b = "1"; // b = "1"
var c = a + b; // c = "11"
```

## JavaScript Comparison Operators
### The Greater Than Operator `>`
Greater than operator. Returns true if the first operand is greater than the second operand, otherwise returns false.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a > b; // c = false
```

### The Greater Than Or Equal To Operator `>=`
Greater than or equal to operator. Returns true if the first operand is greater than or equal to the second operand, otherwise returns false.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a >= b; // c = false
```

### The Less Than Operator `<`
Less than operator. Returns true if the first operand is less than the second operand, otherwise returns false.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a < b; // c = true
```

### The Less Than Or Equal To Operator `<=`
Less than or equal to operator. Returns true if the first operand is less than or equal to the second operand, otherwise returns false.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a <= b; // c = true
```

## JavaScript Type Operators
### The Type Of Operator `typeof`
Type of operator. Returns a string indicating the type of the operand.
```js
var a = 1; // a = 1
var b = "1"; // b = "1"
var c = typeof a; // c = "number"
var d = typeof b; // d = "string"
```

### The Instance Of Operator `instanceof`
Instance of operator. Returns true if the operand is an instance of the object, otherwise returns false.
```js
var a = new Number(1); // a = 1
var b = new String("1"); // b = "1"
var c = a instanceof Number; // c = true
var d = b instanceof String; // d = true
```

## JavaScript Bitwise Operators
### The Bitwise AND Operator `&`
Bitwise AND operator. Returns the bitwise AND of two operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a & b; // c = 0
```

### The Bitwise OR Operator `|`
Bitwise OR operator. Returns the bitwise OR of two operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a | b; // c = 3
```

### The Bitwise XOR Operator `^`
Bitwise XOR operator. Returns the bitwise XOR of two operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a ^ b; // c = 3
```

### The Bitwise NOT Operator `~`
Bitwise NOT operator. Returns the bitwise NOT of the operand.
```js
var a = 1; // a = 1
var b = ~a; // b = -2
```

### The Bitwise Left Shift Operator `<<`
Bitwise left shift operator. Returns the bitwise left shift of the operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a << b; // c = 4
```

### The Bitwise Right Shift Operator `>>`
Bitwise right shift operator. Returns the bitwise right shift of the operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a >> b; // c = 0
```

### The Bitwise Zero Fill Right Shift Operator `>>>`
Bitwise zero fill right shift operator. Returns the bitwise zero fill right shift of the operands.
```js
var a = 1; // a = 1
var b = 2; // b = 2
var c = a >>> b; // c = 0
```

Learn more about bitwise operators [here](https://jsfiddle.net/L8muvg7r/28/).