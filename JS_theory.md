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



