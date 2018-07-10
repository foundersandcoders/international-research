# Callback Functions

* What is the difference between synchronous and asynchronous code? **Dom**
* What is a callback in Javascript? **Eve**
* Why are callbacks useful? **Art**
* When would you use it? **Nathalie**
* **Bonus**: create a simple example of a callback

## What is the difference between synchronous and asynchronous code (JS)?
JS is a largely synchronous language, but there are many actions that can run *asynchronously*, such as:
* AJAX requests, 
* using setTimeout()
* Waiting for other things (e.g. external scripts) to load

Although JS is single-threaded, these asynchronous events are made possible by the browser's JS *Event Loop* and *Event Queue* (we will watch a video on this later!). So, in brief, asynchronous doesn't mean the same thing as "concurrent" or "multi-threaded".

Here's a nice example to display the difference between synchronous and asynchronous code execution, courtesy of PluralSight:

```
// Say "Hello."
console.log("Hello.");
// Say "Goodbye" two seconds from now.
setTimeout(function() {
  console.log("Goodbye!");
}, 2000);
// Say "Hello again!"
console.log("Hello again!");
```
If the code were purely synchronous, you'd expect the output order to be:
`Hello` , `[Nothing for 2 secs]`, `"Goodbye!"`, and finally `"Hello again!"`

However, in JS, we get a different output:
`"Hello"`, `"Hello again!"`, `[Nothing for ~2 secs]`, `"Goodbye!"`
This is because setTimeout() schedules something to happen in the future, and then immediately goes on to the next line of code.

Although this async behaviour can [improve the user experience](https://rowanmanning.com/posts/javascript-for-beginners-async/), the above can cause an issue when waiting for data from an external source, as you might want to use that data (e.g. a function from an external script, coordinates from the Google Maps API...) in a function down the line. This is where callbacks can come in handy :).


#### Resources 
* [JavaScript.info](https://javascript.info/callbacks) has a nice example of using a callback to solve an issue that arises due to the asynchronous nature of certain JS actions (in this case, script loading via a function). There's also a section on "callback hell", under the heading "Pyramid of doom".
* [PluralSight intro to asynchronous JS](https://www.pluralsight.com/guides/introduction-to-asynchronous-javascript)
* Google "callback hell js", "async await", "js promises"
* [CallbackHell](http://callbackhell.com)

## What is a callback in Javascript?

'Callback function' is a name to describe a function that's called as an argument to another function. When the parent function is called and its function body completes, the callback function is then invoked.

#### Example:
```
function printANumber(number, callbackFunction) {
  console.log("The number you provided is: " + number);
  // this is when callbackFunction is called
}

function printFinishMessage() {
  console.log("I have finished printing numbers.");
}

function event() {
  printANumber(6, printFinishMessage);
}
```

Result:

```
The number you provided is: 6
I have finished printing numbers.
```

An example you might be familiar with is:  ```array.map(function(x) { ... });```. Here, ```function(x)``` is a callback function, as it's called as an argument to another function

#### Event Loop
The main browser process is a single-threaded event loop -- it can only do one thing at a time
* when a function from one event is executed, no other events can be listened for until the first function has finished
* if you execute a long-running operation, then the browser stops processing other events
* a callback is executed outside of the main event loop, so even if it's a long-running operation, the main event loop can still function

## Why are callbacks useful?
**Why are callbacks useful?**

JS operates on a *single thread*, i.e. it performs one task at time.

JS code may or may not execute at once. E.g. a function may wait for user input or execute after X milliseconds have lapsed. The browser will display (in whatever way) the outcome of the time-delayed function after the outcome of the functions that execute at once, even though all functions are (invisibly) executed sequentially.

You can use multiple callbacks within the same function.

Callbacks do not manipulate the order in which code is executed, but they do manipulate *when* it is executed. You can think of callbacks as 'switches' or as a way of 'hacking' the synchronous nature of JS so that it behaves asynchronously - essentially, callbacks enable JS to multi-task.

**The drawbacks of callbacks**
It isn't always possible to predict precisely when a higher-order function with finish, which means that all functions that depend on it (i.e. all callbacks) have to be nested within it. Which can very quickly turn into messy, unreadable (at least by human coders) code, affectionately known as 'callback hell' (there's even a website dedicated to it: http://callbackhell.com/).

How to avoid 'callback hell': https://blog.risingstack.com/node-js-async-best-practices-avoiding-callback-hell-node-js-at-scale/

*Read more:*
Source: https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec

## When to use callbacks?
* When requesting data online
    * [Google example](https://mdn.github.io/learning-area/javascript/apis/introduction/maps-example.html) of displaying the location of your current device
    * [See the full code in the Google example repo on GitHub](https://github.com/mdn/learning-area/blob/master/javascript/apis/introduction/maps-example.html)
    
```
// a function is passed as an argument
navigator.geolocation.getCurrentPosition(function(position) {
    // co-ordinates are requested here and once recieved, will be added in the myOptions object  
    var latlng = new google.maps.LatLng(position.coords.latitude, position.coords.longitude);
    var myOptions = {
        zoom: 8,
        center: latlng,
        mapTypeId: google.maps.MapTypeId.TERRAIN,
        disableDefaultUI: true
    }
    // once myOptions is final the map will be rendered in #map-canvas 
    var map = new google.maps.Map(document.getElementById("map_canvas"), myOptions);
});
```    
  
* When you want to use .forEach(), .map(), .filter() and reduce():
    * Higher order functions are those that can take another function as an argument or that can return a function as a result
    * .map() - when you and to modify all items in an array the same way. 
    * .forEach() - when you want to loop through items in an array 



















## General (rough) Notes

### Dom
* "A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action." - MDN
* * "In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions. Functions that do this are called higher-order functions. Any function that is passed as an argument is called a callback function." - [codeburst](https://codeburst.io/javascript-what-the-heck-is-a-callback-aba4da2deced)
* Given the above, we may be splitting our functions into callbacks for testing??
* Synchronous callbacks are executed immediately
* Callbacks are a way to ensure that certain code doesn’t execute until other code has already finished execution. E.g. if one function is waiting for the result of an API request before continuing


### Art
**Why are callbacks useful?**

JS operates on a *single thread*, i.e. it performs one task at time.

JS code may or may not execute at once. E.g. a function may wait for user input or execute after X milliseconds have lapsed. The browser will display (in whatever way) the outcome of the time-delayed function after the outcome of the functions that execute at once, even though all functions are (invisibly) executed sequentially.

Callbacks do not manipulate the order in which code is executed, but they do manipulate *when* it is executed. You can think of callbacks as 'switches' or as a way of 'hacking' the synchronous nature of JS so that it behaves asynchronously - essentially, callbacks enable JS to multi-task.

**The drawbacks of callbacks**
It isn't always possible to predict precisely when a higher-order function with finish, which means that all functions that depend on it (i.e. all callbacks) have to be nested within it. Which can very quickly turn into messy, unreadable (at least by human coders) code, affectionately known as 'callback hell' (there's even a website dedicated to it: http://callbackhell.com/).

*Read more:*
Source: https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec

### When to use callbacks?
1. When requesting data online
    * [Google example](https://mdn.github.io/learning-area/javascript/apis/introduction/maps-example.html) of displaying the location of your current device
```
navigator.geolocation.getCurrentPosition(function(position) {
    var latlng = new google.maps.LatLng(position.coords.latitude, position.coords.longitude);
    var myOptions = {
        zoom: 8,
        center: latlng,
        mapTypeId: google.maps.MapTypeId.TERRAIN,
        disableDefaultUI: true
    }
    var map = new google.maps.Map(document.getElementById("map_canvas"), myOptions);
});
```

[gitHub repo](https://github.com/mdn/learning-area/blob/master/javascript/apis/introduction/maps-example.html)
      
2. When you want to use .forEach(), .map(), .filter() and reduce():
    * Higher order functions are those that can take another function as an argument or that can return a function as a result
    * .map() - when you and to modify all items in an array the same way. 
    * .forEach() - when you want to loop through items in an array 