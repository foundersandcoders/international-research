# FAC14 - Week 2 Research - The DOM





## How can you use JavaScript to create an HTML element and then add it to your webpage? How would you replace an existing element with it?


1. create an HTML element
 * document.createElement is used with an HTML tag to create the element
    ```var div = document.createElement('div');```
    ```javascript
    //output: <div></div> (empty element)
    ```
2.  textContent is then modified/added
        * use textContent
        ```div.textContent = "Sup, y'all?";```
* Another way of doing it: 
This example creates a `<p>` element, then fills it with text and appends it to a `<div>` element:
```javascript
var div = document.createElement("div");
    // Create a <div> node
var text = document.createTextNode("This is a div with text.");
    // Create a text node
div.appendChild(text);
    // Append the text to <div>
```
        
3. add created element to your webpage
* the element is appended to the body using the appendChild method.
        ```document.body.appendChild(div);```
```javascript
document.getElementById("myDIV").appendChild(myParagraph);
    // Append <p> to <div> with id="myDIV"
```
* insertBefore(). This method takes two arguments — the first is the new child node to be added, and the second is the sibling node that will immediately follow the new node. In other words, you're inserting the new node before the next sibling node.
`parentNode.insertBefore(newNode, nextSibling);`
4. replace the old element with a new element
* replaceChild() takes two arguments — the new node, and the node to be replaced
`parentNode.replaceChild(newNode, oldNode);`



## How would you add a ```<li>``` element to the start of a ```<ul>?```

The process to create a `<li>` element inside a `<ul>` requires you to manipulate the DOM via the use of Javascript. If for instance you wanted to create a `h1` element inside the DOM you could use the following [Javascript](https://repl.it/@Zeanortt/DomH1): 
```javascript
    function createH1() {
     let h = document.createElement("H1");
     let t = document.createTextNode("Hello World");
        h.appendChild(t);
        document.body.appendChild(h);}
```

Assumuing that a `<ul>` already exists within your HTML file and you were simply seeking to add a named `<li>` element you could use the following [Javascript](https://repl.it/@Zeanortt/AddListElement):
```javascript
    function someFunction() {
     var node = document.createElement("LI");
     var textnode = document.createTextNode("Tomato");
     node.appendChild(textnode);
     document.getElementById("fruitList").appendChild(node);}
```

## What is a JavaScript Event?

JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates a page.

* When the page loads, it is called an event. 
* When the user clicks a button, that click too is an event. 

We can then register functions as handlers for these specific events and execute JavaScript coded responses to make:
* buttons close windows, 
* messages be displayed to users, 
* data be validated, 
* virtually any other type of response imaginable.

Events are a part of the Document Object Model (DOM) Level 3 and every HTML element contains a set of events which can trigger JavaScript Code.

## What does event.preventDefault() do and why might you use it?

Many events have a default action associated with them. 
* click a link, you will be taken to the link’s target.
* press the down arrow, the browser will scroll the page down.
* right-click, you’ll get a context menu.

For most types of events, the JS event handlers are called before the default behavior takes place. If the handler doesn’t want this normal behavior to happen, typically because it has already taken care of handling the event, it can call the preventDefault method on the event object.

This can be used to implement your own keyboard shortcuts or context menu. It can also be used to obnoxiously interfere with the behavior that users expect. 

Example of making a link unfollowable
```javascript
<a href="https://developer.mozilla.org/">MDN</a>
<script>
  let link = document.querySelector("a");
  link.addEventListener("click", event => {
    console.log("Nope.");
    event.preventDefault();
  });
</script>
```
You would use preventDefault anytime there is a default behaviour you want to bypass.



## What is a NodeList? How is it different from an Array? 

Nodes in the DOM: everything is a node and every node is an object. The name node is used as a generic term, for everything. A nodelist is a collection of DOM elements.

In some cases, the NodeList is a live collection, which means that changes in the DOM are reflected in the collection. For example, Node.childNodes is live:
```javascript
var parent = document.getElementById('parent');
var child_nodes = parent.childNodes;
console.log(child_nodes.length); // let's assume "2"
parent.appendChild(document.createElement('div'));
console.log(child_nodes.length); // should output "3"
```
In other cases, the NodeList is a static collection, meaning any subsequent change in the DOM does not affect the content of the collection.   ``` `document.querySelectorAll()``` returns a static NodeList.

Nodelists differ from arrays in that many of the methods used on arrays do not work with Nodelists as they use different prototypes. This snippet of code is a fairly good go-between

    const nodeList = document.getElementsByClassName('.yourClass'),
      nodeArray = [].slice.call(nodeList);
      Array.from()
     





## What are the security concerns around Element.innerHTML and what could you use instead?


It is not uncommon to see innerHTML used to insert text into a web page. There is potential for this to become an attack vector on a site, creating a potential security risk.

```
const name = "John";
// assuming 'el' is an HTML DOM element
el.innerHTML = name; // harmless in this case

// ...

name = "<script>alert('I am John in an annoying alert!')</script>";
el.innerHTML = name; // harmless in this case
```
Although this may look like a cross-site scripting attack, the result is harmless. HTML5 specifies that a <script> tag inserted with innerHTML should not execute.

However, there are ways to execute JavaScript without using ``<script>`` elements, so there is still a security risk whenever you use innerHTML to set strings over which you have no control. For example:

```
const name = "<img src='x' onerror='alert(1)'>";
el.innerHTML = name; // shows the alert
```
For that reason, it is recommended you not use innerHTML when inserting plain text; instead, use Node.textContent. This doesn't parse the passed content as HTML, but instead inserts it as raw text.






