## Explain what a `single page app` is and how to make one SEO-friendly.

Traditionally, the browser receives HTML from the server and renders it. When the user navigates to another URL, a full-page refresh is required and the server sends fresh new HTML to the new page. This is called **server-side rendering**.

However, in modern SPAs, `client-side rendering` is used instead. **The browser loads the initial page from the server, along with the scripts (frameworks, libraries, app code) and stylesheets required for the whole app.** When the user navigates to other pages, a page refresh is not triggered. The URL of the page is updated via the `HTML5 History API`. New data required for the new page, usually in `JSON` format, is retrieved by the browser via `AJAX` requests to the server. The SPA then dynamically updates the page with the data via JavaScript, which it has already downloaded in the initial page load. This model is similar to how native mobile apps work.

**The benefits:**

- The app feels more responsive and users do **not see the flash between page navigations** due to full-page refreshes.
- Fewer HTTP requests are made to the server, as the same assets do not have to be downloaded again for each page load.
- Clear separation of the concerns between the client and the server; you can easily build new clients for different platforms (e.g. mobile, chatbots) without having to modify the server code. You can also modify the technology stack on the client and server independently, as long as the API contract is not broken.

**The downsides:**

- **Heavier initial page load** due to the loading of framework, app code, and assets required for multiple pages.
- There's an additional step to be done on your server which is to configure it to route all requests to a single entry point and allow client-side routing to take over from there.
- SPAs are reliant on JavaScript to render content, but **not all search engines execute JavaScript during crawling, and they may see empty content on your page.** This inadvertently hurts the Search Engine Optimization (SEO) of your app. However, most of the time, when you are building apps, SEO is not the most important factor, as not all the content needs to be indexable by search engines. **To overcome this, you can either server-side render your app or use services such as `Prerender` to "render your javascript in a browser, save the static HTML, and return that to the crawlers".**


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

## What is "use strict";? What are the advantages and disadvantages to using it?​

`use strict` is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt into a restricted variant of JavaScript.

**Advantages:**

- Makes it impossible to accidentally create global variables.
- Makes assignments which would otherwise silently fail to throw an exception.
- Makes attempts to delete undeletable properties throw (where before the attempt would simply have no effect).
- Requires that function parameter names be unique.
- `this` is undefined in the global context.
- It catches some common coding bloopers, throwing exceptions.
- It disables features that are confusing or poorly thought out.

**Disadvantages:**

- Many missing features that some developers might be used to.
- No more access to function.caller and function.arguments.
- Concatenation of scripts written in different strict modes might cause issues.

## Create a for loop that iterates up to 100 ... - FizzBuzz

```js
for (let i = 1; i <= 100; i++) {
  let f = i % 3 == 0,
    b = i % 5 == 0;
  console.log(f ? (b ? 'FizzBuzz' : 'Fizz') : b ? 'Buzz' : i);
}
```

## Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?​

Every script has access to the **global scope**, and if everyone uses the global namespace to define their variables, collisions will likely occur. Use the module pattern (IIFEs) to encapsulate your variables within a local namespace.


