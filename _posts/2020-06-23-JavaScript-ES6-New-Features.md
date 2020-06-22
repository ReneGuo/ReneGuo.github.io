\---

layout: post

title: JavaScript ES6 New Features

subtitle: What We Did and What We Do Now

date: 2020-06-23

author: Rene

header-img: img/post-bg-JavaScript.jpg

catalog: true

tags:

\- React

\- JavaScript

\- ES6

\---

## JavaScript ES6 New Features

### Declaration of Variables and Constance

> Support for constants (also known as "immutable variables"), i.e., variables which cannot be re-assigned new content. Notice: this only makes the variable itself immutable, not its assigned content (for instance, in case the content is an object, this means the object itself can still be altered). ([ES6 New Features](http://es6-features.org/#Constants))

#### Const

```javascript
// Declare a variable in ES5
var name = 'Rene';
```

```javascript
// What we can do now in ES6!

// Having a constance whose value can not be changed. Just like JAVA!
const PI = 3.14;
```



#### Var

In ES6, `let` and `var` are both variables declaration in javascript but the difference between them is that `var` is **function scoped** and `let` is **block scoped**, which means `var` declares variables can be used through out the function however `let` declares variables can be used only inside a block, such as a loop.

```javascript
// Scope
function test() {
  var foo = "Foo";
  let bar = "Bar";
  console.log(foo, bar);
  
  {
    var baz = "Baz"
    let qux = "Qux";
    console.log(baz, qux);
  }
  
	console.log(baz)
  console.log(qux); // ReferenceError
}
```

And `var` is **hoisted**, which means that the variable can be accessed even before its declaration(or you can assume it as it is always declared as **undefined** at the top of the program). While variables declared with `var` keyword are hoisted, `let` is declared precisely where the declaration sits.

```javascript
console.log(name) // Undifined
var name = "Rene";
console.log(name) // Rene
```

```javascript
console.log(name) // RefferenceError
let name = "Rene";
console.log(name) // Rene
```



### Arrow Function

ES6 introduces a new way to declare a function, Arrow Function. In traditional syntax `Function`, `this` is not always referencing to expected place like Java, while using arrow functions, there is no long problems with `this` in JavaScript. You can use it as in Java!

```javascript
// In ES5 a typical function
function add(a, b) {
  return a + b;
}

// Instead, an arrow function in ES6
const add = (a, b) => {  // a and b are parameters passing into the function
  return a + b;
}

// Or shorter as
const add = (a, b) => return a + b;

```



### Modules

`import` & `export` can link multiple files like HTML to establish dependencies. Assume we have three JavaScrip files, two of them are dependencies of the *app.js*, which is the main application. We can manage dependencies like below:

```javascript
// name.js

const name = {
	firstName = "Rene"
	lastName = "Guo"
}

export default name // default export, disregard to the name of import 
```

```javascript
// utility.js

const PI = 3.14;

const resetName = () => {
	name.firstName = "";
	name.lastName = "";
}

export PI;
export resetName;
```

```javascript
// app.js

import name from './name.js' // or import n from './name.js'
import {PI, resetName} from "./utility.js"
```

If using `export default`, the variable name of `import blabla from name.js` does not matter anymore(doesn't need to match to the variable or constance name in *name.js*), since it will always export the default variable `name`.



To be continued...