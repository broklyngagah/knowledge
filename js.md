# js
JavaScript, JS, twerkScript, ECMAscript, call it whatever you want. Here are
some neat party tricks you can perform at (including, but not limited to)
birthdays, job interviews and cat cafes.

## Function identifying with ES6 symbols
Checking if functions / objects are equal in JS is typically done with the
`===` operator. This checks if both functions point to the same location in
memory, and then returns a Boolean. In cases where you want to check if a
function or object is of a certain type (e.g. generated by a factory), you're
going to have a hard time. 

What you would want to do is attach a flag to the object to mark it as being a
certain type. Luckily with ES6 you can attach unique, enumerable flags (which 
means they don't show up when iterating over the keys) by using ES6 symbols.

Here's an example:
```js
const sym = Symbol('my unique string')

function generate () {
  const obj = {foo: 'bar'}
  obj[sym] = true
  return obj
}

const nw = generate()
const ot = generate()

nw === ot           // => false
nw[sym]             // => true

// don't ever do this, as if both values
// are undefined, it will also return true
nw[sym] === ot[sym]
```

## Only execute function if it exists
Cute little trick to only execute functions if they exist. Removes the need for
noop functions.
```js
function myFunc (fn) {
  fn && fn()
}
```

## Common module signatures
In order to form plug-and-play systems with swappable components it is key that
module signatures remain the same between modules. In staticly typed languages
it is possible to statically define the signatures for the modules, but this
doesn't work for js. In order to scratch that itch, the level community wrote
`abstract-leveldown`: a set of tests that can be used by implementers to enforce
an interface. So far it seems to succeed in it's goal, spreading to other
projects. Known projects to use this pattern are:
- [abstract-leveldown](https://www.npmjs.com/package/abstract-leveldown)
- [abstract-blob-store](https://github.com/maxogden/abstract-blob-store)

## See Also
- [ES6 compat table](https://kangax.github.io/compat-table/es6/) - caniuse for js
