# Basics

## Types

1. `numbers` - Regular numbers and floating point numbers, infinity, NaN (error calculation result). 
2. `strings` - senquence on characters in quotes. Strings can be joined with "+". 
3. `boolean` - two reserved words for booleans: `true` or `false`. 
4. `null` - is a special value that indicates the absence of a value. 
5. `undefined` - indicates that a variable has not been initialized and the value is absent. 
6. `object types` - anything that is not a primitive types is an object type. `Functions`, `array`s and what wa call `objects` ara object types.
7. `bigInt` - JS addded this method to work with integers of arbitrary length. At the end of the number, put the "n" letter. 
8. `symbol` - Symbol is a primitive type for unique identifiers. Symbols are created with `Symbol()` call with an optional description (name). Symbols are always different values, even if they have the same name.

**Type Conversions**

`False` values: '', 0, null, undefined, Nan, false

**`==` vs `===`**

`==` - non-strict equality operator, with type conversion. This means `2 == '2'` id `true`, and `undefined == null` is `true`, `'0' == false` is `true`

`===` - strict equality operator whitch return `true` when the two operands are having the same value without any type conversion. This means `2 === '2'` is `false` and `undefined === null` is `false`

## Values

The `scope` is a portion of code whre the variable is vasible. 

**var**
`var` - traditionaly, used before ES6

A variable initialized with `var` outside of any function is assigned to the global object (window, document), has `global scope` and is visible everywhere. 

A variable initialized with `var` inside of any function is assigned to that function, it is `local` and is visible only insidde it. 

**let**

`let` - it is essentially a `block scoped` version of `var` and can be changed later (mutable). Its scope is limited to the block, statament, expression where its defined. 

Definig `let` outside of any function - does not create a global variable. 


**const**

`const` - immutable. A once a `const` is initialized, its value can never be changed again (that work only for primitive types, we can change fields in arrays and in objects). Has a block scope. 

**Copy and change values**

```js
let a = 42
let b = a
b++

console.log(a) // a = 42
console.log(b) // b = 43
```

Copy `arrays`

```js
let a = [1, 2, 3]
let b = a

b.push(4)

console.log(a) // [1, 2, 3, 4]
console.log(b) // [1, 2, 3, 4]
console.log(a === b) // true
```

`b` copied the array by reference, so both variables change. 

In order not to change the array `a`, you can add:

```js
let c = a.concat()
console.log(a === c) // false
```

Copy `Objects` 

`bb` copied the object `aa` by reference, so both variables change. 

In order not to change the object `aa`, you can add `Object.assign({}, aa)`;

```js
const aa = {k: 1, c: 0};
const bb = aa;
const cc = Object.assign({}, aa);

bb["k"] = 2;

console.log(aa);           // { k: 2, c: 0 }
console.log(bb);           // { k: 2, c: 0 }
console.log(aa === bb);    //true
console.log(cc);           // {k: 1, c: 0}
console.log(cc === aa);    // false
```

**Operators**

`spred` and `rest` operators - these operators transmit their fields - different scope of application

- spred - `(...array)` ; `({...obj})`
- rest - `(a, b, ...rest)`

## Objects

- is an entity tht has its own `state` (valiables) and `behavior` (methods). 

**this** - to access information inside an object, the method can use `this` keyword. `this` - is a reference to the some object. 

**constructors** - a set of objects of the same type, that are created using `new` operator. `Constuructor` - it is a function that can takes some parameters. 

```js 
function Auto(name, model) {
  this.name = name;
  this.model = model;
}

let auto = new Auto('BMW', 'x3');

console.log(auto.name + auto.model); // BMW x3
```

**Prototypal inheritance**

- Each object has its own prototype, which is taken from the parent element. To get the parent prototype, the `__proto__` keyword is used. 

`__proto__` - this keyword **indicates the prototype of the parent class or object** from which the object was created. 

> If we refer to the property of an object, it first looks at whether the object itself has such a property, and then looks at the prototype.

- the `prototype` property of functions is used **to pass properties for objects** (for expamle, that are created through the new operator).

```js
function Cat(name, color) {
  this.name = name;
  this.color = color;
}

Cat.prototype.voice = function() {
  console.log(`Cat ${this.name} says myau`)
}

const cat = new Cat('Tom', 'blue');

cat.voice() // 'Cat Tom says myau'
```
that is, we are extending the prototype of the parent class. 

This is necessary, for example, not to import a function or object, but to immediately call the desired method.

## Classes

is an extensible code template for creating objects that sets their initial values(properties) and behavior implementation(methods).  

A `class` can extend another class of object, and **inherit** all methods of both classes. If the inherited class has a method with the same name, the closest method takes precedence. 

Inside the children class ypu can reference the parent class calling `super()`

```js
class Programmer extends Preson {
  hello() {
    return super.hello() + 'I am programmer'
  }
}

const ivan = new Programmer('Ivan')

console.log(ivan.hello()); // "Hi am Ivan. I am programmer" 

//"Hi am Ivan" - from parent class
```

## Functions

everything in JavaScript happens in functions. 

`function` is a block of code, self contained, that can be defined once and run any times you want. 

Functions in JS are onjects, a special kind of objects - **functional objects**. 

**Functional expression**

```js
const square = function (num) {
  return num * 2;
}
```

**Named function expressions**

```js
const square = function bar(num) {
  return num * 2;
}

square() // working
bar() // Error
```

Why we use named function expressions:

- You can use the name of that function when you need **recursion**.
- Anonymous functions doesn't help when **debugging** as you can't see the name of the function that causes problems.
- When you do not name a function, later on **its harder to understand what it's doing**. Giving it a name makes it easier to understand.

**Functional decloration**

```js
function square(num) {
  return num * 2;
}
```

**Errow Functions**

were introduced in ES6/ES2015, which are especially nice to use when working with inline functions, as parameters or callbacks

```js
const square = (num) => {
  return num * 2;
}
```

## Hoisting

- work of interpreter - all functions are moved to the beginning of the file, so you can call the function before it is defined. 

`var`

```js
console.log(i);
var i = 42;
console.log(i)

//output
undefined
42
```

Variables `let` and `const` dont supported Hoisting. 

```js
console.log(num);
const num = 42;
console.log(num)

//output
ReferenceError
```

## Closures

- a function having access to the parent scope, even after the parent function has closed

The `scope` basically is the set of variables which are visible.

For exapmle: we have a function with its own variable `fw` inside. And this function return an object with two methods, that use parent variable. 
`fw` is a private variable. We cant get it outside this parent function, but we can interact with variable inside. 

```js 
function createFramework() {
  const fw = ['Angular', 'React'];
  
  return {
      print: function() {
          console.log(fw);
      },
      add: function(framework) {
          fw.push(framework);
      }
  }
}

const manager = createFramework();

manager.print(); // ['Angular', 'React']
manager.add('VueJS');

manager.print(); // ['Angular', 'React', 'VueJS']
```








