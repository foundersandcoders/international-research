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

---

### Coverage criteria

To measure what percentage of code has been exercised by a test suite, one or more coverage criteria are used. Coverage criteria are usually defined as rules or requirements, which a test suite needs to satisfy.[4]
Basic coverage criteria

There are a number of coverage criteria, the main ones being:[5]

Function coverage – Has each function (or subroutine) in the program been called?
Statement coverage – Has each statement in the program been executed?
Branch coverage – Has each branch (also called DD-path) of each control structure (such as in if and case statements) been executed? For example, given an if statement, have both the true and false branches been executed? Another way of saying this is, has every edge in the program been executed?
Condition coverage (or predicate coverage) – Has each Boolean sub-expression evaluated both to true and false?
For example, consider the following C function:
~~~
int foo (int x, int y)
{
int z = 0;
if ((x > 0) && (y > 0))
{
z = x;
}
return z;
}
~~~
Assume this function is a part of some bigger program and this program was run with some test suite.

If during this execution function 'foo' was called at least once, then function coverage for this function is satisfied.
Statement coverage for this function will be satisfied if it was called e.g. as foo(1,1), as in this case, every line in the function is executed including z = x;.
Tests calling foo(1,1) and foo(0,1) will satisfy branch coverage because, in the first case, both if conditions are met and z = x; is executed, while in the second case, the first condition (x>0) is not satisfied, which prevents executing z = x;.
Condition coverage can be satisfied with tests that call foo(1,0) and foo(0,1). These are necessary because in the first cases, (x>0) evaluates to true, while in the second, it evaluates false. At the same time, the first case makes (y>0) false, while the second makes it true.
Condition coverage does not necessarily imply branch coverage. For example, consider the following fragment of code:
~~~
if a and b then
~~~
Condition coverage can be satisfied by two tests:

a=true, b=false
a=false, b=true
However, this set of tests does not satisfy branch coverage since neither case will meet the if condition.

