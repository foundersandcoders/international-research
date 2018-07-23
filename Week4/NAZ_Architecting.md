
# Architecting


---

## Separation of concerns - backend vs. frontend. (client vs server side)
Historically, back end and front end development had greater distinction. Front end was used for low intensity work on the UI, back end used for any serious functionality. However, the line between front and back end has blurred. Front end capabilities are being used for increasingly large tasks, and the introduction of node in 2009 allowed the back end to be coded in a previously front end focused language.


---

#### Despite this the front end has benefits:
* Access to DOM
* Ability to react without requests/responses
* A more interactive application
* Ideal for when the page elements need to be changed without the need to contact the server.


---

#### In turn the back end has other benefits:
* Compute intense calculations which the client side may not be able to handle
* Work with sensitive information that shouldn't be shared with users e.g. user validation
* Communicate with other servers more effieciently (e.g. API requests)
* Saving and retrieving data
* Ability to chose language


---


#### In Conclusion
Depending on the scope of a project, both front and back end may be used. A judgement must be made on each functionality to decide whether it should be in the front end or back end. Things to think about will be: how resource intensive the functionality, does the functionality need to be available rapidly, does it need to use any sensitive information.

<br>

---


## Alternative back-end technologies
Which other technologies (programming languages and servers) might be used instead of Node on the back end? What are some of the pros and cons of using Node in your stack, rather than one of those alternatives?



---


### Alternative technologies

* **Ruby on Rails** -  Very easy to learn, intuitive, and can be used both for prototyping and big projects. While Node.js has a much better performance and scalability, Rails wins at rapid development functionality. It hasn't got as many modules as node.js (a.k.a. gems), but users value them.
* **Django** - Quite fast, and just like Python, it is relatively easy to learn and an impressive speed of development. The choice betweed node.js and Django would very much depend on your language of choice. The Google search engine runs on Django.
<br>

---

### Pros of node.js
* **Node.js is fast:** it uses JavaScript in the backend. It runs on the Google’s V8 engine, which compiles the JavaScript directly into machine code making it faster than most.
* **The value of NPM:** node.js is an open-source technology, with a long and rapidly growing list of tools and modules. There are currently over 700k acording to the people at [NPM](https://www.npmjs.com/). Overtaking the number of Ruby on Rails gems.
* **Real-time web apps:** The event-driven architecture of node.js is appropriate for real-time applications, especially chat applications and games. As both the client-side and the server-side are written in JavaScript, the synchronization process is better and quicker.
* **Productivity:** Merging the front-end and back-end into a single language improved efficiency, and is the obvious choice for full-stack development. It also implies fewer employees are needed for each project. PayPal reported 2 times increase in developer productivity [after using node.js](https://www.paypal-engineering.com/2013/11/22/node-js-at-paypal/).
<br>
---

### User voted pros
![node, Rails, Django Pros](https://i.imgur.com/jbr7UfJ.png)

---
<br>

### User voted cons

![node, Rails, Django Cons](https://i.imgur.com/AKczFkU.png)
<br>


---

## Writing for different environments:
Why might you have to write JavaScript differently if its going to run in the browser, rather than in Node? What tools can help bridge the gap?

### node.js is extremely similar to JS v8
It is just the Node wrapper which has been written on top of  JavaScript V8 Runtime engine, which is deleting few objects and also including some according to the requirements of node.

<br>
---

### Node is different in the following ways
* Modules are different, there are some pre-installed when you initialise node such as http and [others](https://www.w3schools.com/nodejs/ref_modules.asp).
* There are no objects such as window or document
* Node has objects which browser js does not. e.g. global object
* Code is organised into modules, it can't be loaded through the index.html, it must be required in each file.
* Because you are in control of the node.js environment on your server, you are able to use new functionality in ES6+. Not all browsers will necesserily support this.



---


### Bridging the gap between ES6 and ES5
* Not all browsers run ES6. You can use modules to **transpile** your ES6 code in to ES5.

>  **Transpiling** taking source code written in one language and transforming into another language that has a similar level of abstraction
* One package used to do this is Babbel. Guide to its use [here](https://medium.com/@SunnyB/how-to-convert-es6-into-es5-using-babel-1b533d31a169).


---
