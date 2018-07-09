# RegEx research notes
Created by the wonderful Eve, Dom, Simon & Kate from FAC14

## Topics to cover
* Pattern creation and recognition
* Groups
* Use of tools like [regex101](https://regex101.com/) and [regexr](https://regexr.com/)
* Code snippet examples, e.g. email validator

## Research notes

### RegEx basics

The purpose of regular expressions is to perform pattern-recognition and find-and-replace functions on text.

For example, you can use regular expressions if you want to find out if the letter 'e' appears in a string.

Regular expressions are objects in JavaScript.

They can be instantiated in two ways: with literal notation or with object constructors.

Literal notation: ```var myRegex = /pattern/flag;```

Constructor: ```var myRegex = new RegExp('pattern', 'flag');```

```pattern``` is what to search for, whereas ```flag``` indicates what kind of search. For example, flags can be used to perform a case-insensitive search. A regular expression can have multiple flags.

#### Literals vs. Constructors

There is a difference between literals and constructors: literal regular expressions cannot accept dynamic input. The ```pattern``` between the two slashes in ```var myRegex = /pattern/flag;``` is interpreted literally.

With constructors, something like this is possible:
```
var words = ["red", "orange", "yellow"];
var myRegex = new RegExp( '(' + words.join('|') + ')' );
console.log(myRegex); // returns /(orange|yellow|green)/
```

This means that a regular expression defined through an object constructor is dynamic and can be changed respond to, for example, user input.

#### Regex methods

Because regular expressions are objects in JavaScript, they have methods:
* ```myRegex.exec(string)``` returns the first match
* ```myRegex.test(string)``` returns true or false
* ```myRegex.toString(string)``` returns the string value of the regex

#### Regex properties

They also have properties:
* ```myRegex.source``` returns the text of the pattern
* ```myRegex.lastIndex``` specifies the index at which to start the next match (i.e. somewhere other than the start of the string)
* ```myRegex.global```, ```myRegex.ignoreCase``` and ```myRegex.multiline``` check whether the global, case-insensitive and multiline flags, respectively, are set

#### Using regex on strings

Strings have methods that can make use of regular expressions:

* ```str.search(regex)``` returns the position of the first match, or ```-1``` if no match was found
* if the regular expression doesn't contain a global flag, ```str.match(regex)``` returns:
    * the first match
    * the index of the first match
    * the queried string
* if the regular expression contains a global flag, ```str.match(regex)``` returns:
    * an array containing all matches
* ```str.split(regex, limit)``` splits the string using the regular expression
* ```str.replace(regex, string|function)``` finds the regex pattern and replaces it

### Pattern creation/recognition

* A regular expression consists of a pattern and optional flags
* There are two syntaxes to create a regular expression object

* the long syntax:
>     regexp = new RegExp("pattern", "flags");
    
* the short one, using slashes "/":
>     regexp = /pattern/; // no flags
>     regexp = /pattern/gi; // with flags

**Slashes "/" tell JavaScript that we are creating a regular expression.** 


#### EXAMPLE SYNTAX 
![](https://image.ibb.co/hO7NEy/regExp.png)

### Groups

* Groups can be used to find specific groups of characters or substrings
    * You want to capture exactly 3 digits followed by 1 or more alphanumeric characters: **/(\d{3})(\w+)/**
    * (\d{3}) = **\d** is digits, and **{3}** is exactly 3
    * (\w+) = **\w** is alphanumeric chars, and **+** is one or more
    * It will match **123s**, **1234**, and **123 sfhdfsdk**, but not **123** on its own
* If needed, you can also use RegEx groups to save anything that matches your group
* There are two types of group: captured (where you save the matches) and uncaptured (where you don't)
* Captured groups
    * Why capture a group?
        * You want to use this data elsewhere, i.e. capture email addresses and then sort them alphabetically (https://repl.it/@sbinlondon/DrearyUnwillingActivecell)
        * Groups are captured in an array
* Uncaptured groups
    * Why not capture a group?
        * There's a performance penalty, so don't do it unless you need to
* Optional groups
    * You can make a capturing group optional by putting a **?** outside the **(...)**
    * [Example on Stack Overflow](https://stackoverflow.com/questions/3512471/what-is-a-non-capturing-group-what-does-do)

### Useful tools for testing/"debugging" RegEx
These sites are some of the many useful RegEx resources available
* [regexr](https://regexr.com)
* [regex101](https://regex101.com) - used in the example below
* [regexone](https://regexone.com) - interactive RegEx exercises
* [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

## Examples (e.g. email/username validator)

Some tasks you could practice RegEx with:
1. Phone number validator
2. Find all proper names in a paragraph
3. Email validator

In our [interactive example](https://regex101.com/r/ckFx6r/2) (click the link!), we'll turn a slightly flawed email validation RegEx into something more full-featured. Read the spec and follow the instructions at the link.
