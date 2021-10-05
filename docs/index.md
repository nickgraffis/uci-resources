# UC Irvine Fall 2021 Full Stack Web Development Bootcamp Resources
Here are some resources for your success and continued education. If you would like to add your own resources, you can fork this repository, and then under `uci-resources` > `docs` > `index.md`, add your own resources. Then create a pull request! [In depth contribution guide](/contributing).

Resources here are organized by categories that are ment to mimic the modules that your working on in class.

## :toolbox: Tools
### VSCode
* [Download/Docs VSCode for MacOS](https://code.visualstudio.com/docs/?dv=osx)
* [Download/Docs VSCode for Windows](https://code.visualstudio.com/docs/?dv=win)
* Emmit Cheatsheet :heart: :fire:: [link](https://docs.emmet.io/cheat-sheet/)
* [VS Code KeyBindings](https://code.visualstudio.com/docs/getstarted/keybindings)
* [VS Code KeyBindings for MacOS](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf)
  * Thanks Vahan! :tada:
* VS Code Package for previewing HTML, MD files: [link](https://marketplace.visualstudio.com/items?itemName=searKing.preview-vscode)
### Terminal Tools for MacOS
* [Download iTerm](https://iterm2.com)
* [Download OhMyZsh](https://ohmyz.sh)

### Design Tools
* [Figma](https://www.figma.com/)

### GitHub Pages
* [Using GitHub Pages](https://youtu.be/P4Mu1t5rIXg)

### GitLab
* [Create SSH Key](https://docs.gitlab.com/ee/ssh/#generate-an-ssh-key-pair)
* Keeping up with the latest class book:
  * [Video Guide](https://youtu.be/5gGuRWH3w-Q)
  * Go to Gitlab (https://uci.bootcampcontent.com/UCI-Coding-Bootcamp/uci-irv-virt-fsf-pt-09-2021-u-c/-/tree/master). Then copy the SSH url.
  * Navigate into a good location in your computer:
  * `cd Desktop && mkdir bootcamp && cd bootcamp`
  * Clone the repo & navigate to it:
    * `git clone git@uci.bootcampcontent.com:UCI-Coding-Bootcamp/uci-irv-virt-fsf-pt-09-2021-u-c.git && cd uci-irv-virt-fsf-pt-09-2021-u-c`
  * You now have access to the class repository!
  * When you want to get the latest updates to the class repository:
    * `git pull` 

### Random Tools
* [Jeff Goldblum's Lorem Ipsum :wink:](http://jeffsum.com)

## The Terminal & Commandline
* [Commandline Tools](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Understanding_client-side_tools/Command_line#basic_built-in_terminal_commands)

## :space_invader: GIT
* Some extra reading thanks to [stackoverflow](https://stackoverflow.com), on how to *uncommit* your git commits: [link](https://stackoverflow.com/questions/2845731/how-to-uncommit-my-last-commit-in-git/13480388#13480388).

## :memo: HTML
### :framed_picture: Images
* Easy placeholder images [here](https://placeholder.com).
* Random, high res, images from unsplash with [https://source.unsplash.com/random](https://source.unsplash.com/random).
### Semantic HTML
* A great link, thanks to [W3 School](https://www.w3schools.com), [HTML5 Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)
* The difference between `strong` and `bold`: [link](https://www.geeksforgeeks.org/difference-between-strong-and-bold-tag-in-html/)
### :art: Colors
* [Why do we use hexidecimal in colors?](https://medium.com/@savas/why-do-we-use-hexadecimal-d6d80b56f026)
### Typography
* [Google Fonts](https://fonts.google.com/)
* [The importance of Typogoraphy](https://medium.com/free-code-camp/typography-can-make-your-design-or-break-it-7be710aadcfe)
* [History of Sans Serif](https://www.typotheque.com/articles/a_brief_history_of_sans_serif_typefaces)

## CSS
* `font-weight`: [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight)
* `position`: [W3Schools](https://www.w3schools.com/cssref/pr_class_position.asp)
* `position`: [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
  * Check out `position: sticky` for futher reading!

### Units
* [W3 Units Converter](https://www.w3schools.com/cssref/css_units.asp)
### Flexbox
* [Awesome Video from Wes Bos!](https://www.youtube.com/watch?v=CFgeJq4l1YM&ab_channel=WesBos)
  * Thanks Awad! :tada:
* :frog: [Flexbox Froggy!](https://flexboxfroggy.com/)
* [A flexbox playground](https://nickgraffis.github.io/flex-box-demo/)

### Box Shadow
* [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow)
* :test_tube: [The perfect box shadow](https://tobiasahlin.com/blog/layered-smooth-box-shadows/)

### Attribute Selectors
* [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)
  * Thanks Runa! :tada:
```css
a[href$=".css"]::after {
  content: "👨‍✈️";
}

ul li:nth-child(2) a[href$=".css"]::after {
  content: "👨‍✈️";
}

ul li:nth-child(3) a[href$=".css"]::after {
  content: "🧑‍🚀";
}
```

### Pseudo-Classes/Elements
* [Hover Pseudo-Class for Pseudo Elements](http://jsfiddle.net/5WV75/)

### Border Radius
```css
/* The syntax of the first radius allows one to four values */
/* Radius is set for all 4 sides */
border-radius: 10px;

/* top-left-and-bottom-right | top-right-and-bottom-left */
border-radius: 10px 5%;

/* top-left | top-right-and-bottom-left | bottom-right */
border-radius: 2px 4px 2px;

/* top-left | top-right | bottom-right | bottom-left */
border-radius: 1px 0 3px 4px;

/* The syntax of the second radius allows one to four values */
/* (first radius values) / radius */
border-radius: 10px / 20px;

/* (first radius values) / top-left-and-bottom-right | top-right-and-bottom-left */
border-radius: 10px 5% / 20px 30px;

/* (first radius values) / top-left | top-right-and-bottom-left | bottom-right */
border-radius: 10px 5px 2em / 20px 25px 30%;

/* (first radius values) / top-left | top-right | bottom-right | bottom-left */
border-radius: 10px 5% / 20px 25em 30px 35em;

/* Global values */
border-radius: inherit;
border-radius: initial;
border-radius: revert;
border-radius: unset;
```

### CSS Art
* [Simpsons](https://pattle.github.io/simpsons-in-css/)
* [CSS Art Challenge](https://alvaromontoro.com/blog/67936/100-days-of-css-illustrations)
* :jack_o_lantern: [Nick's Pumpkin](https://codepen.io/nickgraffis/pen/OJXvRyJ)

## Useful HotKeys/CLI Commands
* `F12`: Open Chrome DevTools (PC)
* `Option + ⌘ + J`: Open Chrome DevTools (Mac)
* `cat ~/.ssh/id_rsa.pub | pbcopy`: Copy your SSH key to your clipboard (Mac)
* `clip < ~/.ssh/id_rsa.pub`: Copy your SSH key to your clipboard (PC)

## JavaScript
* Generate a random whole number
```javascript
Math.floor(Math.random() * 10)
```
* [Quara Answer](https://www.quora.com/What-is-the-difference-between-an-operator-and-a-function) - Difference between operators and functions, according to math
* [JS Operators](https://www.w3schools.com/jsref/jsref_operators.asp)
* Super deep dive into operators like (+) and how a computer actually adds two numbers together: [JSFiddle](https://jsfiddle.net/L8muvg7r/28/)
* JS Basics from MDN:
  * [Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
  * [Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)
  * [Objects Part 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
  * [Objects Part 2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
  * [Strings]( https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_methods)
  * Thanks Andy! :tada:
* JS Window Object from MDN:
  * [Window.prompt](https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt)
  * [Window.confrim](https://developer.mozilla.org/en-US/docs/Web/API/Window/confirm)
  * [Window.alert](https://developer.mozilla.org/en-US/docs/Web/API/Window/alert)