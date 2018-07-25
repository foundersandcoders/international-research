# Engineering

### By Ben, Ryan and Suha (FACN4)

#### 23/07/2018

---

# Modules

---

### What is a module?

A cluster of code. There are three type:

1.  Modules which come pre-installed with Node.js (example: 'path', 'fs')
2.  Modules install with NPM. (example: 'tape', 'istanbul', 'prettier')
3.  Self made modules.. using 'module.export' to create the module and 'require' and import the module to the required page.

---

### What is Modularising?

Seperating your code into seperate modules. For example:
![](https://i.imgur.com/SF8uPHr.png)

---

### Why Modularise?

1.  Maintainabilty:
    It's easier to come back and make changes if your code is seperated into 'modules'. MUCH NEATER.
2.  Reusability:
    You can easily copy and paste the module in future projects. NAUGHTY!
3.  Namespacing:  
    Without modularing, two completey unrelated parameters can more easily share the same variable names

---

### What is module.export?

![](https://i.imgur.com/kCCaEFO.png =500x)

![](https://i.imgur.com/A4Wxr0E.png =500x)

Creates a new module which is served by to the require method. Can contain objects or functions.

---

### What is require?

![](https://i.imgur.com/Is0GYJI.png =500x)

![](https://i.imgur.com/YpjSIiD.png =500x)

It navigates to the selected module. Can be a user made module or an install one.

---

# Why can't we use modules in the browser?

Because modules need node.js to run... browsers just run plain old javascript!

---

### How can we modularise client-side code?

The only js file you really want on the client side is the DOM.

All the logic, XHR requests etc should be done server side.

The various scripts requried for the DOM can be linked at the bottom of the HTML page.
![](https://i.imgur.com/5efqsRs.png)

---

# Asyncronous functions:

#### Why should you use asyncronous forms of functions wherever possible in Node?

REMEBER HIM?

![](https://i.imgur.com/IGyHoSx.png)

---

Node.js works asynchronously, always. If you're doing some blocking I/O (such as with eg. fs.readFileSync() or other synchronous function), the complete node.js runtime process stops processing anything else during that call. Therefore, in web request processing, you never call synchronous functions (it's only acceptable in node.js command line apps and during app startup etc.)

This is just a fundamental features of node.js; a consequence of it is that node.js/JavaScript doesn't have and doesn't need synchronized thread synchronization features like eg. Java.

Technically, the only place in a running node.js process which is multithreaded is the internal libuv library, and only to compensate for missing asynchronous I/O of the host system.

You can use nodes.js timers to create artificial events if your processing isn't triggered by I/O events. You're right to assume that in general, this makes nodes.js inconvenient or outright unsuitable for

---

#### What are error-first callbacks, and why is it important to follow that pattern in your own code?

error-first callbacks is also known as an “errorback”, “errback”, or “node-style callback”.

There’s really only two rules for defining an error-first callback:

1.  The first argument of the callback is reserved for an error object. If an error occurred, it will be returned by the first err argument.
2.  The second argument of the callback is reserved for any successful response data. If no error occurred, err will be set to null and any successful data will be returned in the second argument.

![](https://i.imgur.com/SH6Y5za.png)

Node.js relies on asynchronous code to stay fast, so having a dependable callback pattern is crucial. Without one, developers would be stuck maintaining different signatures and styles between each and every module.

---

#### Why should you avoid using throw in callbacks?

![](https://i.imgur.com/M0hJX8K.png)

---

#### When might you use the syncronous form of a function instead?

- In small projects.
- Sync functions are useful, especially on startup, where you want to make sure that you have the result prior to executing any more code.
  For example, you could load in a configuration file synchronously. However, if you are trying to do a file read during a live request, you should use async functions so you don't block other user requests.

---

Working with URLs (the url and querystring modules): What is a urlObject and how is it structured? Why is it important to be able to turn JavaScript objects into querystrings and back again? Why is it a bad idea to build a query string manually from other strings (think about URL encoding and escape characters)?

**What is urlObject?**
urlObject it is a function which takes a string URL and breaks it down into an object of accessible properties automatically in order to have easy access to the URL's parameter values as key value pairs and store a parameters multiple values automatically into an array too.
so here's the urlObject function:
https://www.thecodeship.com/web-development/javascript-url-object/
**the structure of the url**
![](https://i.imgur.com/lATo9DU.jpg)

---

**Why is it important to convert querystring to Javascript object and back agian?**

\_what is querystring?
The QueryString collection is used to retrieve the variable values in the HTTP query string.

The HTTP query string is specified by the values following the question mark (?), like this:

--<a> href= "test.asp?txt=this is a query string test">Link with a query string </a> --

The line above generates a variable named txt with the value "this is a query string test".

Query strings are also generated by form submission, or by a user typing a query into the address bar of the browser.

**Note**: If you want to send large amounts of data (beyond 100 kb) the Request.QueryString cannot be used.

---

It's important to convert querystring to javascript objects because when passing a data to to the server, the server can use and proccess this data only when it is a javascript object.
after being proccessing and using the data in the server, we want this data to be back to the client, so the server stringifies the data and then parsing it to an url string.
here's a link for explaining the steps of parsing and stringifying data from and to the server:
https://www.youtube.com/watch?v=QTAYRmMsVCI

---

# Input/Output

---

### What does 'fs' do?

---

### Wht use 'path'?

### Links

#### Modules:

https://medium.freecodecamp.org/javascript-modules-a-beginner-s-guide-783f7d7a5fcc
http://www.tutorialsteacher.com/nodejs/nodejs-module-exports

#### Asyncronous functions:

http://fredkschott.com/post/2014/03/understanding-error-first-callbacks-in-node-js/
https://ruben.verborgh.org/blog/2012/12/31/asynchronous-error-handling-in-javascript/

#### Input/output

https://nodejs.org/api/fs.html
https://nodejs.org/api/path.html

#### Working with URLs

http://www.developerdrive.com/2013/08/turning-the-querystring-into-a-json-object-using-javascript/
https://howchoo.com/g/nwywodhkndm/how-to-turn-an-object-into-query-string-parameters-in-javascript
