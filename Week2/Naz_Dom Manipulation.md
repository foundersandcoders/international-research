**What is Java Script Event :**

A JS event is a Reaction that occures after specific actions you take in a browser in such specific areas that were defined in the first place in your HTML file .





**JavaScript  lets you execute code when events are detected , these elements help you acheive that :**

**Common HTML Events:**

![](https://i.imgur.com/tdJGrtx.png)


here’s a simple code made with HTML :
```

<!DOCTYPE html>
<html>
<body>

<button>Click Me</button>

<p id="demo"></p>

<script>
function myFunction() {
    document.getElementById("demo").innerHTML = "Hello World";
}
</script>

</body>
</html>





& it goes like this with JS event (Reaction):

<!DOCTYPE html>
<html>
<body>

<button onclick="myFunction()">Click Me</button>

<p id="demo"></p>

<script>
function myFunction() {
    document.getElementById("demo").innerHTML = "Hello World";
}
</script>

</body>
</html>

```







What is event.preventDefault() method:
Syntax-> event.preventDefault()

The preventDefault() method cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur.

For example, this can be useful when:
    • Clicking on a "Submit" button, prevent it from submitting a form
    • Clicking on a link, prevent the link from following the URL


It Prevents a link from opening the URL:

document.getElementById("myAnchor").addEventListener("click", function(event){
    event.preventDefault()
});

BUT!

Not all events are cancelable. Use the cancelable    property to find out if an event is cancelable.
https://www.w3schools.com/jsref/event_cancelable.asp
