# THEORY

## 1. Common questions 

**JavaScript** 
- programming language that allows you to implement complex features on webpage
- is single-threaded language, which means it has only one call stack is used to execute program /**any given time Js can do only one operation**/

**Stack** - is the only thread of js-code execution. Functions calls are placed on the stack and runs in reverse oreder. 

**Heap** - memory allocation. 

**Browsers/Web APIs** - Application Programming Interface for the Web. All browsers have a set of built-in Web APIs to support complex operations, and to help accessing data.

For example, the Geolocation API can return the coordinates of where the browser is located.

For example:
```
setTimout()
setInterval()
```

**HTML** - (Hyper Text Markup Language) - markaup language that we use to structure our components. 

**CSS** - (Cascading Style Sheets) - is a language of style rules that we use to apply styling to our HTML content. 

**SPA** - Single Page Application - this is a web application or website that uses a **single HTML document as a wrapper for all web pages** and organizes user interaction through dynamically loaded `HTML`, `CSS`, `JavaScript`, usually via `AJAX`.

**React** - is a JS library that is used for building user interfaces specifically for single-page application. 

**Redux** - is a library used for ddata storage for any UI layout. 

- redux-thunk - middleware allows you to write action-creators that return a function instead of an action. Function takes the `dispatch` method as an argument, so that after the asynchonous operation has completed, use it to dispatch a normal synchonous action. 
- redux-saga - is a middleware-library that aims to make application side effects (asynchonous things like data fetching) - it is like a separate thread in your application that is solely responsible for side effects. 

**Jest** - library for unit-testing. In all projects where I participated, writing tests was required. So I wrote a lot of tests. 

**lifecycle methods** - can be ddefined as the series of methods that are involked in different stages of the components existanse.

**REST**

`REST` - Representatinal State Transfer - a set of rules that define how a programmer can organize the writing of a server-side web application code so that all systems can easily exchange data and the application can be scaled. 

`RESTful` - the service is written according to all REST rules - it is an application that provides a list of URLs with which the server can accept requests such as: GET, PUT, POST, DELETE or OPTIONS. Using the URL, the service understands which data to work with and which objects to get or update or delete.

**HTTP**

`HTTP` - agreement on the format of text files that go between the server and the client - this allows you to make requests through the browser and exchange information in the request body.

`HTTPS` - this is the same thing, but the information is encrypted. The site must receive an **SSL certificate**. 

`HTTP method` is **idempotent** if a repeated identical request has the same effect without changing the state of the server.

Idempotent mothods: GE, PUT, DELETE, OPTIONS
non-idempotent mothod: POST - a repeated call can, for example, place an order on the website 2 times. 

OPTIONS - description of connection parameters - we can find out which query methods the server supports. 

**CORS**

`CORS` - Cross-Origin Resource Sharing - a technology that **uses additional headers** to allow a user agent to get **permission to access resources from a server** on a domain other than what the site is currently using. 

### SOLID

`SOLID` - five design principles intended to make software designs more understandable, flexible, and maintainable. 

> **SOLID stands for:**
> - S - Single-responsiblity Principle
> - O - Open-closed Principle
> - L - Liskov Substitution Principle
> - I - Interface Segregation Principle
> - D - Dependency Inversion Principle 

1. **Single-responsiblity Principle**. 

> A class or function should have one and only one reason to change, meaning that a class should have only one job.

2. **Open-Closed Principle**. 

> Objects or entities should be open for extension but closed for modification. This means that a class should be extendable without modifying the class itself.

3. **Liskov Substitution Principle**. 

> It is necessary that subclasses could serve as a substitute for their superclasses.
> In other words, as simple as that, a subclass should override the parent class methods in a way that does not break functionality from a client’s point of view. 

4. **Interface Segregation Principle**

> We should create highly specialized interfaces designed for a specific client. Clients should not depend on interfaces that they do not use.

5. **Dependency Inversion Principle**

> The object of the dependency should be an abstraction, not something concrete. 
> In the process of software development, there is a moment when the functionality of the application ceases to fit within a single module. As a result, for example, it may turn out that high-level components depend on low-level components.

### Server Side Rendering [SSR]

**Server-side rendering (SSR) is the ability of a web application to render the web page on the server instead of rendering it in the browser.** When the page arrived on the client-side, it is fully rendered. It is because the server-side has fully rendered the page before it was sent by the server to the client.

Some server-side rendering **advantages** include:

- A server-side rendered application enables pages to **load faster**, improving the user experience.
- When rendering server-side, **search engines can easily index and crawl content** because the content can be rendered before the page is loaded, which is ideal for SEO. 
- Webpages are correctly indexed because web browsers prioritize web pages with faster load times.
- Rendering server-side helps efficiently load webpages for users **with slow internet connection or outdated devices**.

Server-side rendering **disadvantages** may include:

- Rendering server-side can be costly and resource-intensive as it is not the default for JavaScript websites, and **the server takes on the full burden of rendering content** for users and bots.
- While rendering static HTML server-side is efficient, **rendering bigger, more complex applications server-side can increase load times.** 
- Server-side rendering may not be compatible with third-party JavaScript code. 
- Rendering server-side may be ideal for static site generation, but frequent server requests and full page reloads can result in overall slower page rendering in more complex applications. 

### Client Side Rendering [CSR]

CSR is the opposite of SSR. If the SSR renders the page on the server-side, **CSR renders the page on the client-side**. 

When the request is received on the server, it will not render the page, instead, the server will send a single page that will be the skeleton of the page to the client. The server sends the page along with the javascript file. Later, the js will turn the page into a fully rendered page. If the page needs to take data, the client will make a request to the `API` to take the data and then render it to the page. Lastly, if the client navigates to a different route, the server will not send the page again, instead, the client will re-render the page according to the route that client requested. So the page that is used, is always the same page as the first request.

**advantages**

- ideal for Web apps
- fast rendering after initial load
- rich site interaction
- reduce server load

**disadvantages**

- Slover initial load time
- SEO is not priority
- Higher memory consumption

**The difference**

the main difference between `CSR` and `SSR` is where the page is rendered. SSR renders the page on the server-side and CSR renders the page on the client-side. **Client-side manages the routing dynamically without refreshing the page every time the client requests a different route.**

**use SSR**
- if SEO is your priority, typically when you are building a blog site and you want everyone who searching on google go to your website, then SSR is your choice.
- if your website needs a faster initial loading.
- if the content of your website doesn't need much user interaction.

**use CSR**

- when SEO is not your priority
- if your site has rich interactions
- if you are building a web application

### What is a static website?

A static website is made up of one or more HTML webpages that load the same way every time. Static websites contrast with dynamic websites, which load differently based on any number of changing data inputs, such as the user's location, the time of day, or user actions. While static webpages are simple HTML files that can load quickly, dynamic webpages require the execution of JavaScript code within the browser in order to render.

### AJAX - Asynchronous JavaScript And XML.

**AJAX allows web pages to be updated asynchronously by exchanging data with a web server behind the scenes**. This means that it is possible to update parts of a web page, without reloading the whole page.

Using AJAX you can:

- Read data from a web server - after the page has loaded
- Update a web page without reloading the page
- Send data to a web server - in the background

AJAX just uses a combination of:

- A browser built-in `XMLHttpRequest` object (to request data from a web server)
- JavaScript and HTML DOM (to display or use the data)

I guess, Almost no one uses XML data and Use the JSON data instead. 

`JSON` stands for JavaScript Object Notation. JSON is a text format for storing and transporting data. 

Modern Browsers can use Fetch API instead of the XMLHttpRequest Object. The Fetch API interface allows web browser to make HTTP requests to web servers.

**The Fetch API** interface allows web browser to make HTTP requests to web servers.












