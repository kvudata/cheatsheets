---
title: ES2015+
category: JavaScript
layout: 2017/sheet
tags: [Featured]
updated: 2017-10-21
weight: -10
intro: |
  A quick overview of new JavaScript features in ES2015, ES2016, ES2017 and beyond.
---

### Block scoping

#### Let

```js
function fn () {
  let x = 0
  if (true) {
    let x = 1 // only inside this `if`
  }
}
```
{: data-line="2,4"}

#### Const

```js
const a = 1
```

`let` is the new `var`. Constants work just like `let`, but can't be reassigned.
See: [Let and const](http://babeljs.io/learn-es2015/#ecmascript-2015-features-let-const)

### Backtick strings

#### Interpolation

```js
var message = `Hello ${name}`
```

#### Multiline strings

```js
var str = `
hello
world
`
```

Templates and multiline strings.
See: [Template strings](http://babeljs.io/learn-es2015/#ecmascript-2015-features-template-strings)

### Binary and octal literals

```js
let bin = 0b1010010
let oct = 0o755
```

See: [Binary and octal literals](http://babeljs.io/learn-es2015/#ecmascript-2015-features-binary-and-octal-literals)

### New methods

#### New string methods

```js
"hello".repeat(3)
"hello".includes("ll")
"\u1E9B\u0323".normalize("NFC")
```

See: [New methods](http://babeljs.io/learn-es2015/#ecmascript-2015-features-math-number-string-object-apis)

### Classes

```js
class Circle extends Shape {
```

#### Constructor

```js
  constructor (radius) {
    this.radius = radius
  }
```
{: data-line="1"}

#### Methods

```js
  getArea () {
    return Math.PI * 2 * this.radius
  }
```
{: data-line="1"}

#### Calling superclass methods

```js
  expand (n) {
    return super.expand(n) * Math.PI
  }
```
{: data-line="2"}

#### Static methods

```js
  static createFromDiameter(diameter) {
    return new Circle(diameter / 2)
  }
}
```
{: data-line="1"}

Syntactic sugar for prototypes.
See: [Classes](http://babeljs.io/learn-es2015/#ecmascript-2015-features-classes)

### Exponent operator

```js
const byte = 2 ** 8
// Same as: Math.pow(2, 8)
```
{: data-line="1"}

Promises
--------
{: .-three-column}

### Making promises

```js
new Promise((resolve, reject) => {
  if (ok) { resolve(result) }
  else { reject(error) }
})
```
{: data-line="1"}

For asynchronous programming.
See: [Promises](http://babeljs.io/learn-es2015/#ecmascript-2015-features-promises)

### Using promises

```js
promise
  .then((result) => { ··· })
  .catch((error) => { ··· })
```
{: data-line="2,3"}

### Promise functions

```js
Promise.all(···)
Promise.race(···)
Promise.reject(···)
Promise.resolve(···)
```

### Async-await

```js
async function run () {
  const user = await getUser()
  const tweets = await getTweets(user)
  return [user, tweets]
}
```
{: data-line="2,3"}

`async` functions are another way of using functions.

See: [async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

Destructuring
-------------
{: .-three-column}

### Destructuring assignment

#### Arrays

```js
var [first, last] = ['Nikola', 'Tesla']
```
{: data-line="1"}

#### Objects

```js
let {title, author} = {
  title: 'The Silkworm',
  author: 'R. Galbraith'
}
```
{: data-line="1"}

Supports for matching arrays and objects.
See: [Destructuring](http://babeljs.io/learn-es2015/#ecmascript-2015-features-destructuring)

### Default values

```js
var scores = [22, 33]
var [math = 50, sci = 50, arts = 50] = scores
```

```js
// Result:
// math === 22, sci === 33, arts === 50
```

Default values can be assigned while destructuring arrays or objects.

### Function arguments

```js
function greet({ name, greeting }) {
  console.log(`${greeting}, ${name}!`)
}
```
{: data-line="1"}

```js
greet({ name: 'Larry', greeting: 'Ahoy' })
```

Destructuring of objects and arrays can be also be done in function arguments.

### Reassigning keys

```js
function printCoordinates({ left: x, top: y }) {
  console.log(`x: ${x}, y: ${y}`)
}
```
{: data-line="1"}

```js
printCoordinates({ left: 25, top: 90 })
```

This example assigns `x` to the value of the `left` key.

### Loops

```js
for (let {title, artist} in songs) {
  ···
}
```
{: data-line="1"}

The assignment expressions work in loops, too.

Spread
------

### Object spread

#### with Object spread

```js
const options = {
  ...defaults,
  visible: true
}
```
{: data-line="2"}

#### without Object spread

```js
const options = Object.assign(
  {}, defaults,
  { visible: true })
```

The Object spread operator lets you build new objects from other objects.

See: [Object spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

### Array spread

#### with Array spread

```js
const users = [
  ...admins,
  ...editors,
  'rstacruz'
]
```
{: data-line="2,3"}

#### without Array spread

```js
const users = admins
  .concat(editors)
  .concat([ 'rstacruz' ])
```

The spread operator lets you build new arrays in the same way.

See: [Spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

Functions
---------

### Function arguments

#### Default arguments

```js
function greet (name = 'Jerry') {
  return `Hello ${name}`
}
```
{: data-line="1"}

#### Rest arguments

```js
function fn(x, ...y) {
  // y is an Array
  return x * y.length
}
```
{: data-line="1"}

#### Spread

```js
fn(...[1, 2, 3])
// same as fn(1, 2, 3)
```
{: data-line="1"}

Default, rest, spread.
See: [Function arguments](http://babeljs.io/learn-es2015/#ecmascript-2015-features-default-rest-spread)

### Fat arrows

#### Fat arrows

```js
setTimeout(() => {
  ···
})
```
{: data-line="1"}

#### With arguments

```js
readFile('text.txt', (err, data) => {
  ...
})
```
{: data-line="1"}

#### Implicit return
```js
numbers.map(n => n * 2)
// No curly braces = implicit return
// Same as: numbers.map(function (n) { return n * 2 })
```
{: data-line="1"}

Like functions but with `this` preserved.
See: [Fat arrows](http://babeljs.io/learn-es2015/#ecmascript-2015-features-arrows-and-lexical-this)

Objects
-------

### Shorthand syntax

```js
module.exports = { hello, bye }
// Same as: module.exports = { hello: hello, bye: bye }
```

See: [Object literal enhancements](http://babeljs.io/docs/learn-es2015/#enhanced-object-literals)

### Methods

```js
const App = {
  start () {
    console.log('running')
  }
}
// Same as: App = { start: function () {···} }
```
{: data-line="2"}

See: [Object literal enhancements](http://babeljs.io/learn-es2015/#ecmascript-2015-features-enhanced-object-literals)

### Getters and setters

```js
const App = {
  get closed () {
    return this.status === 'closed'
  },
  set closed (value) {
    this.status = value ? 'closed' : 'open'
  }
}
```
{: data-line="2,5"}

See: [Object literal enhancements](http://babeljs.io/learn-es2015/#ecmascript-2015-features-enhanced-object-literals)

### Computed property names

```js
let event = 'click'
let handlers = {
  [`on${event}`]: true
}
// Same as: handlers = { 'onclick': true }
```
{: data-line="3"}

See: [Object literal enhancements](http://babeljs.io/learn-es2015/#ecmascript-2015-features-enhanced-object-literals)

Modules
-------

### Imports

```js
import 'helpers'
// aka: require('···')
```

```js
import Express from 'express'
// aka: Express = require('···').default || require('···')
```

```js
import { indent } from 'helpers'
// aka: indent = require('···').indent
```

```js
import * as Helpers from 'helpers'
// aka: Helpers = require('···')
```

```js
import { indentSpaces as indent } from 'helpers'
// aka: indent = require('···').indentSpaces
```

`import` is the new `require()`.
See: [Module imports](http://babeljs.io/learn-es2015/#ecmascript-2015-features-modules)

### Exports

```js
export default function () { ··· }
// aka: module.exports.default = ···
```

```js
export function mymethod () { ··· }
// aka: module.exports.mymethod = ···
```

```js
export const pi = 3.14159
// aka: module.exports.pi = ···
```

`export` is the new `module.exports`.
See: [Module exports](http://babeljs.io/learn-es2015/#ecmascript-2015-features-modules)

Generators
----------

### Generators

```js
function* idMaker () {
  var id = 0
  while (true) { yield id++ }
}
```

```js
var gen = idMaker()
gen.next().value  // → 0
gen.next().value  // → 1
gen.next().value  // → 2
```

It's complicated.
See: [Generators](http://babeljs.io/learn-es2015/#ecmascript-2015-features-generators)

### For..of iteration

```js
for (let i of iterable) {
  ···
}
```

For iterating through generators and arrays.
See: [For..of iteration](http://babeljs.io/learn-es2015/#ecmascript-2015-features-iterators-for-of)
