# Topic 1: Architecting
![architect](https://media.giphy.com/media/w1AdHXsJXIG8U/giphy.gif)

### Separation of concerns (Emily)
![separation](https://media.giphy.com/media/l2Je4IvMkMk7qUC5O/giphy.gif)
* The process of breaking a computer program into distinct features that should overlap in functionality as little as possible
* The process of SoC is achieved through modularising
* General rule is each section should address a seperate concern
    * HTML - stucture 
    * CSS - style
    * Javascript - functionality
    * Prior to CSS, HTML defined both semantics and style
* When this isn't followed, it becomes more difficult to change, test or debug your code

#### Reasons why it benefits you:
* When separated, individual concerns can be reused, developed on and updated independently from rest of code
* Insulates code from potential failure from other functions
* Especially useful to be able to modify one section of code without having to know the details of the other sections/make corresponding changes to those sections

#### MVC architecture:

One commonly seen design pattern in software is **Model, View, Controller**.

**Models** are responsible for retrieving and updating data from the database.

**Views** are responsible for creating the UI, e.g. filling a template file with data.

**Controllers** bridge the gap between the model and view - they handle requests from the client, send and receive data from models and prepare it before sending it to the view to be rendered.

### Client side vs server side (Michael)

![WEBSITE](https://media.giphy.com/media/bF2M6el0vi2qc/giphy.gif)

:computer: *Client* - The web browser viewing the site on your computer.

:globe_with_meridians: *Server* - The computer that hosts the website's files and data.

💣*Validation* - checking user input is correct and that it won't damage your website/server.

📝 *Templating* - Using a pre-defined page structure, and filling it with dynamic data (e.g. Google image search, Amazon product page - each has the same structure but is filled with different data)

#### Why you might want to run code...

##### On the client:
![code running on the client](https://media.giphy.com/media/yUb1EBeo2TzJC/giphy.gif)
* Client-side rendering can make loading new content quicker, as you can grab just the necessary data and then re-render only a part of the page at a time.
* To avoid placing a high load on the server - tasks like rendering complex graphics or running an interactive game can take place on the client side.
* To run form validation before making a call to the server, reducing server load.
* In a [single page application](https://en.wikipedia.org/wiki/Single-page_application) e.g. using [Vue.js](vue.js) - it might take longer to download, but once it has downloaded an SPA is available on the client even when there is no internet connection, and each new page will load very fast as it's being rendered directly from the client.
* Using a templating library like [handlebars](handlebarsjs.com) to fill in a template by requesting the 'filling' data from the server. Each time you render a new page using the same template, you just need to grab the data to fill in the blanks. 

##### On the server:
![alt text](https://media.giphy.com/media/PD9hjqdeidgqY/giphy.gif)
* To hide private data like API keys from the client
* To keep information in a database private, and only give the client the data you want them to have access to.
* To keep form validation rules secret and prevent a malicious user from [injecting code](https://www.wikihow.com/Use-JavaScript-Injections) that could bypass security checks or cause a data breach.
* To create pages from a template that can be viewed in the browser without using JavaScript.
* Server-side rendering can make loading the page quicker, as browsers are optimised to load an HTML web page quickly.
* Creating a page from a template on the server-side can also be better for SEO as when search engines and clients view the page, it has been populated with all the dynamic data already - to the client it looks like a static page, but it can be recreated by the server many times with new data.

There used to be more of a clear separation between server-side and client-side code. Until fairly recently, templating using dynamic data in pages would always be done on the server side. However, newer libraries have allowed for dynamic pages to be rendered on the client side, retrieving just the necessary data from the server and not the whole page. This can be quicker and can avoid having to reload any more of the page content than is stricly necessary, improving page load time and reducing server load. Some libraries have even moved the entire site and all its data onto the client side, meaning once it has been loaded once it is always available even without an internet connection. However, server-side technology has also improved so that parts of a page can be rendered on the server and updated dynamically, also improving page load times. Which is faster? Who knows...

### Alternative back-end technologies (Dom)
Note: the info below is kept quite "general", as the [Nazareth repo](https://github.com/foundersandcoders/international-research/blob/master/Week4/NAZ_Architecting.md) already has some good, more in-depth comparisons of back-end technologies.

#### Considerations
![Thinking emoji 3D spinning](https://media0.giphy.com/media/CaiVJuZGvR8HK/giphy.gif)
There is no "best" back-end technology, as they all have their pros/cons and ideal use cases. When picking a back-end technology, you should consider: 
* The task at hand
    * More specifically, potential bottlenecks and what it involves (e.g. heavy I/O)
    * Does it need to be able to scale? Does it need to run extra efficiently?
    * Is this a quick MVP or a bigger, longer-term project?
* Speed, scalability & reliability
    * How quickly/efficiently does the code run?
    * How well will it work if/when you need to scale? How easy will it be to make it scale?
* Productivity
    * How quickly can you build your product with this technology?
    * How big is the technology's ecosystem? Are there lots of packages/frameworks/gems out there that speed up the build process?
    * Rails
* Skills and goals as a developer/team
    * This links in with productivity: if you're a team of JS developers with experience with Node, then you may well be more productive with it. If you might need to bring on more developers, will there be plenty with experience in that technology (or can they become familiar with it quickly)?
    * However, as developers we're always learning, and this can be an opportunity to try a new technology which may be better suited for certain tasks
* Trends
    * Is this technology still being supported/updated regularly?
    * Is the community around this technology (still) thriving?

#### Other, relatively common alternatives to Node/Express: 
`Framework/Runtime (Language)`
* Rails (Ruby)
* Django (Python)
* Flask (Python)
* Laravel (PHP)
* Phoenix (Elixir (Erlang VM))
* [Deno?!](https://www.youtube.com/watch?v=M3BM9TB-8yA) (TypeScript (JS))
* Spring (Java), Golang, Scala/Play & many more...

So many choices!
![Daria with the devil and angel on her shoulder](https://media3.giphy.com/media/5wBBmDD10iAg/giphy.gif)
...but which one will you choose?

#### Ramble/highly subjective summary of the above
* Arguably, comparisons should be made with these technologies and Meteor/Express, not Node by itself
* Rails is typically seen as very productive, but not that fast/scalable. It is often used for smaller projects or quickly prototyping an MVP. It's got a big community (including plenty of bootcamp grads), and there are loads of "Gems" available
* Django is also seen as productive (and many people are a fan of both Python and Ruby's syntax). Some say Django is faster than Rails, but neither are massively scalable.
* Flask is a more "bare bones" alternative to Django. This means it's likely less productive, but gives you more control (and is possibly "lighter") than Django
* Laravel seems decent but PHP gets a lot of hate these days. Still popular though...
* Phoenix is more niche, but many people like the Syntax and functional nature of Elixir, and Elixir is a very efficient, fault-tolerant language. Ideal for making scalable projects with heavy I/O.
* Deno is a work-in-progress created by Ryan Dahl, the creator of Node! See his 2018 talk titled "[10 Things I Regret About Node.js](https://www.youtube.com/watch?v=M3BM9TB-8yA)" for an introduction. In brief, its aim is to solve "2018 problems" rather than "2009 problems", and to be built from the ground up with Ryan's learnings (regrets?) from Node.


### Writing for different environments (Emma)

#### How is node.js different from browser side js?

* ES6 works great in Node but is not compatible with all browsers.
* Node uses modules and when refering to js in other files you need to export and require the code you want to use.
* Node comes with its own set of [core modules](https://nodejs.org/api/modules.html#modules_modules)
* Node does not have the predefined global object called "window" or the "document" object.
* Node does have a predefined global object called “global”. It contains several functions that are not available in browsers, as they are needed for server side works only.
* Node is headless whereas a browser is not.

![guillotine](https://media.giphy.com/media/10qpsHIBVwe19u/giphy.gif)

#### How to bridge the gap between them.

* **[Browserify](http://browserify.org/)** - allows you to use require() in browser side code

* **Babel** - allows you to transpile ES6 into ES5
You can try it out for yourself [here](https://babeljs.io/repl/).

* **Lebab** - allows you to transpile ES5 into ES6
You can try it out [here](https://lebab.io/try-it).


![goodbye](https://media.giphy.com/media/aSFo6DFAtfCs8/giphy.gif)
