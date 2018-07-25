# Topic 2: Engineering

## Modules

#### Why is it a good idea to modularise your code?
###### Breaking out logic into modules
You create small, separate modules with clear responsibility instead of spaghetti code. Grouping functions related to a single entity or object into a single file and organizing the directory structure based on logic has many advantages: 
- it will save a lot of time determining which function to touch when a bug has to be fixed
- less code has to be written
- a single procedure can be developed for reuse, eliminating the need to retype the code many times
- scoping of variables can easily be controlled
- code in each file is short, simple and easy to understand
- it helps to decouple all of the components in the architecture, facilitating the replacement of discrete functionality without the need to modify any other lines of code
- it will also help in writing test cases

#### What are require() and module.exports?
The module.exports is a special object which is included in every JS file in the Node.js application by default. 
module.exports is an object that the current module returns when it is "required" in another program or module

The builtin require function is the easiest way to include modules that exist in separate files. The basic functionality of require is that it reads a javascript file, executes the file, and then proceeds to return the exports object.
require(module) is simply calling for a certain special object representing the functionality of the module, it’s just a way of loading modules

#### Why can't you use them in the browser?
In the terminal, you are running the node application and it is running your script. That is a very different execution environment than directly running your script in the browser. While the Javascript language is largely the same (both V8 if you're running the Chrome browser), the rest of the execution environment such as libraries available are not the same.

node.js is a server-side Javascript execution environment that combines the V8 Javascript engine with a bunch of server-side libraries.  require() is one such feature that node.js adds to the environment. So, when you run node in the terminal, you are running an environment that contains require().

require() is not a feature that is built into the browser. That is a specific feature of node.js, not of a browser. So, when you try to have the browser run your script, it does not have require().
#### How might you modularise client-side code?
Browsers don't have the require method defined, but Node.js does. With Browserify you can write code that uses require in the same way that you would use it in Node.
http://browserify.org/
Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in old browsers or environments.
https://babeljs.io/
Webpack can take all your modules and bundle them in a single output file commonly known as bundle.js. This process gives you the ability to use almost every module in your frontend project.
https://webpack.js.org/


Safari, Chrome, Firefox and Edge all support the ES6 Modules import syntax. 
``` javascript
<script type="module">
  //import { export } from "module-name"
  import {foo, bar} from '/modules/my-module.js'
</script>
```

## Asynchronous Functions

#### Why should you use asyncronous forms of functions wherever possible in Node?
* Node is commonly used on web servers
    * deals with requests that may take some time to complete
    * single-threaded
* a server would not be able to respond to other requests while waiting for a synchronous function to complete
    * every user making a request to the server would have to wait for a response

![](https://media.giphy.com/media/UJR3QgkMnm7tu/giphy.gif "title")

[](https://www.pluralsight.com/guides/introduction-to-asynchronous-javascript)

#### What are error-first callbacks, and why is it important to follow that pattern in your own code?
* the error-first pattern is a callback pattern
    * the first argument passed to a callback function is reserved for the error object
    * the second argument is reserved for any successful response data
* we used error-first callbacks this morning:
```
fs.readFile(__dirname + '/public/index.html', function(error, file) {
    if (error) {
        console.log(error);
        return;
    }
    response.end(file);
});
```
* a dependable way for programmers to know how an error resulting from a request is going to be presented
* allows the programmer to decide how they want to handle an error
    * programmer can choose to ignore, handle or propagate the error

[](http://fredkschott.com/post/2014/03/understanding-error-first-callbacks-in-node-js/)

#### Why should you avoid using `throw` in callbacks?
* the `try` -> `catch` -> `throw` -> `finally` sequence in JavaScript lets you:
    * test a block of code for errors
        * `try { // block of code to try }`
    * handle the error
        * `catch(error) { // display error }`
    * create custom errors
        * `throw "error message"`
    * run the code anyway
        * `finally { // run the damn thing anyway }`
* after throwing an error, execution of the current function will stop
    * control is passed to the first `catch` block in the call stack, or the program will terminate
* `throw` doesn't let you pass the error as an argument to a callback function

#### When might you use the syncronous form of a function instead?
* synchronous code may run faster than asynchronous code
    * and is simpler to understand
* for example, reading multiple small files:
    * running asynchronously may cause the `EMFILE: too many open files` error
    * `fs.readFileSync()` vs. `fs.readFile()` to read 1999 small text files

[](https://medium.com/@adamhooper/node-synchronous-code-runs-faster-than-asynchronous-code-b0553d5cf54e)

## Input/output (the fs and path modules)

The Node.js file module allows you to work with the files stored on your computer.

It can be called as follows using the require method:

`var fs = require('fs');`

The browswer runs in a sandbox which only allows it to run web-based applications. Therefore browsers cannot currently access the users files, so the node.js file system module is a must for creating servers. 

Methods 

Reading files:

```
fs.readfile();

fs.readFile('demofile1.html', function(err, data) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write(data);
    res.end();
  });
```
Creating files:
```
var fs = require('fs');

fs.writeFile('mynewfile.txt', 'Hello content!', function (err) {
  if (err) throw err;
  console.log('Saved!');
});
```
Deleting files
```
var fs = require('fs');

fs.unlink('mynewfile2.txt', function (err) {
  if (err) throw err;
  console.log('File deleted!');
});
```

Renaming files
```
var fs = require('fs');

fs.rename('mynewfile1.txt', 'myrenamedfile.txt', function (err) {
  if (err) throw err;
  console.log('File Renamed!');
});
```

Different operating systems use different file path separators. So manually inputting file paths will not always work for different operating systems. 

Path module
```
var path = require('path');
```
Provides a series of methods for working with directories and file paths.
```
var path = require("path");
var directories = ["dirA", "dirB", "dirC"];
var directory = directories.join(path.sep);

console.log(directory);
```
dirA\dirB\dirC on Windows
dirA/dirB/dirC on UNIX

Similarly, Windows places a semicolon to separate paths in a path environment variable. Other systems use a colon.

Node provides the delimiter property to fix this:
```
var path = require("path");

process.env.PATH.split(path.delimiter).forEach(function(dir) {
  console.log(dir);
});
```

Extracting file name:
```
var path = require('path');
var filename = path.basename('/Users/Refsnes/demo_path.js');
console.log(filename)
```
Returning extension:
```
var path = require('path');

var ext = path.extname('/Users/Refsnes/demo_path.js');
console.log(ext);
```
Returning filepath of directory:
```
var path = require('path');
//Return the directries:
var directories = path.dirname('/Users/Refsnes/demo_path.js');
console.log(directories);
```


Method	Description

`basename()`	Returns the last part of a path
`delimiter`	Returns the delimiter specified for the platform
`dirname()`	Returns the directories of a part
`extname()`	Returns the file extension of a path
`format()`	Formats a path object into a path string
`isAbsolute()`	Returns true if a path is an absolute path, otherwise false
`join()`	Joins the specified paths into one
`normalize()`	Normalizes the specified path
`parse()`	Formats a path string into a path object
`posix`	Returns an object containing POSIX specific properties and methods
`relative()`	Returns the relative path from one specified path to another specified path
`resolve()`	Resolves the specified paths into an absolute path
`sep`	Returns the segment separator specified for the platform
`win32`	Returns an object containing Windows specific properties and methods


## Working with URLs
### What is the urlObject and how is it structured?
* The urlObject allows you to apply methods to a url
```
const url = require('url');
```
* Using the urlObject you can parse, construct or authorisse your url, see all methods available on [nodejs.org](https://nodejs.org/api/url.html) below  
![available url methods on nodejs.org](https://i.imgur.com/rUOs13a.png)


### Why is it important to be able to turn JavaScript objects into query strings and back again?
* URLs can be used to send information

> 
> Information added to a `<form>` with `method="GET"` will be added to the end of the action URL as a query string:
> 
> `GET /example/message.html?name=Jean&message=Yes%3F HTTP/1.1`
> 
[READ MORE: Eloquent JavaScript, Chapter 18: HTTP and Forms](https://eloquentjavascript.net/18_http.html)


### Why is it a bad idea to build a query string manually from other strings (think about URL encoding and escape characters)?
* URLs have their own syntax called URL encoding
    * The legal characters for URLs are 0-9, A-Z, a-z, and the following special characters: $-_.,+!*’()
    * Others are based on % and the ASCII code of the sign 
    
    | Character | URL syntax |
    | -------- | -------- |
    | space | %20    | 
    | :     | %3A    |
    | \     | %5C    | 


JavaScript provides the **encodeURIComponent** and decodeURIComponent functions to encode and decode this format.
*    encodeURIComponent() - makes your text a working URL
``` 
encodeURI("http://www.example.org/a file with spaces.html")
--> http://www.example.org/a%20file%20with%20spaces.html
```

* decodeURIComponent() - decodes your URL into text

```
decodeURIComponent("http%3A%2F%2Fexample.org%2F%20many%20files%20here")
--> http://example.org/many files here
```
