# ✖️ Calculator Tutorial!

[Final Product (CodePen)](https://codepen.io/nickgraffis/pen/XWgLvvq)

## Step 1: Building the HTML
We are going to use [TailwindCSS](https://tailwindcss.com/) to build our HTML. It gives you classes that you can use to style your HTML.

```html
<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
```

Now we can create our HTML using the classes provided by TailwindCSS. First we need to create a container element that will house the calculator:

```html
<div class="min-w-screen min-h-screen bg-gray-100 flex items-center justify-center px-5 py-5">
    <div class="w-full mx-auto rounded-xl bg-gray-100 shadow-xl text-gray-800 relative overflow-hidden" style="max-width:300px">
      ......
    </div>
</div>
```

Next inside of our container, lets create an area where we can visualize the output.
```html
<div class="w-full h-40 bg-gradient-to-b from-gray-800 to-gray-700 items-end text-right">
  <div id="output" class="w-full py-5 px-6 text-6xl text-white font-thin">
  
  </div>
</div>
```
We gave this an id of `output` so we can refrence that back in our JavaScript.

Next we have to create a container for our buttons.
```html
<div class="w-full bg-gradient-to-b from-indigo-400 to-indigo-500">
  ......
</div>
```

Next we want to create rows of buttons and but the actual buttons inside of those rows
```html
<div class="flex w-full">
  <div class="w-1/4 border-r border-b border-indigo-400">
      <button id="clear" class="w-full h-16 outline-none focus:outline-none hover:bg-indigo-700 hover:bg-opacity-20 text-white text-opacity-50 text-xl font-light">
        C
      </button>
  </div>
</div>
```

This row of buttons has the `C` button, which has an id of `clear`. And it's width is `1/4` meaning that we can fit 4 buttons in this area.

We will do this for all of our buttons.

## Step 2: Building the JavaScript

### Helper Functions
First lets make a few helper functions. 
```js
const $ = (selector) => document.querySelector(selector)
```
This function `$` will accept a selector and return the first element that matches that selector. It does this by using the `document` object and calling the `querySelector` method on it.

So if we want to find the `output` element, we can use `$('#output')`. 

```js
const click = (el, cb) => el?.addEventListener('click', cb)
```

Next the `click` function will accept an element and a callback. If the element is not null, it will add an event listener to the element. The event listener will call the callback when the element is clicked.

### Setting Variables
Lets find all of our HTML elements and store them in variables.
```js
const output = $('#output'),
      clear = $('#clear'),
      zero = $('#zero'),
      posneg = $('#posneg'),
      //...etc
```

Let's also create a variable to store the equation we are currently evaluating,
```js
let eq = []
```
So if we have `8 + 8` we can store `[8, '+', 8]` in `eq`.

### Calculator Object
Next I think we should create an object called `c` that will be how we run all of our calculator functions.

```js
const c = { }
```

Here are the methods we will add to this:
1. `c.add` - Add something to the display
```js
add: (exp) => {
    output.innerHTML += exp;
    return c
  },
```
This method just accepts some expression and adds it to the `output` element's `innerHTML`. And then it returns the original object again.

So we could use it like this: `c.add('8').add('+').add('8').add('=')`, and the output html element would be `8 + 8 = `.

2. `c.ad` - Add display to equation
```js
ad: () => {
  eq.push(isNaN(output.innerHTML) ? output.innerHTML : parseFloat(output.innerHTML));
  return c
},
```
This method will take whatever is current inside of the `output` element and add it to the `eq` array. If the output is a number, it will parse it to a number, or if it isn't, like a `+` or `-` it will just add it to the array.

3. `c.ae` - Add some expression to the equation
```js
ae: (exp) => {
    eq.push(exp);
    return c
  },
```
So we can use this like `c.ae('+')` which will add `+` to the equation.

4. `c.calc` - Calculate the equation
```js
calc: () => {
    let total = eval(eq.join(''))
    output.innerHTML = total
    eq = []
  }
```

5. `c.cl` - Clear the display
```js
cl: () => {
    output.innerHTML = ''
    return c
  }
```
Calc will evaluate the equation in `eq` and set the `output` element's `innerHTML` to the result. It will then clear the `eq` array.

### Connecting the button with the calculator
Now that we have this object, we can have every click of the buttons call some methods on it! And we can use our helper `click` function to do this.

```js
click(one, (e) => c.add(1))
```

A very simple one. When the user clicks the `one` button, the `c.add` method will be called and it will add `1` to the `output` element. This does not yet affect the `eq` array, it will just add `1` to the `output` element.

```js
click(plus, (e) => c.ad().ae('+').cl())
```
The plus button is more complecated. We first want to `ad()` add the display to the equation. So if the display says `1` add that to the `eq` array. Then we want to add something directly to the equation, `ae`, we want to add a plus sign to the equation. Then we want to `cl()` clear the display.

```js
click(equals, (e) => c.ad().calc())
```
The equals button will first `ad()` add the display to the equation. Then it will `calc()` evaluate the equation and display it.