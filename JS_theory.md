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

**Question**

What's the difference between a variable that is: null, undefined or undeclared?

> **Undeclared variables** are created when you assign a value to an identifier that is not previously created using `var`, `let` or `const`. Undeclared variables will be defined globally, outside of the current scope.

```js
function foo() {
  x = 1; // Throws a ReferenceError in strict mode
}

foo();
console.log(x); // 1
```

> A variable that is `undefined` is a variable that **has been declared, but not assigned a value**. It is of type `undefined`. If a function does not return any value as the result of executing it is assigned to a variable, the variable also has the value of `undefined`.

```js
var foo;
console.log(foo); // undefined
console.log(foo === undefined); // true
console.log(typeof foo === 'undefined'); // true
```

> A variable that is `null` will have been explicitly assigned to the `null` value. It represents **no value** and is different from `undefined` in the sense that **it has been explicitly assigned**. 

```js
var foo = null;
console.log(foo === null); // true
console.log(typeof foo === 'object'); // true
```

**Type Conversions** - JavaScript variables can be converted to a new variable and another data type. 

The global method `Number()` can convert strings to numbers.

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

**this** - to access information inside an object, the method can use `this` keyword. `this` - is a reference to the some object and depends on how the function is called: 

- If the `new` keyword is used when calling the function, `this` inside the function [constructor] is **a brand new object**.
- If `apply`, `call`, or `bind` are used to call/create a function [involke function with Context], `this` inside the function is **the object that is passed in as the argument**.
- If arrow function uses as a object method, `this` is the **global object**. In a browser, it is the `window` object.
- If the function is an **arrow function**, it receives the `this` value of its surrounding scope at the time it is created.

**constructors** - a set of objects of the same type, that are created using `new` operator. `Constuructor` - it is a function that can takes some parameters. 

```js 
function Auto(name, model) {
  this.name = name;
  this.model = model;
}

let auto = new Auto('BMW', 'x3');

console.log(auto.name + auto.model); // BMW x3
```

## Prototypal inheritance

- Each object has its own prototype, which is taken from the parent element. To get the parent prototype, the `__proto__` keyword is used. 

`__proto__` - this keyword **indicates the prototype of the parent class or object** from which the object was created. 

> When a property is accessed on an object and **if the property is not found on that object**, the JavaScript engine looks at the object's `__proto__`, and the `__proto__`'s `__proto__` and so on, until it finds the property defined on one of the` __proto__`s or until it reaches the end of the prototype chain.

```js
function Parent() {
  this.name = 'Parent';
}

Parent.prototype.greet = function () {
  console.log('Hello from ' + this.name);
};

const child = Object.create(Parent.prototype);

child.cry = function () {
  console.log('waaaaaahhhh!');
};

child.cry();
// waaaaaahhhh!

child.greet();
// hello from Parent

child.constructor;
// ƒ Parent() {
//   this.name = 'Parent';
// }

child.constructor.name;
// 'Parent'
```

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
that is, we are **extending the prototype of the parent class**. 

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

**Question**

What's a typical use case for anonymous functions?

> - They can be used in `IIFEs` to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope. `(function () {})();`
> - As a callback that is used once and does not need to be used anywhere else. `setTimeout(function () {}, 0)`
> - Arguments to functional programming constructs. `arr.map(() => {})`


## Hoisting

- work of interpreter - all functions are moved up to the top of their module/function-level scope, so you can call the function before it is defined. 

`var`

```js
console.log(i);
var i = 42;
console.log(i)

//output
undefined
42
```

Variables declared via `let` and `const` are hoisted as well. But they are not initialized and accessing them before the declaration will result in a `ReferenceError` exception. [Variables `let` and `const` dont supported Hoisting].

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

## IIFE
**Immediate Involked Function Expression**

- is a JavaScript function that runs as soon as it is defined. - often to create a local scope

It is a design pattern which is also known as a **Self-Executing Anonymous Function** and contains two major parts:

- The first is the **anonymous function** with lexical scope enclosed within the Grouping Operator (). Due to this, IIFE variables are closed inside it, and the global scope is not clogged with them.
- The second part creates the **immediately invoked function expression ()** through which the JavaScript engine will directly interpret the function.

The variable to which `IIFE` is assigned, stores the result of the function execution, but not the function itself:

```js
var result = (function () {
    var name = "Barry";
    return name;
})();
// Immediately creates the output:
result; // "Barry"
```

```js
for (var i = 0; i < 5; i++) {
  (function() {
    var j = i;
    result.push( function() {console.log(j)} )
  })()
}

result[2](); //2
result[4](); //4
```

**Question**

Explain why the following doesn't work as an IIFE: `function foo(){ }()`

> 1. Statements that begin with function are considered to be **function declarations**; by wrapping this function within `()`, it becomes a **function expression** which can then be executed with the subsequent `()`. And these functions are not exposed in the global scope. 

```js
(function foo(){ })() // - function expression
```

> 2. You might also use `void` operator: `void function foo(){ }();`. Unfortunately, there is one issue with such approach. The evaluation of given expression is always `undefined`, so if your IIFE function returns anything, you can't use it. 

## Context

`Context` in JavaScript is related to objects. It refers to the object within the function being executed. `this` refers to the object that the function is executing in.

```js
const person = {
  surname: 'Stark',
  knows: function(what, name) {
    console.log(`You know ${what}, ${name} ${this.surname}`)
  }
}
person.knows('everything', 'Bran'); // You know everything, Bran Stark

const john = {surname: 'Snow'};
person.knows.call(john, 'nothing', 'John'); // You know nothing, John Snow
```

We call the `knows` function in the context of `john`

**Methods**

- `call(context, param1, param2)` - calls the function immediately. 
- `apply(context, [param1, param2])` - call the function immediately. 
- `bind(context, param1, param2)` - return a new function: 

```js
const blach = person.kwows.bind(john, 'nothing', 'John');

blach();
```

**Context In Classes transmited using `new` operator**

**Errow functions**

- don't create a new context, but refers to the endclosing function context, which in some cases might be a `window` object. 

`this` in the function expression refers to parent scope, looking for variables. 

```js
const car = {
  brand: 'Ford';
  model: 'Fiesta';
  start: functon() {
    console.log(`Started ${this.brand} ${this.model}`)
  },
  stop: () => {
    console.log(`Stopped ${this.brand} ${this.model}`)
  }
}

car.start(); // Started Ford Fiesta
car.stop(); // Stopped Undefined undefined
```
**Arrow functions are not suitable to be used for object methods and contructors**

## Event Loop

It solves one main problem: 

The event loop continuosly checks tha call stack to see, if there is any function that needs to run. While doing so, it adds any function call, it finds, to the call stack, and executes each one in order. 

```js 
console.log('1');
setTimeout( () => console.log('2'), 100); 
console.log('3');

// Output: 1 3 2
```

![5c5b41e37c793ce1fad4f342257bbede](https://user-images.githubusercontent.com/57959373/159160191-4d1be6fa-0a94-4384-b80c-3299922ea603.gif)

`setTimeout` - JS does not know how to work with it, so it gives the execution of this function to a `third-party API` (Web Api)  and cleans the call stack. 

The function passed to `setTimeout` gets into the `Callback Queue` and then gets into the `Call Stack`

**Microtasks and Macrotasks**

`Microtasks` come solely from our code. They are usually created by promises: an execution of `.then/catch/finally` handler becomes a microtask.

`Macrotasks` include keyboard events, mouse events, timer events, network events, Html parsing. 

Separation of macro and microtask enables the event loop **to prioritize types of tasks**; for example, giving priority to performance-sensitive tasks.

Immediately after every `macrotask`, the engine executes **all** tasks from `microtask queue`, prior to running any other macrotasks or rendering or anything else.

A more detailed event loop algorithm:

1. Dequeue and run the oldest task from the `macrotask queue` (e.g. “script”)
2. Execute all microtasks:
- While the `microtask` queue is not empty: Dequeue and run the oldest `microtask`.
3. Render changes if any.
4. If the `macrotask queue` is empty, wait till a macrotask appears.
5. Go to step 1.

`macrotasks`: setTimeout, setInterval, setImmediate, requestAnimationFrame, I/O, UI rendering

`microtasks`: process.nextTick, Promises, queueMicrotask, MutationObserver

## Event delegation

The idea is that if we have **a lot of elements** handled in a similar way, then instead of assigning a handler to each of them – we put a **single handler** on their common ancestor.

> Lets say we have a table with 99 cells. And our task is to highlight a cell `<td>` on click. Instead of assign an onclick handler to each `<td>` – we’ll setup the “catch-all” handler on `<table>` element. It will use `event.target` to get the clicked element and highlight it.

## Describe event bubbling.

Event bubbling is the mechanism behind **event delegation.**
When an event triggers on a DOM element, it will attempt to handle the event if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. This bubbling occurs up the element's ancestors all the way to the document. 

## Promises

- it is a special object in JavaScript that has three states: `pending`, `resolve`, `reject`. 

How promises work:
1. Once a `promise` has been called, it will start in **pending state**. This mean that the caller function continues the execution, while waits some feedback from `promise`. 
2. At this point the caller function waits for it yo either return the promise in a resolved state or in a rejected state. 

To create Promise: `new Promise()`

```js 
const isMomHappy = true;

const willIGetNewPhone = new Promise(
  function(resolve, reject) {
    if (isMomHappy) {
      const phone = {brand: 'APPLE', color: 'black'}
      resolve(phone);
    } else {
      const reason = new Error('mom has a bad mood')
      reject(reason);
    }
  }
)
```

Involke `promise`:

```js
 const askMom = function() {
  willIGetNewPhone
         .then((phone) => {
           console.log(phone);
         })
         .catch((error) => {
           console.log(error.message);
         })
 }
 
 askMom(); 
```
Promises are asynchonous: 

```js
console.log(1);
const promise = new Promise((resolve) => {
     console.log(3);
     setTimeout(() => console.log(2), 5000);
     throw new Error("Ups...");
     resolve();
 });
 promise.then(() => console.log(4));
 // promise.catch(() => console.log(5));
 console.log(7);
     const p = promise.catch(() => console.log(5));
     p.then(() => console.log('then'));
     p.catch(() => console.log('catch'));
 setTimeout(() => console.log(6), 2000);

// 1, 3, 7, 5, 'then', Error, 6, 2
```

It is because JS waits no one. 

Anything that needs to be executed after the promise must be inserted into `promise.then()`

## Async / await

JavaScript ES8 introduced the `async/await` construct, which simplifies working with promises.

**Asynchronous functions are declared using the `async` keyword.** Such a function returns an **AsyncFunction** object. This object is an asynchronous function that executes the code inside it. 

When an asynchronous function is called, it returns a `Promise` object.

**`await` suspends the execution of the function and waits for the promise to be resolved.** After that, the execution of the async function continues, and, for example, the value received after the promise resolution is returned.

```js
async function f() {
  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve('okay'), 1000)
  })
  let result = await promise;
  
  console.log(result);
}

f();
```







