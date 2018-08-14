# Web Storage Notes

Let's *unpack* (🤡🥁) some stuff about storage...

![](https://media.giphy.com/media/QovoAPHU4bjeE/giphy.gif)

### With web storage, web applications can store data locally within the user's browser.

#### **Before HTML5:** 
* Data had to be stored in cookies and included in every server request

![](https://media.giphy.com/media/l3vRmjIZpfYp8MLwA/giphy.gif)

#### **Today:**
* You can choose between *web storage* or *cookies* :new:
* Web storage can be either *local storage* or *session storage* :cool:

_All this choice..._

![](https://i.imgur.com/HFDIFGf.png)

## What is local storage? :fish_cake:

* Stores user data locally in the browser until the user clears it :computer:

![](https://media.giphy.com/media/BfqcuxcIAUGVa/giphy.gif)

### When is local storage useful?

It's worth considering as long as you are NOT looking to store any sensitive data. :mag_right: It's advantages:

* You can store lots of data (around 5mb)
* People seem to find it a lot easier to work with
* This can make them a useful tool for analytics

## What is session storage? :icecream:
* Stores data only for a session, meaning that the data is stored until the browser (or tab) is closed :no_good: 


### When is session storage useful? 
* **User settings:** things only want to show the user once or that you need the user to do once per login

* **When you have a dynamic interface:** Saving the current state of a dynamic page (e.g., what algorithmic content has been rendered by the user), allwoing the user to return to the same page at a later time

* **When you have special layout or templates:** can be loaded once and accessed from the session storage 

## Anything else? 

**How are they similar?** :dancers:
* They are both part of the Web Storage API
* Their implementations are very similar! Yay! :tada:
* They can both store a large amount of data (at least 5MB)
* Neither type can be accessed by the **server** - the data is only accessible from client-side JavaScript. Unlike cookies... :no_entry:

**How are they different?** :x:
* Session storage only holds on to user data for as long as the session lasts
* Local storage holds on to the user data until the user clears it

:warning: **Warning!**
* Local storage is accessible through JavaScript on the same domain. 
* This means that **any JavaScript running on your site will have access to web storage**, and because of this can be vulnerable to cross-site scripting (XSS) attacks :rotating_light: :rotating_light: :rotating_light: 

### Demo a simple usage of localStorage and sessionStorage

[**LOCAL STORAGE DEMO**](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_webstorage_local_clickcount)
[**SESSION STORAGE DEMO**](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_webstorage_session)


## OMG cookies?! :cookie:

*Come with us on now on a journey through time and space, to the world of The Mighty(?) Cookie.*

![](https://media.giphy.com/media/26gs8nKrs7uduirss/giphy.gif)

Cookies 🍪🍪🍪🍪 are similar to local storage in that they persist beyond the window closing, and could be considered a type of local storage, but there are some key differences that described below:

### tl;dr

**Cookies** and _local storage_ serve different purposes. **Cookies** are primarily for reading **server-side**, _local storage_ can only be read by the _client-side_. 

So the question is, in your app, who needs this data — the _client_ or the **server**?

### Cookies vs local/session storage

The downside of cookies...

![](https://media.giphy.com/media/26xBvXNKIykYtxIcw/giphy.gif)

* Only hold a very limited amount of data (around 4kb)
* Sent with every HTTP request so they add to the load of every document accessed on the domain
* Painful to work with (:question:), which can lead to oversights by developers

![](https://media.giphy.com/media/w6MqZsuQurdYY/giphy.gif)

* SQL injection can be performed from a cookie :dolphin: 

* Developers have defaulted to always using HTTP-only cookies which is good, but makes life harder for analytics because tracking in browser usually relies on Javascript 

### When to use cookies?

:rotating_light: :rotating_light: :rotating_light:  **Security!** :rotating_light: :rotating_light: :rotating_light: 

![](https://media.giphy.com/media/rg8Quo1tI1Et2/giphy.gif)

:warning: **Local Storage wasn't designed to be used as a secure storage mechanism in a browser.** 

It was designed to be a simple string only key/value store that developers could use to build slightly more complex single page apps. 

**:cookie:If you need to store sensitive data:cookie:**, you should always use a server-side session. To this you would want to use cookies............. Sensitive data includes:

* User IDs
* Session IDs
* JWTs
* Personal information
* Credit card information
* API keys
* And anything else you wouldn't want to publicly share on Facebook

**Compatibility**
* Cookies offer more universal coverage (unlike local and session storage that are both HTML5)
* Some browsers block local storage (& sometimes session storage) in incognito/private mode which makes it hard to access important stuff like a userId

## OMG Help

![](https://i.imgur.com/ns7KWbp.png)



### Interesting aside:

"Incognito" modes in different browsers have different ways of dealing with storage. Some won't let you store anything, some will, but wipe it all after a session.

> Chrome's "incognito mode" means -- is defined as -- starting from a clean slate (as if you started browsing for the first time on a new computer), and when you exit incognito mode, the accumulated data is discarded.

These incognito scenarios are worth bearing in mind so you don't rest functionality on the ability to store stuff locally.

Remember to check for browser support for localStorage and sessionStorage

```
if (typeof(Storage) !== "undefined") {
    // Code for localStorage/sessionStorage.
} else {
    // Sorry! No Web Storage support..
}
```

Related article:
https://blog.whatwg.org/tag/localstorage

## Useful Resources

[w3schools Web Storage reference](https://www.w3schools.com/html/html5_webstorage.asp)

[MDN Reference](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

[Please stop using local storage ](https://dev.to/rdegges/please-stop-using-local-storage-1i04) - Article


Comparison sheet:

https://docs.google.com/spreadsheets/d/16JIA-A87pKiRNL5PuZWBbGt__Z5Sr84t7oSBNuL5O70/edit?usp=sharing
