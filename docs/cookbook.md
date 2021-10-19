## Deploy to Netlify

<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://app.yac.com/embed?url=https://yac.com/play/0rYEwA4xo" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

## Node JS, NPM, and `require`

An extreamly basic concept of all programming languages is the ability to break up code into modules. A 5,000 line file can be broken up into smaller files called modules, and this makes code easier to read, understand, and maintain. The browser can also use modules to load code dynamically, but this isn't supported in all browsers. So what we want, is a way to write code in several files, and then combine them all into one file. 

You need to have [node]() and [npm]() installed on your computer. Once you've done this you'll also need to install [browserify]() onto your computer. You can then do something like this:

```js
var unique = require('uniq');

var data = [1, 2, 2, 3, 4, 5, 5, 5, 6];

console.log(unique(data));
```
You are saying, in this file, that you want to require a module called `uniq`. This module is inside a folder in your project called `node_modules`. You could also use `require` to get any file you like. 

```js
var myModule = require('./myModule.js');
```
To get the `uniq` module installed you can use `npm`. 

Install the uniq module with npm:
```bash
npm install uniq
```

Now recursively bundle up all the required modules starting at index.js into a single file called bundle.js with the browserify command:
```bash
browserify index.js -o bundle.js
```
Browserify parses the AST for `require()` calls to traverse the entire dependency graph of your project. Now you can use the bunlde in your project instead of `index.js`.

```html
<script src="bundle.js"></script>
```