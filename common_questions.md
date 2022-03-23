## What's the difference between host objects and native objects?​

**Native objects** are objects that are part of the JavaScript language defined by the ECMAScript specification, such as `String`, `Math`, `RegExp`, `Object`, `Function`, etc.

**Host objects** are provided by the runtime environment (browser or Node), such as `window`, `XMLHTTPRequest`, etc.

## What's the difference between an "attribute" and a "property"?

**Attributes** are defined on the HTML markup but **properties** are defined on the DOM. 

To illustrate the difference, imagine we have this text field in our HTML: `<input type="text" value="Hello">`.

```js
const input = document.querySelector('input');
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello
```

But after you change the value of the text field by adding "World!" to it, this becomes:

```js
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello World!
```

## 
