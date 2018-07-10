# Unit testing vs integration testing notes

## An analogy :car:

You wouldn't make a car without testing the individual bits before putting it together - otherwise you'd have no way to know if a single component was faulty; but you also wouldn't sell the car without testing how it works all together. 💥🚨🚑

![dog driving car](https://gogrove.co.uk/uploads/453/unbelievable-collection-of-funny-driving-quotes-and-car-memes-dog-styles-ideas.jpg)

## What is a unit test? 🤔

**Unit testing** is the testing of single functions/individual units of source code by supplying input and making sure the output is as expected. It's usually done by the developers who are writing the code, and they need to know the code inside and out.

Unit tests should be:

* Dead simple. :smile: 
* Lightning fast. ⚡️
* Give a good bug report. :bug:

What's a good bug report? 🐞📋

* Which component is under test?
* What is the expected behavior?
* What was the actual result?
* What is the expected result?
* How can the behavior be reproduced?

Unit testing can _also help you to write better code!_ :muscle: Code that’s hard to unit test usually has poor design. You can use unit tests to help design your code, keep it as a safety net 🕸when doing changes, and prevent regressions (bugs that occur repeatedly :bug: :bug: :bug:).

Unit testing can slow down the development process at first :turtle: , but generally saves a lot of time later on by avoiding bugs and refactoring as you go 🤓, thus avoiding [technical debt](https://en.wikipedia.org/wiki/Technical_debt).

:car: In our analogy, this is like testing each nut and bolt before you put them together to build parts of the car. You won't have to go back and check that each part works on its own later on.


## What is an integration test? 🤔

> ...but you wouldn't sell the car without testing how it works all together. 
> 

![](https://preview.ibb.co/hQq5Go/stealacar.jpg)

**Integration testing** is the testing of how our individual units/modules all behave when you put them together. It is usually done by people who are specifically testers, not the devs who are writing the code. The testers don't need to know the code inside and out as well as the devs do, but they need to know the architecture and how everything fits together.

While unit testing focuses on individual bits of code within the software, integration testing verifies how it works with other modules and external dependencies.

Because integration tests often require complex steps, i.e. setting up a test database to interact with your app, it’s recommended to focus on unit tests and only do integration testing where required.

**Approaches for Integration Testing:**
* _Big Bang Approach:_
    * As it sounds! Everything combined and tested at once. 💥
    * Advantages:
        * convenient on a small scale
    * Problems: 
        * hard to localize faults 
        * easy to miss areas in large systems and not test
        * can only begin once the whole system is built
        * doesn't priotisise more critical modules
 * _Incremental Approach:_ 
     * Combine 2+ logically related modules and test.
     * Combine further modules, testing on the way
     * Continue until whole system is integrated, tested and functioning
     * (this is clearly a way better approach...) 👍🏼
     * Requires **stubs** and **drivers** - dummy programs to simulate running the programme, replacing actual other modules:
         * **Stubs** are called by the Module under Test.
         * **Drivers** call the Module to be tested.

Incremental Approach is is further divided into:
* _Top Down Approach_ ⬇️
    * Higher UI levels tested first
    * get early prototype
    * but need lots of stubs!
* _Bottom Up Approach_ 🍑⬆️
    * Lower levels tested first (e.g. basic logic and backend not DOM manipulation)
    * Doesn't necessarily prioritise critical UI modules.
    * Don't get early prototype
* _Sandwich Approach_ 🍔
    * Combination of Top Down and Bottom Up
    * Tasty
    * Two teams start in the filling and work outwards 

## When would you use each kind of test? 🤔

**Unit testing** should be used as you're writing the code :computer: and should be used frequently!

**Integration testing** can only be used once unit testing has been done. If you start these more complex tests without checking each component first, it's hard to pinpoint where your code is going wrong. :confused:

<!--

## Mob notes - the RAW, uncollated notes for people who want to dive deep

Spend some time doing research and write whatever you find relevant/helpful here under your name heading. Then we'll look at the notes, see what themes emerge, and write a 'clean' version in the next section.

### Kate

#### Unit testing 

* _' It is a testing method by which individual units of source code are tested to determine if they are ready to use.'_ - [Guru99 blog](https://www.guru99.com/unit-test-vs-integration-test.html)
* _'It helps to reduce the cost of bug fixes since the bugs are identified during the early phases of development life cycle.'_ - [Guru99 blog](https://www.guru99.com/unit-test-vs-integration-test.html)
* Conducted by the developers, not testers
* 'White box testing' - tests the software solution's internal coding and structure. Based on the inner workings of the application. _'It focuses primarily on strengthening security, the flow of inputs and outputs through the application, and improving design and usability.'_
    * How to white box test? TDD! Create tests and pass them.
* Can be performed by any time
* Easier to find errors since you're working in bite-sized chunks
* But cannot verify whether your software is working with external dependencies
* Devs who are testing must know the software and all its units very well
* _'If your test uses some external resource, like the network or a database, it’s not a unit test.'_ - [Codeutopia](https://codeutopia.net/blog/2015/04/11/what-are-unit-testing-integration-testing-and-functional-testing/)
* _'Unit testing is the only testing method which also helps you write better code – Code that’s hard to unit test usually has poor design.'_ - [Codeutopia](https://codeutopia.net/blog/2015/04/11/what-are-unit-testing-integration-testing-and-functional-testing/)
* _'You can use unit tests to help design your code and keep it as a safety net when doing changes'_ - [Codeutopia](https://codeutopia.net/blog/2015/04/11/what-are-unit-testing-integration-testing-and-functional-testing/)
* _'Unit tests are also great for preventing regressions – bugs that occur repeatedly'_ - [Codeutopia](https://codeutopia.net/blog/2015/04/11/what-are-unit-testing-integration-testing-and-functional-testing/)

#### Integration testing

* Conducted by testers, not the developers who have written the code
* Tests integration between the disparate modules that the devs have created, and how they gel together.
* Can be performed in a 'bottom-up', 'top-down', or 'big bang' method.
    * Bottom up: Lower level modules are tested with higher levels modules until all modules have been tested. Can be done before all modules are finished, which can speed things up. But critical modules which are prone to defects may not be tested until last, which isn't ideal.
    * Top down: Follows the control flow of the software system, testing big modules first down to smaller modules. Easier to pinpoint faults, and early prototypes can be made and tested while the rest is worked on. Critical modules tested as priority. But smaller modules may not get as much testing.
    * Big bang: components integrated together all at once, then tested. Convenient for smalls systems. But can only be done after all modules are done, and can be difficult to figure out where the bugs are. 
* Must be performed after unit testing
* 'Black box testing' - focuses on inputs and outputs of the software system, so the testers don't have to know the code very well like the devs who do unit testing. Test the functionality of the software without looking at the code structure.
* Verifies that your software can work well with its external dependencies
* Harder to find errors since you're combining lots of parts
* _'while unit tests are isolated from other components, integration tests are not...'_
* Verifying that two different systems, like a database and your app, work well together requires integration testing
* Because integration tests often require complex steps, i.e. setting up a test database, it's recommended to focus on unit tests and only do integration testing where required

### Jessie

Integration Testing - it is also sometimes called:
* 'I & T' (Integration and Testing)
* 'String Testing' 
* 'Thread Testing'.


**Why do Integration Testing?:**
Unit tests check smaller code units. If unit tests cover the whole code base, why use integration tests?

* A Module/unit is usually designed by an individual developer whose understanding and programming logic may differ from other programmers. Integration Testing becomes necessary to verify the software modules work in unity.
* During module development there's likely to be changing requirements. These new requirements may not be unit tested and hence system integration Testing becomes necessary.
* Interfaces of the software modules with the database could be erroneous.
* External Hardware interfaces, if any, could be erroneous.
* Inadequate exception handling could cause issues.

**Approaches for Integration Testing:**
* Big Bang Approach:
    * As it sounds! Everything combined and tested at once. 💥
    * Advantages:
        * convenient on a small scale
    * Problems: 
        * hard to localize faults 
        * easy to miss areas in large systems and not test
        * can only begin once the whole system is built
        * doesn't priotisise more critical modules
 * Incremental Approach: 
     * Combine 2+ logically related modules and test.
     * Combine further modules, testing on the way
     * Continue until whole system is integrated, tested and functioning
     * (this is clearly a way better approach...) 👍🏼
     * Requires **stubs** and **drivers** - dummy programs to simulate running the programme, replacing actual other modules:
         * **Stubs** are called by the Module under Test.
         * **Drivers** call the Module to be tested.

Incremental Approach is is further divided into:
* Top Down Approach
    * Higher UI levels tested first
    * get early prototype
    * but need lots of stubs!
* Bottom Up Approach
    * Lower levels tested first (e.g. basic logic and backend not DOM manipulation)
    * Doesn't necessarily prioritise critical UI modules.
    * Don't get early prototype
* Sandwich Approach - Combination of Top Down and Bottom Up

**Why is it cool?**
Requires strong understanding of application architecture and how components work together.

**Integration Test procedure**

1. Prepare the Integration Tests Plan
2. Design the Test Scenarios, Cases, and Scripts.
3. Executing the test Cases followed by reporting the defects.
4. Tracking & re-testing the defects.
5. Steps 3 and 4 are repeated until the completion of Integration is successfully.

Other common type of testing:
**Acceptance testing** — Testing an application in the browser or on a device to analyze the performance of the entire application.

### Sangita
Unit testing:
Unit tests really do help enforce IOC. Without unit tests the onus is on the developers to make sure they meet the requirements of well written code
For small discrete units of functionality that may or may not make up an individual user story by itself - for example, a user story which says that we retrieve all customers when we access a specific web page can be an acceptance test (simulate hitting the web page and checking the response) but may also contain several unit tests (verify that security permissions are checked, verify that the database connection queries correctly, verify that any code limiting the number of results is executed correctly) - these are all "unit tests" that aren't a complete acceptance test.
white-box-testing
Integration testing:
Simply, test that different component parts of your system integrate correctly - for example - maybe you simulate a web service request and check that the result comes back. I would generally use real (ish) static data and mocked dependencies to ensure that it can be consistently verified.
black-box-testing

A unit test is a test written by the programmer to verify that a relatively small piece of code is doing what it is intended to do. They are narrow in scope, they should be easy to write and execute, and their effectiveness depends on what the programmer considers to be useful. The tests are intended for the use of the programmer, they are not directly useful to anybody else, though, if they do their job, testers and users downstream should benefit from seeing fewer bugs.

Part of being a unit test is the implication that things outside the code under test are mocked or stubbed out. Unit tests shouldn't have dependencies on outside systems. They test internal consistency as opposed to proving that they play nicely with some outside system.

An integration test is done to demonstrate that different pieces of the system work together. Integration tests cover whole applications, and they require much more effort to put together. They usually require resources like database instances and hardware to be allocated for them. The integration tests do a more convincing job of demonstrating the system works (especially to non-programmers) than a set of unit tests can, at least to the extent the integration test environment resembles production.


### Michael

> Let’s consider the making of a car. Single-class testing is akin to testing each nut and bolt separately. Imagine testing of such components brought no issue to light. Still, it would be very risky to mass manufacture the car without having built a prototype and sent it to a test drive.

[A Java Geek](https://blog.frankel.ch/unit-test-vs-integration-test/)

>* **Unit tests** ensure that individual components of the app work as expected. Assertions test the component API.
>* **Integration tests** ensure that component collaborations work as expected. Assertions may test component API, UI, or side-effects (such as database I/O, logging, etc…)

>**Unit tests should be:**

>* Dead simple.
Lightning fast.
A good bug report.
What do I mean by “a good bug report?”

>I mean that whatever test runner and assertion library you use, a failing unit test should tell you at a glance:

>* Which component is under test?
>* What is the expected behavior?
>* What was the actual result?
>* What is the expected result?
>* How can the behavior be reproduced?

https://www.sitepoint.com/javascript-testing-unit-functional-integration/

**Test Types**
In general, the most important test types for a website are:

* Unit Tests- Testing of individual functions or classes by supplying input and making sure the output is as expected.
* Integration Tests- Testing processes or components to behave as expected, including the side effects.
* UI Tests- (A.K.A Functional Tests) Testing scenarios on the product itself, by controlling the browser or the website, regardless of the internal structure to ensure expected behavior.

https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2018-f68950900bc3

>A unit test runs some code over a segment of your program checking the input and output. These tests allow developers to check individual areas of a program to see where(and why) errors occur.
>
>This comes with an inherent understanding of what you’re trying to test for and how the code should function. Checking for bugs and errors can only be useful when you know exactly what you’re looking for.

[JS Unit Testing For Beginners](https://designmodo.com/test-javascript-unit/)

https://www.smashingmagazine.com/2012/06/introduction-to-javascript-unit-testing/

What’s in a good test failure bug report?
* What component are you testing?
* What should it do?
* What aspect of the component do you need to test? (e.g. test it returns a function, compare the value of output, test number of items in array)
* What was the output (actual behavior)?
* What was the expected output (expected behavior)?

https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d
-->