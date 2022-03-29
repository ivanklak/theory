# Questions

## Semantic HTML

what does it mean? semantic tags?

## What does a DOCTYPE do?

`DOCTYPE` is an abbreviation for **Document Type**. 

For webpages, the `DOCTYPE` declaration is required. It is used to tell user agents what version of the HTML specifications your document respects. Once a user agent has recognized a correct DOCTYPE, it will trigger the **no-quirks mode** matching this DOCTYPE for reading the document. If a user agent doesn't recognize a correct DOCTYPE, it will trigger the **quirks mode**.

The DOCTYPE declaration for the HTML5 standards is `<!DOCTYPE html>`.

## How do you serve a page with content in multiple languages?

When an HTTP request is made to a server, the requesting user agent usually sends information about **language preferences**, such as in the `Accept-Language` header. The server can then use this information to return a version of the document in the appropriate language if such an alternative is available. The returned HTML document should also declare the `lang` attribute in the `<html>` tag, such as `<html lang="en">...</html>`.

## What kind of things must you be wary of when designing or developing for multilingual sites?

- Use lang attribute in your HTML.
- Directing users to their native language - Allow a user to change his country/language easily without hassle.
- Formatting dates and currencies - Calendar dates are sometimes presented in different ways.
- Language reading direction - In English, we read from left-to-right, top-to-bottom, in traditional Japanese, text is read up-to-down, right-to-left.

## What are `data-` attributes good for?

- Earlier frontend developers used `data-` attributes to store extra data within the DOM itself. 
- For testing: data-testid

Что делать сначала, когда только начинаешь новый проект?
- prepare some basic layout, just a tamblate for HTML file 
- what kind of sections and other information I would like to put on the webpage
- start create div and containers to see how the layout will look like
- build it from the top to bottom, If I would scroll down the page I would see what I wanna see next and probably working on that things 


