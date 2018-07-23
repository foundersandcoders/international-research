# Topic 3 - Packaging

## What is packaging?

A Package contains metadata, such as the software's name, description of its purpose, version number, vendor, scripts, and a list of dependencies necessary for the software to run properly. Upon installation, metadata is stored in a local package database.

In Node.js, a package is defined as:

"A folder containing a program described by a package.json file."

We have all already created a package already when we run npm init. We are asked for information such as name, description, version etc.. which are then stored in package.json

## What are dependencies?

Defintion: A dependency is a package that our software requires to run properly.

In our world, a dependency is a 3rd party, non-core module that is required by your project in order for it to run properly.

### Why are dependencies useful?

They save time and effort. We don't want to reinvent the wheel. If we can leverage modules created by others, we don't need to spend time creating the code ourselves and also it may be a better quality.

### But what are the challenges?

1.  Version Conflicts
2.

## NPM

#### NPM: What is a package manager?

####

NPM node package manager !
managing all the packages you downloaded.

managing means:

- Make it more readable and easy to reach the packagaes you installed
- Manage all the packages important information in one file; such as scripts,urls,descriptions & names...
- Block any conflicts between the different packages helping with dependencies

## NPM Init & Package.JSON

npm init <initializer> is used to set up a new or existing npm package.

Each init of a Node project creates a package.json containing essential information about the project such as name, description, version and dependencies.

## Using an Installed Package

Step 1. Assign the package to a variable using require e.g var lodash = require('lodash');

Then use packageName.functionName to access the methods of the package e.g. var output = lodash.without([1, 2, 3], 1);
console.log(output);

### Install it !

###

using this command line in your terminal

```
npm install
```

be aware of the difference between installing the package **globally**, installing it as a **dependency**, or installing it as a **development dependency**

installing it globally will install it in your local machine and not in specific project.
while installing it dependency will install it on your specific project.
devDependency will install it for your developing goal and not for the client, which means your published code doesnt depent on this package.

#### Why should we avoid installing globally ?

![](https://i.imgur.com/rncdpiA.png)

just like how global variables are kind of gross.
imagine like every time you want to use variable in your code you define the var in your local machine and will be accessible from any other project you build, it's completly mess.

installing the package for all your projects not a good idea because every project should be completely self-contained. if you just install globally each package your computer will contain bunch of needless packages.

## Package Files

### Where does NPM install to?

#### Non-global

Non-global libraries are installed the node_modules sub folder in the folder you are currently in.

#### Global Files

You can run npm list -g to see where global libraries are installed.
![](![](https://i.imgur.com/g6v1wYF.png)

On Unix systems they are normally placed in /usr/local/lib/node or /usr/local/lib/node_modules when installed globally.

You can run npm list to see the installed non-global libraries for your current location.

## Where package files should not live...

On GitHUB. The node_modules folder is large in size and will take up a lot of space on GitHUB. It will also take your other team members a long time to clone or pull the project.

### .gitignore

The node_modules folder should be added to .gitignore to avoid uploading all files to GITHub. For example:

![](https://i.imgur.com/Qhc5Ts3.png)
