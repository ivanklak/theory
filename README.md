# THEORY

## 1. Common questions 

**JavaScript** 
- programming language that allows you to implement complex features on webpage
- is single-threaded language, which means it has only one call stack is used to execute program /**any given time Js can do only one operation**/

**Stack** - is the only thread of js-code execution. Functions calls are placed on the stack and runs in reverse oreder. 

**Heap** - memory allocation. 

**Browsers/Web API`s** - API to support complex operations, and to help accessing data

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







