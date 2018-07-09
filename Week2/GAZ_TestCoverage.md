# Test Coverage

---

## What is test coverage?
In software testing, test coverage measures the amount of testing performed by a set of test. It will include gathering information about which parts of a program are actually executed when running the test suite in order to determine which branches of conditional statements have been taken.

In simple terms, **it is a technique to ensure that your tests are actually testing your code or how much of your code you exercised by running the test.**

---

## Why is test coverage useful?
* Finding area of a requirement not implemented by a set of test cases.
* Helps to create additional test cases to increase coverage.
* Identifying a quantitative measure of test coverage, which is an indirect method for quality check.
* Identifying meaningless test cases that do not increase coverage.

---

## What are Istanbul and nyc?
**Istanbul:**
A JavaScript code coverage tool written in JavaScript, with a purpose to report what lines, functions and branches did your TDDs cover, including both unit tests, integration tests and also browser tests. In other words, it's a tool that have been built to scale the amount of code that you are testing, which is computed over the compiler output not the original source code.
Branch (or branching, branched)refer to the act of switching execution to a different instruction sequence as a result of executing a branch instruction

**NYC:**
it's the NEW Istanbul command line interface, which have replaced the old Istanbul tool bin, in NYC, you can get reports on different scopes by using different command line flags, for example: --all flag will be examine all files that you have inside your project folder, and deal with them as they are JS files, which may(will) throw errors and make your test fail, from here comes the turn of Typescript compiler (you can find a resource to know more about it in references. below.) more and more, NYC is the easiest way to get a code coverage no matter the number of frameworks you are using, or how many subprocess you have in your code.

| Tables        | Istanbul           | NYC  |
| ------------- |:-------------:| :-----:|
| Definition of | istanbul is the code coverage tool that computes statement, line, function and branch coverage | nyc is the istanbul command line interface (replacement for the old istanbul bin |

---

## How would you use them to improve your testing?
Istanbul/NYC methodology of testing exists to tell programmers what and where the tests they have designed work, consider it as a map that tells you which ways you have completed and which you have not, how many steps have you been walking, and how many steps are left until you finally have tested everything properly. less talk, this is just another tool to support JavaScript programmers to keep tracking their code testing and know how well they have done it.

---

## Use Istanbul/nyc to calculate your code coverage for the TDD workshop.

**Istanbul**
~~~
npm run cover
~~~
~~~
npm i istanbul -D
~~~
~~~
"scripts": {
  "cover" : "istanbul cover test.js"
}
~~~
~~~
npm run cover
~~~
![alt text](http://www7.0zz0.com/2018/07/09/15/551179993.png "1")

![alt text](http://www9.0zz0.com/2018/07/09/15/491095001.png "2")

![alt text](http://www9.0zz0.com/2018/07/09/15/168517977.png "3")



