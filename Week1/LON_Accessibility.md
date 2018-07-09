# Accessibility Group Research

## Creating an accessible navbar

### 1. Why is this important?

Nav bar is one of the most important areas that needs to be accessible - it’s their route to navigating your website.

### 2. What is needed to make it accessible:

#### a. Keyboard accessible navigation
It’s important that users can navigate with only a keyboard or button

#### b. Touch device capable
People access via multiple devices. Be aware when styling (e.g. hover functions)

#### c. Readability
Menu should adapt to be readable regardless of size of screen, length of words, language or people who need larger text.
(e.g. Simply scaling down your menu on a small device will make it very hard for people with reduced sight or dexterity)

#### d. Assistive technology friendly
Ensuring your website is easily navigable for screen-readers, screen magnifiers, and other assistive software.

### 3. Quick ways to ensure accessibility

#### a. Using semantic HTML and following navbar rules
* nav - Outer wrapper to clearly outline your navigation section
* a - elements only when changing a URL
* button> for javascript actions
* Bear in mind div and span are not found by tabs

#### b. Ensure your website is properly structured with clear labels
* This allows users to confidently skip entire irrelevant sections of your site
* Consistent styling of the menu
* Sufficient colour contrasts
* Putting menus generally where people expect them (e.g. horizontally top or vertical left)

#### c. Use invisible text to provide extra navigation info for readers
```
CODE SNIPPET: HTML
<li>
	<span class="current">
		<span class="visuallyhidden">Current Page: </span>
		Space Bears
	</span>
</li>
```

#### d. Add an accessibility menu
You can provide an alternative navigation altogether to optimise for assistive technology and accessibility. 

#### e. Beware drop-down/fly-out menus
These can be hard for those with reduced dexterity & can sometimes be styled in a way that makes them missed by screen readers. 

Possible options:
* Use a button to toggle visibility of the ul items (always wrap this in the navbar not outside)
* Build a separate accessibility menu
* Use Aria (e.g. aria-haspopup="true" indicates the menu item has a sub menu)

#### f. A good navbar is a skippable navbar!
A user may not want to go through the nav bar everytime. Provide a link at the top of the page which jumps the user down to an anchor or target at the beginning of the main content:

```
<a href=”#maincontent” >skip navigation</a>
<main id=”maincontent”>
```

### 4. Useful links

Part of the web accessibility initiative:
https://www.w3.org/WAI/tutorials/menus/structure/

Takes you through a real life example through the ancestry website:
https://blogs.ancestry.com/ancestry/2014/01/27/creating-a-completely-accessible-navigation-bar-in-html-css-and-js/

Useful accessibility menu tutorial:
https://www.smashingmagazine.com/2017/11/building-accessible-menu-systems/

## Creating an accessible modal

### 1. What is a modal?

A modal, or modal window generally refers to a window that overlays a page's main content. When a modal is open it should disable the main body of the page and focus the user on the modal's content alone. 
[Wikipedia reference](https://en.wikipedia.org/wiki/Modal_window)

**You may have enountered modal windows as...**
* Sign-up/Log-in boxes.
* Pop-up adverts
* Lightboxes for displaying larger images
* Dialog boxes for warnings/important alerts

**Example:**

* [Sign in/Sign up example](https://codepen.io/codyhouse/pen/pIrbg)
    
    
### 2. The problems of modals for accessibility.

Modals are conceptually outside the flow of the document and should conceal all other content, but HTML mark-up *requires* they sit somewhere in the flow of the document! This can cause a problem for top-to-bottom screen readers.

**To give a screen reader user the same experience as a visual user:**
* The browser's focus should be moved to the start of the modal content when a modal opens. 
* Focus should be restricted to the modal while it is open. You should not be able to tab to or tab through the main content of the page from a modal.
* There should be an accessible cancel/escape button to return to the main page.
* When the modal closes, the focus should be set back to where it was before the modal opened.

[Demonstration of bad modal window here](https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/3987b0ea-3723-43cc-8b03-334eefdb8bf2/inaccessible.html#!).


### 3. Solving the accessibility problem.

**Steps to take:**

1. Markup the Dialog and Dialog Overlay Appropriately
1. On Dialog Open, Set Focus
1. On Dialog Close, Return Focus to the Last Focused Element
1. While Open, Prevent Mouse Clicks Outside the Dialog
1. While Open, Prevent Tabbing to Outside the Dialog
1. Allow the ESC Key to Close the Dialog

### 4. Using ARIA and semantic HTML

There is an HTML5 `<dialog>` element that will eventually solve a lot of these issues, however it is not well implemented *yet* ([see how easy it will be one day!](https://keithjgrant.com/posts/2018/meet-the-new-dialog-element/)) so it's best to supplement the dialog element with ARIA to make sure screen readers can read the content.

* Use `role="dialog"` to show screen readers that the element has dialog function
* Use `aria-labelledby` and `aria-describedby` to tell the screen reader which text represents the label and description of the modal box
* Use aria-hidden to make sure screen-readers do not focus on the page content while the modal is open

### 5. Using JS

#### Controlling focus

* Using the .focus() method brings focus to the desired element.
* Using an event listener you can keep focus inside the modal.
* If the modal can be opened from more than one location in the page, you can store the id of the element that opened it, and return focus back to the right place when the modal is closed.

Further description here:

https://www.w3.org/WAI/GL/wiki/Using_ARIA_role%3Ddialog_to_implement_a_modal_dialog_box

#### Adding Key handlers

Listening for particular key strokes works in a very similar way to listening to any other event. Event types for keys are 'keydown', 'keyup' and 'keypress'. More info on those [here](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent).

Each key has a defined 'keycode', and you can look up a key's keycode at _keycodes.info_. You can use semantic codes like 'Space' for readability but most examples seem to use the numerical codes, which is what I've used here.

For example, the code for the spacebar is 32. The code for the escape key is 27.

This code block gives you an idea of how you would implement a esc-key modal escape in JavaScript:

```
object.addEventListener("keydown", myScript);

const myScript = (event) => {
    if ( event.which == 27 ) {
        modal.close();
    }
}
```


#### Sources - Modal Accessibility

https://www.smashingmagazine.com/2014/09/making-modal-windows-better-for-everyone/

https://www.w3.org/WAI/GL/wiki/Using_ARIA_role%3Ddialog_to_implement_a_modal_dialog_box

https://keithjgrant.com/posts/2018/meet-the-new-dialog-element/

https://en.wikipedia.org/wiki/Modal_window

https://a11yproject.com/posts/how-to-hide-content/

#### Learning resources

[Udacity](https://classroom.udacity.com/courses/ud891)

[FreeCodeCamp](https://learn.freecodecamp.org/responsive-web-design/applied-accessibility)
