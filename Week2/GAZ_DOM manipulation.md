#### FACG5 DOM manipulation [9 Jul 2018] 




<span style="color:#020c16 ; font-size:15px ; font-family:cairo ;">

  * ##  How can you use JavaScript to create an HTML element and then add it to your webpage? How would you replace an existing element with it?

</span>




 #### The createElement() method creates an Element Node with the specified name.

 #### By Using the createTextNode() method to create a text node.

#### After the element is created, use the element.appendChild() or element.insertBefore() method to insert it to the document.

```HTML
<script type="text/JavaScript">

var btn = document.createElement("BUTTON");        // Create a <button> element
var t = document.createTextNode("CLICK ME");       // Create a text node
btn.appendChild(t);                                // Append the text to <button>
document.body.appendChild(btn);                    // Append <button> to <body>
<script/>

```
#### To add it to a specific Div
```HTML
<script type="text/JavaScript">

var element = document.getElementById("div1");
element.appendChild(para);
<script/>

```

#### To replace an existing element with it 
```HTML
<div>
    <a id="link" href="#">Replace This</a>
  </div>

<script type="text/JavaScript">
  var link = document.getElementById("link");
  var new = document.createElement("span");
  new.textContent = "New Element";
  link.parentNode.replaceChild(new, link);
</script>
```
#### Or by using  

```HTML
<script type="text/JavaScript">

  var newElementContent = document.createTextNode("New Element");
newElement.appendChild(newElementContent);  
<script>
```

----


<span style="color:#020c16 ; font-size:15px ; font-family:cairo ;">

 * ## How would you add a "li" element to the start of a "ul"?

</span>

 
  #### by using appendChild to ul id 
 ```HTML


<ul id="myList">
  <li>Mohannad</li>
  <li>Ahmed</li>
</ul>

<script>
    var node = document.createElement("li");
    var textnode = document.createTextNode("Ibrahem");
    node.appendChild(textnode);
    document.getElementById("myList").appendChild(node);
</script>
 ```


----

<span style="color:#020c16 ; font-size:15px ; font-family:cairo ;">

* ## What is a JavaScript Event? What does event.preventDefault() do and why might you use it?


</span>

#### HTML events are "things" that happen to HTML elements.

####  When JavaScript is used in HTML pages, JavaScript can "react" on these events.

## HTML Events
####  An HTML event can be something the browser does, or something a user does.



* #### An HTML web page has finished loading
* ####  An HTML input field was changed
* #### An HTML button was clicked
 
| Event  | Description | 
| :---: | :---: | 
| onchange | An HTML element has been changed |
| onclick | The user clicks an HTML element |
| onmouseover | The user moves the mouse over an HTML element|
| onmouseout | The user moves the mouse away from an HTML element |
| ononkeydownchange | The user pushes a keyboard key |
| onload | The browser has finished loading the page |

## event.preventDefault()

#### The preventDefault() method cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur.

#### For example, this can be useful when:

#### Clicking on a "Submit" button, prevent it from submitting a form
#### Clicking on a link, prevent the link from following the URL


```HTML
<script type="text/JavaScript">
event.preventDefault();
<script/>
```
#### The cancelable event property returns a Boolean value indicating whether or not an event is a cancelable event.

```HTML
<script type="text/JavaScript">
var x = event.cancelable;
<script/>
```

----



<span style="color:#020c16 ; font-size:15px ; font-family:cairo ; ">

* ## What is a NodeList? How is it different from an Array?

</span>

* #### A NodeList object is a list (collection) of nodes extracted from a document.

* #### A NodeList object is almost the same as an HTMLCollection object.

* #### Some (older) browsers return a NodeList object instead of an HTMLCollection for methods like getElementsByClassName().

* #### All browsers return a NodeList object for the property childNodes. 

* #### Most browsers return a NodeList object for the method querySelectorAll().


```HTML
<script type="text/JavaScript">
var Node = document.querySelectorAll("p");

// To access it , we use 

y = Node[1];

// To get the length

Node.length;


<script/>
```

> ## A node list is not an array! 
> A node list may look like an array, but it is not.
> You can loop through the node list and refer to its nodes like an array.
> However, you cannot use Array Methods, like valueOf(), push(), pop(), or join() > on a node list.



----


<span style="color:#020c16 ; font-size:15px ; font-family:cairo ; ">

* ## What are the security concerns around Element.innerHTML and what could you use instead?


</span>

#### innerHTML is often misused and a very common source of client-side HTML-injection (DOM-XSS) security hole.
#### So we used some instead methods, such as 'createElement, text Content'