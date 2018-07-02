# FACN4 CSS 02-07-2018

## Responsive vs mobile-first design

Responsive web design is a web design method that enables web to fit the screens of different devices automatically, displaying the content in a way that people feel comfortable. This greatly reduces users’ operations like panning, zooming and scrolling when browsing the web.

Tools that are used to to make your website adaptive:
.CSS flexbox
.CSS grid
The main difference between both approaches are:
\_ Flexbox is made for one dimensional layouts and Grid is made for two dimensional layouts. [Further reading](https://hackernoon.com/the-ultimate-css-battle-grid-vs-flexbox-d40da0449faf) on which ones to use in specific scenarios.Discussion on which to use

Both flexbox and grid take some time to master. Here are some useful games/tools to help you learn [Flexbox](https://flexboxfroggy.com/) & [CSS Grid](https://cssgridgarden.com/).

#### Mobile First means designing for mobile before designing for desktop or any other device (This will make the page display faster on smaller devices).\*\*

Mobile first design is so important in product design because:

1.  Mobile internet usage has surpassed desktop usage in 2016.
2.  People have spent more and more time on the internet from mobile ends.
3.  Early in 2012, smartphone sales have overtaken PC sales.
4.  Search Engine Optimisation scores are begining to value mobile user experiences over that of desktop

#### Media query uses to make a website adaptive to both screen sizes and mobile first design:\*\*

The @media rule is used in media queries to apply different styles for different media types/devices.

Media queries can be used to check many things, such as:

width and height of the viewport
width and height of the device
orientation (is the tablet/phone in landscape or portrait mode?)
resolution
Using media queries are a popular technique for delivering a tailored style sheet (responsive web design) to desktops, laptops, tablets, and mobile phones.

You can also use media queries to specify that certain styles are only for printed documents or for screen readers (mediatype: print, screen, or speech).

In addition to media types, there are also media features. Media features provide more specific details to media queries, by allowing to test for a specific feature of the user agent or display device. For example, you can apply styles to only those screens that are greater, or smaller, than a certain width.

examples of using @media:

1.  specifying the screen size:
    If the browser window is 600px or smaller, the background color will be lightblue:
    @media only screen and (max-width: 600px) {
    body {
    background-color: lightblue;
    }
    }
2.  Being resposive to a mobile access using braekpoints:
    When the screen (browser window) gets smaller than 768px, each column should have a width of 100%:

/_ For desktop: _/
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}

@media only screen and (max-width: 768px) {
/_ For mobile phones: _/
[class*="col-"] {
width: 100%;
}
}

## How to write CSS with BEM (Block Element Modifier)

BEM is a popular convention for the use and naming of classes

It involves using multiple class names (grouped as blocks, Elements & modifiers) on HTML tags in order to stack properties. e.g.

> `<a href="somelink.com" class="btn btn--green btn--big"> <span class="btn__price">$9</span> <span class="btn__text">Big button</span></a>`

I hear you say, what is wrong with using a single class which styles a large green submit button? Please read on.

### Benefits to using BEM:

- Large projects may use many styles of button. Defining buttons in managable chunks allows us to re use our code, and may allow us to make a new style without actually writing any more css.

- If we are reading the HTML instead of CSS, we are able to quickly get an idea of which element depend on another.

- BEM allows teams to have a shared syntax so that they're on the same page on CSS methodology.

- With BEM everything is a class and nothing is nested. That makes CSS specificity very flat and low. Meaning that you can work in more confidence that modifying styles won't have unintended consequences elsewhere in your code.

For a great example of BEM in action have a look at the following [codePen](https://codepen.io/team/css-tricks/pen/226a65c8f7d64615aabd45048d1d3b6d)

[Further reading](https://css-tricks.com/bem-101/)
