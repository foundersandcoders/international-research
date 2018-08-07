# Packaging Group Research

## Dependencies (Simon)

### What are packages? 
A Package contains metadata, such as the software's name, description of its purpose, version number, vendor, scripts, and a list of dependencies necessary for the software to run properly. Upon installation, metadata is stored in a local package database.

**Example:**
* node.js has a package manager called npm.
* Running npm init creates package.json file that specifies packages and dependencies of your project.


```
// package.json
{
"name": "it-depends",
"version": "1.0.0",
"main": "index.js",

"dependencies": {
"express": "^4.16.2",
"moment": "^2.20.1",
"mongodb": "^3.0.2"
},

"devDependencies": {
"nodemon": "^1.14.12"
}
}
```

### What are dependencies?
1. packages that our software requires to run properly.
2. code written by others for you --> you depend on someone elses code

### Why should you use them? 
1. in order not to reinvent the wheel! Save yourself energy and time.

2. to be able to use dedicated, proven, well-tested libraries and tools that somebody has already authored. 

### What are frequent problems? 
**1. Risk management issues**

> Why is it bad to have many dependencies, really, why do you care?
> 
![](https://media1.giphy.com/media/vvuM9kHnq7Kgw/giphy.gif)

**Because each dependency is a risk.**


>Recently, security researchers analyzed 133,000 websites for outdated JavaScript libraries. Of the websites analyzed, 37% loaded insecure JavaScript, either directly or via a third-party service, such as advertisers.
>

![](https://image.ibb.co/gM0GJo/Bildschirmfoto_2018_07_24_um_15_18_11.png)


Not keeping a application’s JavaScript packages up-to-date can be challenging. As a project begins to grow, so too does the time and effort involved in ensuring that all of the project’s dependencies are adequately patched.

**2. Dependency tree chaos**

![](https://image.ibb.co/bSTYDo/Bildschirmfoto_2018_07_24_um_16_27_27.png)

**Example npm** 
Version syntax:(MAJOR.MINOR.PATCH) —> e.g. 2.3.5

**Symbols to remeber:**

* ^ (caret) means that changes are allowed up to the MINOR part.
* version ^2.2.4  means that both 2.2.5 as well as 2.3.0 will be considered valid and “the latest” of them will be used if available.

* ~(tilde) means that only PATCH segment changes are allowed.
* ~2.2.4 —> the only valid candidate out of those two mentioned would be 2.2.5.

**Why chaos?**

```
"dependencies": {
"express": "^4.16.2",
"moment": "^2.20.1",
"mongodb": "^3.0.2"
},
```
You depend directly on version 4.16.2 of express. 
Express depends on accepts in form of ~1.3.4
accepts in turn depends on mime-types in the ~2.1.16 range....

**Run npm install:** different update rules involve different dependency trees. 
Bad if you work on larger projects with several developers over a long period...

### Conclusion
The trick is to keep your dependency tree in a known state and under your full control, which are often missing pieces in many projects.
![](https://media2.giphy.com/media/K2ZWOSOLLYsAE/giphy.gif)
Luckily there are a few tools and services to help you (e.g. npm-check package). 

* [NPM CHECK](https://www.npmjs.com/package/npm-check)
* [SNYK](https://snyk.io)
* [SHRINKWRAP](https://docs.npmjs.com/cli/shrinkwrap)
* [GREENKEEPER](https://greenkeeper.io)


---


## NPM 
 Package manager is a piece of software that lets you manage the dependencies (external code written by you or someone else) that your project needs to work correctly.
 
![](https://media.giphy.com/media/l0MYRamKpDTaySHEQ/giphy.gif) 

 
### Package managers generally help you juggle:

#### Project Code:
This is the code of your project for which you need to manage various dependencies.

Typically, all of this code  is checked into a version control system like Git.

#### Manifest file:
This is a file that keeps track of all your dependencies (the packages to be managed). 

It also contains other metadata about your project. In the JavaScript world, this file is your **package.json**

#### Dependency code:

This code constitutes your dependencies. 

It shouldn’t be mutated during the lifetime of your application, and should be accessible by your project code in memory when it’s needed.

#### Lock file:
This file is written automatically by the package manager itself. It contains all the information needed to reproduce the full dependency source tree. It contains information about each of your project’s dependencies, along with their respective versions.

npm init is used to set up a new or existing npm package.

Each init of a Node project creates a package.json containing essential information about the project such as name, description, version and dependencies.

how to use installed package in your code:
**var package_to_use = require('package_to_use');**

in the package
**module.exports = package_to_use;**
 


---


## NPM Install 
Npm packages can be installed either globally or locally. Choosing an installation method depends on how you intend to use it.

![](https://www.veteranstoday.com/wp-content/uploads/2017/10/globalization-11.jpg)

**Globalisation can be good!**
You might want to install a package globally when you intend to use it e.g. to launch a file that isn't part of an overarching project.
	For instance, if you install the `http-server` package globally, you can create a server file from the command line in whatever directory you are, without having to navigate to a project directory.

To install e.g. the `http-server `package globally, type in your terminal:
` npm install http-server -g` 

**... but often isn't. Here's why you'll often install a package as a dependency ...**
Generally, a package is installed locally, i.e. within a project, if the project needs that package in order to work.

**... and here's why you might *not* want to install a package globally:**
*... it makes sharing the project with others potentially harder.*
Unless you include a package as a requirement in the `package.json` of a project that is open-source and/or public (or at least shared with other developers), you'll have to warn others that they'll need to install that package for things to work. 

You can do that manually and explicitly in your `README` file, but installing all required packages locally makes things easier and prevents problems that may arise because e.g. you forgot to warn others or because others forgot to check the `README`.

*... it adds an extra step to the procedure others will need to follow in order to work on the project* 

*... it makes collaboration prone to conflicts*
Say you have version 1 of a package globally installed and someone else has version 4. When you both come to work on the same project, you may run into conflicts.

*... **you** may run into conflicts*
This could happen if you  use an updated version of a package for one project, but have another version of the same package globally installed.

**How do I install a package locally as a dependency?**
You use either the command
`npm install --save` plus the name of the package
or
`npm i -S` plus the name of the package.

**How and why do I install a package locally as a development dependency?**
**How?**
You can use either
`npm install --save-dev` plus the name of the package
or
`npm i -D` plus the name of the package.

**Why?**
The short answer seems to be:
*dependencies* --> *necessary to run* e.g. a library
*devDependencies* --> *necessary for developing* e.g. testing.

The longer answer is that if you're working on a programme that you will be sharing, others will need the packages you used for your code to run (i.e. your project's dependencies), but may not need e.g. any external test packages you may have used - they may even wish to use a different test package. These packages, which you used to develop, but not to run, your programme, are your project's devDependencies.


*Further reading*
Generally on dependencies and why you might install them globally or locally:
https://www.smashingmagazine.com/2016/01/issue-with-global-node-npm-packages/
Development dependencies
https://medium.com/@dylanavery720/npmmmm-1-dev-dependencies-dependencies-8931c2583b0c
https://github.com/npm/npm/blob/2e3776bf5676bc24fec6239a3420f377fe98acde/doc/files/package.json.md#devdependencies
(For the curious, there are also peer dependencies:
https://nodejs.org/en/blog/npm/peer-dependencies/
---


## Package Files 

### Where does NPM install packages? 

There are 2 places to install packages:

#### LOCAL

If you want to depend on the package from your own module. 

**And where do they go??**
The node_modules sub folder in the folder you are currently in.

![](https://i.imgur.com/072gJcN.png)

You can check by running this in your work folder using: ***npm list***


#### GLOBAL

If you want to use a package as a command line tool and no matter which directory is current. 

**And where do they go??**

You will find a node_modules folder in /usr/local or wherever node is installed.

Here's the route to mine:

![](https://i.imgur.com/iqEHPW9.png)

*Psst... they are hidden so you'll need to show your hidden files to see in GUI*

Now let's check whether your global packages are in the same place...

**RUN THIS: *npm list -g***


### Why is it important to make sure that installed packages aren't included in your repositories? 

Because Github is amazing, and installed packages on our repositories do this:

![](https://media.giphy.com/media/LaEZzr50dsKiY/giphy.gif)

The node_modules folder is large and takes up LOTS of space. 

Think about all the repos we alone have created to date. Now think if we'd uploaded the entire node_modules folder to every single one of these repos...

.
.
.
.

... just letting that sink in...

.
.
.
.


You also cause your team this:

![](https://media.giphy.com/media/o5oLImoQgGsKY/giphy.gif)

The bigger the files the longer it'll take to download when your team clone the repo. 

We experienced this first hand! It's not fun!!!!


### How do you prevent Git from including these files in your repository?

**.gitignore** is here to save the day

but there's a catch...

![](https://media.giphy.com/media/asH1RXz0bdTzy/giphy.gif)

# **You must have the files you want to ignore in your .gitignore BEFORE committing.**

You cannot force a file that is already committed in the repo to be removed retroactively just because it is added to the .gitignore

A possible way to do this ([courtesy of StackOverflow](https://stackoverflow.com/questions/6535362/gitignore-after-commit)) is:

**git rm --cached** 

--cached means you keep the local copy but remove from the repo. So for example if you want to remove all the "exe" files from your repo:

**git rm --cached /\*.exe**

*WARNING: I have not tried this so perhaps easier for us all to remember to set up .gitignore at the start of our repo and whenever you add a new dependency or file you wish to ignore*

It's like remembering your keys before your leave the house! 

**TO HELP WITH THIS...**

Useful gitignore rules to keep in mind:
https://gist.github.com/octocat/9257657

You can also create a global gitignore configuration

Useful global gitignore rules to keep in mind: 
https://gist.github.com/octocat/9257657


To create useful gitignore files, this site seems great: https://www.gitignore.io/
Here's what it pulled up for VSCode and Node:
https://www.gitignore.io/api/node,visualstudiocode

![](https://i.imgur.com/zFkUcCh.png)



### Useful links

Beginner's Guide to NPM: https://www.sitepoint.com/beginners-guide-node-package-manager/

gitignore manual: https://git-scm.com/docs/gitignore

Collection of useful gitignore packages: https://github.com/github/gitignore

NPM-Folders documentation is really clear: https://docs.npmjs.com/files/folders