# Test Coverage

## What is test coverage?

### ✨ _Formal defintion_ ✨

Test coverage is defined as a technique which determines whether our test cases are actually covering the application code and how much code is exercised when we run those testcases.

### wait, _what?_
![what?](https://media.giphy.com/media/cAEm5rSuuBEGY/giphy.gif)

It's a useful way to check how much of your code is actually being tested.

Kind of like a testing status check.

Test coverage doesn't tell you how good your tests are, just what parts of your code are being tested and if those tests are passing.

## Why is test coverage useful?

![score](https://media.giphy.com/media/1fnwSUTsHRyGXEYMos/giphy.gif)
- Gives us something objective - a score
- This also then gives us meaningful tasks which we can track (i.e. 'We don't have 100%, we now need to build tests to achieve 100%)

_THINGS TO BEAR IN MIND THOUGH..._

- 100% doesn't mean all bugs are found. If your tests aren't fully complete, you might cover the code but not actually be testing it as completely as you should
- Also doesn't spot bugs of omissions (i.e. bugs caused by code you haven't put in)



## What are Istanbul and nyc?

Lovely cities...

![](https://lonelyplanetimages.imgix.net/mastheads/64275521.jpg?sharp=10&vib=20&w=1200)

![](https://lonelyplanetimages.imgix.net/mastheads/GettyImages-538096543_medium.jpg?sharp=10&vib=20&w=1200https://)

:)

But also...

### Istanbul

Istanbul is a code coverage analysis script you run when executing your unit tests. 

By default, istanbul creates reports in a directory coverage under the current working directory (index.html).

Istanbul’s metrics include lines of code, functions, and branches; and it generates reports that color each line to indicate full, partial, or no coverage.

### Why? 
Istanbul tells you when code you have written is being executed so you can decide if un-covered lines can be removed or require additional testing.

You can track how well your unit-tests exercise your codebase

**Istanbul test coverage on FizzBuzz**
![](https://image.ibb.co/jKh2wo/Bildschirmfoto_2018_07_10_um_15_41_35.png)
![](https://image.ibb.co/eXfpbo/Bildschirmfoto_2018_07_10_um_15_41_22.png)
### NYC

NYC is the 'state of the art' ([their words](https://github.com/istanbuljs/nyc)) command-line interface for Istanbul.

It used to be separate but now the idea is essentially that nyc is the all-in-one, simple-to-use, command line interface for the Istanbul 2.0 API.

*You can dig more into the differences within the above github: https://github.com/istanbuljs/nyc/issues/524*


### _What do these columns mean?_

- **Statements**: how many of the statements in your code have been executed
- **Branches**: Tells you how many branches of code have been executed, conditional statements create branches of code (if/else) and these may not be executed
- **Functions**: The proportion of functions you have defined that have been called
- **Lines**: proportion of lines of code that have been executed

**Snapshot of Istanbul:**
![](https://i.imgur.com/AG1Yrl8.png)

**Snapshot of NYC:**
![](https://i.imgur.com/1v1KwgH.png)


- Very useful element of NYC is this extra column: Uncovered Line #s
    - Provides a really visual way to see where the code that is not covered lives
    - HOWEVER, as mentioned, you can see the direct code for both NYC and Istanbul by opening index.html within the **coverage** folder

![](https://i.imgur.com/plwRSrC.png)


- **NOTE!** 👀 Istanbul seems to report an extra branch, giving different percentage rates to NYC

### To keep things interesting, they have different ways of triggering them...

In package.json file you need to add a line under scripts:

**Opening NYC:**
"coverage": "nyc tape ./romanizer.test.js"

**Opening Istanbul:**
"coverage": "istanbul cover ./romanizer.test.js"



## How would you use them to improve your testing?

for the tldr people: 

1. Code coverage tools like Istanbul/NYC generate automatic reports analysing how much of your code is being tested by your test suite. That's neat, good job robots 🤖
2. Code coverage helps you spot superflous code or gaps in your testing. 
3. For when you're a real smarty: code coverage link into CI/CD to make sure PR's aren't ruining absolutely everything, so you might as well just push straight to master (seriously, **never do this**)

* 👀 **BUT IMPORTANTLY** 👀 Code coverage cannot (and should not) replace human code review. It's testing how thorough your testing is, not the code itself. 

## Use Istanbul/nyc to calculate your code coverage for the TDD workshop.

This is shown in the two snapshots of each of Istanbul and NYC above.

Here's also that same work for Romanizer...

**Istanbul:**

![](https://i.imgur.com/icBzwEh.png)

**NYC:**

![](https://i.imgur.com/IOhLjCl.png)



## Further reading: 

![that's one smart cat](https://media.giphy.com/media/Mj1QjRKM14ifC/giphy.gif)

* **Istanbul website**: https://istanbul.js.org/
* **Udacity**'s free Software Testing course has a good section on Code Coverage: https://eu.udacity.com/course/software-testing--cs258
* **dwyl on Istanbul**: https://github.com/dwyl/learn-istanbul - their *tracking coverage as-a-service* section shows how you can start bringing it all together with Github PR's, which is **awesome**.
