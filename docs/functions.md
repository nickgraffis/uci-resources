# Functions

## Anatomy of a Function

### Declaration of a Function

![Anatomy of a Function](./assets/function-declaration.png)

1. Name - The name of a function that can be used to _invoke_ it later on.
2. Parameters - A list of inputs that can be passed into a function.
3. Body - The logic or statements that perform the computation.

### Invocation of a Function

A function declaration does nothing on it's own. You make use of functions by calling them. The return value of the function can be assigned to a variable.

![Declaration of a Function](./assets/function-call.png)

1. Function call - Executes the code inside the function body ☝️.
2. Aruguments - The values to be used as _parameters_ in the function.
3. Return value - By default function will return `undefined`, but can return the result of a computation when the body contains a `return` statement.


## Function Declarations vs. Expressions

**A function _declaration_ is a statement that describe what your code does. Declarations are _hoisted_, which means they are loaded at the top of the scope before any other code runs.**

```js
makeBread(2); // Call still works here

function makeBread(qty) {
  return '🍞'.repeat(qty)
}
```

An alternative approach is use a function as a value or _expression_ by assigning any anonymous function to avariable or parameter.

```js
var makeBeer = function(qty) {
  return '🍺'.repeat(qty);
}
```

## 🤔 Should you use declarations or expressions?

There is no universally accepted best-practice, but function expressions are commonly preferred for (1) their ability to be reassigned, (2) flexibility when composing higher order functions, and (3) the fact that they don’t pollute the global scope.

## Parameters and Arguments

You have a variety of ways to structure parameters in a function. Below are examples of positional, named, and rest parameters:

```js
// Positional
function makeBreakfast (main, side, drink) {
    return `Breakfast is ${main}, ${side}, and ${drink}.`;
}

// Named
function makeLunch (opts) {
    const { main, side, drink } = opts;
    return `Lunch is ${main}, ${side}, and ${drink}.`;
}

// Rest params
function makeDinner (main, ...args) {
    return `Dinner includes ${main} and ${args.join('')}.`;
}


makeBreakfast('🥞', '🥓', '🥛'); // Breakfast is 🥞, 🥓, and 🥛.

makeLunch({ main: '🥙', side: '🍟', drink: '🥤' }); // Lunch is 🥙, 🍟, and 🥤.

makeDinner('🍜', '🥘', '🍙', '🥠', '🍑'); // Dinner includes 🍜 and 🥘🍙🥠🍑.
```

## Arrow Functions 

Arrow functions provide syntactic sugar for writing compact code, while also omitting a new `this` object, which solves common pain points when writing object-oriented code. An arrow function is unique because it:

1. Does not have its own `this` object.
2. Implicit return value when brackets are omitted. i.e. `() => true` returns true.
3. Always an expression, never a statement.

```js
const makeBeer = function beerFun(qty) {
    return '🍺'.repeat(qty);
}

const makeWine = (qty) => '🍷'.repeat(qty);
```

## Pure Functions

A pure function is one that only relies only its inputs, produces no side effects, and does not modify values outside its local scope.

Notice how the impure function below mutates a global variable and uses it to calculate the return value. In other words, it depends on values outside of its own function parameters and/or body.

```js
let global = 0;
const impure = () => {
    global++;
    return global ** 2;
}

const pure = (x) => x ** 2;
```

## Higher Order Functions

A _higher order_ function is created by combining (or composing) multiple functions together by passing (1) functions as arguments or (2) returning functions. There are many built-in JS functions that use HOF, for example `setTimeout` and `Array.map`.

```js
// Anonymous
setTimeout( () => console.log('hello!'), 2000);

// Named
const log = () => console.log('hello');
setTimeout(log, 2000);


// Array Map
[1,2,3,4].map(v => v ** 2);
```

🤔 Should you use declarations or expressions?

## Recursive Function

A recursive function is one that calls itself from inside its own function body. If a terminating condition is not provided it will create and infinite loop. Recursive functions are commonly used in algorithm implementations to efficiently handle tasks like binary-tree traversal. Below is an example of a recursive function that traverses the the file system using NodeJS.

```js
const fs = require('fs');
const { join } = require('path');

const traverse = (dir) => {

    const subfolders = fs.statSync(dir).isDirectory() 
                       && fs.readdirSync(dir);

    if (subfolders) {

        console.log('👟👟👟 Traversing ', dir);

        subfolders.forEach(path => {
            const fullPath = join(dir, path);

            traverse( fullPath );

            
        });
    }

}

traverse( process.cwd() );
```

## When should you write functions?

When building an app, you will often ask yourself should I write a new function for that?, but the correct answer is nuanced and highly-subjective. A common acronym in programming is DRY and is aimed at avoiding duplication:

> "DRY Do Not Repeat Yourself"

Find yourself writing repetitive code? Try abstracting it into a custom function. Sounds simple enough, but you should not take DRY to the extreme. If you find yourself having a difficult time coming up with readable function names, it probably means your are over-optimizing and starting to build your own complex framework of abstractions - possibly a much worse situation than duplicated code. People have recognized this issue and counter DRY with WET.

> "WET Write Everything Twice, but not Thrice"

In this world, we only break down code into custom functions when it is duplicated more than twice. The rational is that it provides more confidence that this extra layer of absctraction is actually required. As programmers, we often try to optimize too early because we’re terrified of duplication.

In brief, both DRY and WET are useful principles, but neither are perfect - it just takes practice.