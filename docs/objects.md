# Objects
Javascript has 7 primative data types: `undefined`, `null`, `boolean`, `number`, `string`, `symbol`, and `bigint`.

That means that generally everything else in Javascript is an `object`.

## Creating an object with object literals
You generally define an object using the `{}` syntax, or _object literal syntax_

```js
const obj = { }
```

Inside of your object is a collection of properties, which are key-value pairs. A _key_, or _property name_ is any string-like value. And if the property name includes a leading number, a hyphen, or a space, you'll need to srap the property name in quotes.

The value of a property is any value, including another object.

```js
const obj = {
  pumpkin: '🎃',
  'grim-reaper': '💀',
  candy: {
    lollipop: '🍭',
    'cotton candy': '🍬',
  }
}
```

## Accessing properties

You can access a property of an object using the `.` operator or the `[]` operator. If your property name includes a leading number, a hyphen, or a space, you'll need to use the `[]` operator. You can chain property accessors to access nested properties.

```js
console.log(obj.pumpkin) // 🎃
console.log(obj['grim-reaper']) // 💀
console.log(obj.candy.lollipop) // 🍭
console.log(obj.candy['cotton candy']) // 🍬
```

## Updating property values, and adding new properties

You can update an objects propertys by assigning a new value to it. You can also add properties, even if you declared the object using the `const` keyword. You set new properties the same way.

```js
obj.pumpkin = '🍰'
obj['grim-reaper'] = '☠️'
obj.dracula = '🦇'

console.log(obj.pumpkin) // 🍰
console.log(obj.dracula) // 🦇
```

## Deleting properties

You can delete a property from an object by assigning `undefined` to it. You can also delete properties by using the `delete` keyword.

```js
delete obj.pumpkin
obj['grim-reaper'] = undefined

console.log(obj['grim-reaper']) // undefined
console.log(obj.pumpkin) // undefined
```

## Optional chaining

In the situation where a property is undefined, you can use the `?` operator to check if the property exists. And then continue to acesses nested properties. If the property is defined, you can access it. If not, the `?` operator will return `undefined`. When using optional chaining with the `[]` notation, you can use the `?.` operator to check if the property exists. _Notice the extra dot_. If you do not use optional chaining you will get an error when trying to access a property that does not exist.

```js
delete obj.candy

console.log(obj.candy?.lollipop) // undefined
console.log(obj.candy?.['cotton candy']) // undefined
console.log(obj.candy.lollipop) // TypeError: undefined is not an object (evaluating 'obj.candy.lollipop')
```

This is much cleaner than the old way we would have to do things

```js
if (obj.candy) console.log(obj.candy.lollipop)
else console.log(undefined) // undefined
```

## The Object constructor

You can use the Object constructor to create new objects with the `new` keyword.

```js
const object = new Object()

object.dracula = '🧛🏻‍♂️'
object.witch = '🧙‍♀️'
```

## The Object.create() method

You can can also use the Object.create() method to create new objects, that inheirt from an existing object. You can also pass in an empty object, or null, but it is most powerful if you want the object to inheirt properties of another object.

```js
const object = Object.create({})
```

A weird gotcha here though is that if you create an object with `Object.create()` and pass in an object, the new object will have all of the properties of the object you passed in, but those will not be visible immediately. You have to use the `Object.getOwnPropertyNames()` method to get the names of the properties. Or access those properties directly.

```js{4-8}
const monster = {
  eats: Math.random() > 0.5 ? '🧠' : '🫀',
}

const object = Object.create(monster)

console.log(object) // { }

console.log(object.eats) // '🧠'

console.log(Object.getPrototypeOf(object)) // { eats: '🧠' }
```

## Object.defineProperty() method

You can use the `Object.defineProperty()` method to add properties to an object. You pass in the object you want to add the property to, and the property name and _descriptor_. You can use the `value` property in the descriptor to set the value of the property. You can also use the `get` and `set` properties to set the getter and setter functions.

```js
Object.defineProperty(object, 'unicorn', {
  value: '🦄',
})
```

You can even customize the objects getters and setters.
const obj = Object.create({})

```js
Object.defineProperty(obj, 'rabbit', {
	get() {
  	return '🐰'
  },
  set(value) {
  	console.log(value)
  }
})

console.log(obj.rabbit) // 🐰
obj.rabbit = '🐇' // 🐇
console.log(obj.rabbit) // 🐰
```

This isn't how you will generally be working with objects, but understanding how they work is important. Here we have basically forced the get of the `rabbit` property to return `🐰`, so no water what we assign to the property value, we will always be given `🐰`.

We have also adjusted the setter function to log the value that is being assigned to the property. You can add logic in this setter to do anything, such as updating an addtional piece of data.

## Tips and tricks working with literals

Most of the time you'll just be working with the object literal syntax, and you can do some cool things.

1. You can define properties when creating an object to the value of variables, if the variable name matches the property name.

```js
const spider = '🕷'
const legs = 8

const obj = {
  spider,
  legs
}

console.log(obj) // { spider: '🕷', legs: 8 }
```

2. Conversly, you can also deconstruct an object into variables, and assign a variable to each of the properties you would like. You could even rename them to help stop them from clashing with other variable names.

```js
const { spider: mySpider, legs } = obj

console.log(legs) // 8
console.log(mySpider) // 🕷
```

3. This works for nested objects as well...

```js
const spider = '🕷'
const legs = 8

const obj = {
  spider,
  legs,
  species: {
    class: 'Arachnida',
    phylum: 'Arthropoda',
  }
}

const { species: { class, phylum: myPhylum } } = obj

console.log(class) // Arachnida
console.log(myPhylum) // Arthropoda
```

4. You can create property names dynamically, by using the `[]` notation. This can be really useful if a property you are adding is unknown at runtime. 

```js
const getTime = (time) => {
  switch (time) {
    case 'morning':
      return '🌅'
    case 'afternoon':
      return '🌆'
    case 'evening':
      return '🌇'
    case 'night':
      return '🌆'
    default:
      return '🌄'
  }
}

const schedule = {}

schedule[getTime('morning')] = 'brush teeth'

console.log(schedule) // { '🌅': 'brush teeth' }
```

## Property values can be functions

```js
const obj = {
  spider,
  legs,
  web: '',
  makeWeb() {
    this.web += '🕸'
  }
}
```

When we create a method this way, the shorthand version, `this` is the object that the method is being called on. The same can be sadi for creating a method with the `function` keyword; `makeWeb: funciton() { }`.

However, if we were to use arrow syntax, the `this` keyword would be the global object. `makeWeb: () => { }`. In that case you would need to create some sort of global variable.

```js
let web = ''

const obj = {
  spider,
  legs,
  makeWeb: () => {
    this.web += '🕸'
  }
}
```

You can also use `this` to return the object itself, from methods. Allowing you to chain methods together, a la jQuery

```js
const obj = {
  spider,
  legs,
  web,
  makeWeb() {
    this.web += '🕸'
    return this
  }
}

obj.makeWeb().makeWeb().makeWeb()

console.log(obj.web) // 🕸🕸🕸
```

## Digging Deeper

Objects references are stored in the heap, and are not copied when you pass them around. This means that if you pass an object to a function, and that function modifies the object, the changes will be reflected in the original object. This behavior is not the same for primitives, which are copied when you pass them around.

```js
var a = '🎃'
var b = a

console.log(a, b) // 🎃, 🎃
```

So when you change the value of a, it will not change the value of b

```js
var a = '🎃'
var b = a
var a = '👽'

console.log(a, b) // 👽, 🎃
```

In the case of an object, however, the object itself is refrenced when creating a new variable. So if you change the value of a, it will change the value of b.

```js
var a = { boo: '🎃' }
var b = a
console.log(a, b) // { boo: '🎃' }, { boo: '🎃' }

a.boo = '👻'
console.log(a, b) // { boo: '👻' }, { boo: '👻' }
```

A way to get around this would be to create a new object and have it inherit the properties of another object.

```js
var a = { boo: '🎃' }
var b = Object.assign({ }, a)
```

You can see exactly what properties will be copied over with `Object.getOwnPropertyNames(a)`. This only uses the internal, enumerable properties of a. Any other property names that it inherited hire up in the prototype chain will not be copied over.

In addition if this object were to reference other objects, those objects would not be recursivly deep copied over. If a was making a reference to another object, those objects would still be copied over by reference, it wouldn't recursively copy over all the values in those nested objects.

## Spread syntax

A better alternative to this would be to use the spread syntax. This allows you to place an enumerable data type, in this case an object, into another object by spreading out all of it's properties and values. This has some minor differences to `Object.assign()`, including that nested objects are recursivly deep copied over.

```js
var b = { 
  ...a,
  something: 'else'
}
```

## Looping over an object

### For in loop
You can use a for in loop to loop over all the enumerable properties of an object, including it's prototypes.

```js
var object = {
  commet: '☄️',
  dinosaur: '🦖',
}

for (k in object) {
  console.log(k) // commet, dinosaur
}
```

### Object.keys()
You can also use `Object.keys()` to get an array of all the enumerable properties of an object.

```js
for (v of Object.keys(object)) {
  console.log(v) // commet, dinosaur
}
```

### Object.values()
Or you can use `Object.values()` to get an array of all the values of an object.

```js
for (v of Object.values(object)) {
  console.log(v) // ☄️, 🦖
}
```
### Object.entries()
Or you can use `Object.entries()` to get an array of tuples the key/value pairs of an object.

```js
for ([k, v] of Object.entries(object)) {
  console.log(k, v) // commet, ☄️, dinosaur, 🦖
}
```

## Constructor functions

You can customize the way a new object is created by using a constructor function. This is a function that is called when you use the `new` keyword. This method can replace `new Object()`. By convention, capitalized names are used for constructor functions. Then you initilize the object with the `new` keyword.

```js
function Zombie(name) {
  this.name = name
  this.reanimated = Date.now()
  this.eatBrain = function() {
    return `${this.name} is hungry for 🧠!`
  }
}

var object = new Zombie('🧟‍♂️ Nick')

console.log(object.eatBrain()) // 🧟‍♂️ Nick is hungry for 🧠!
```

The `Class` keyword in Javascript is just shorthand for a constructor function.