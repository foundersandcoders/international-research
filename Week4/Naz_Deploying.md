# **Links :**
* **Cloud Platforms :**
  * Heroku https://www.heroku.com
  * AWS (Amazon) https://aws.amazon.com
  * Digital Ocean https://www.digitalocean.com
  * Other -> https://www.capterra.com/cloud-management-software

*  **How to (easily) set up Node environment variables in your JS application :** Important++
  https://codeburst.io/how-to-easily-set-up-node-environment-variables-in-your-js-application-d06740f9b9bd

* **Deploy Node.JS Apps to Heroku**
https://www.youtube.com/watch?v=AZNFox2CvBk


* **Cloud Computing Services Models** - IaaS **PaaS** SaaS **Explained**
https://www.youtube.com/watch?v=36zducUX16w

* **Environment Variables in Node.js**
https://www.youtube.com/watch?v=HRBNeERE5PU

* **What modules might you use to help manage environment variables?**
http://modules.sourceforge.net/

# What Is PaaS ?
**Platform as a service (PaaS)** ++is a cloud computing model in which a third-party provider delivers hardware and software tools++ -- usually those needed for application development -- to users over the internet. A PaaS provider hosts the hardware and software on its own infrastructure. As a result, PaaS frees users from having to install in-house hardware and software to develop or run a new application.

# PaaS - pros and cons :
**Platform as a Service (PaaS)**
* PaaS is a fairly new technology stack that runs on top of IaaS and was created with the developer in mind. With the PaaS platform, everything is provided except the application code, users, and data. Typically, when using a PaaS, the vendor maintains the application server, databases, and all of the necessary operating system components, giving you time to focus on the application code. Since the vendor manages that platform for you, it is often hard to open up ports that are not specifically called for the application server, runtime, or database in use. PaaS also provides features that are specifically meant for applications, including the ability to scale the application tier up based upon the user demand of the application. In most platforms, this happens with little-to-no interaction from the developer.

* **Pro:** PaaS provides a complete environment that is actively managed, letting you focus on your application code.

* **Con:** Developers are often restricted to certain major/minor versions of packages available on the system so that the vendor can manage the platform effectively.



**PaaS vs. SaaS vs. IaaS**
PaaS is one of three main categories of cloud computing services. The other two are software as a service (SaaS) and infrastructure as a service (IaaS).

# PaaS architecture and how it works:
PaaS does not typically replace a business's entire IT infrastructure. Instead, a business relies on PaaS providers for key services, such as application hosting or Java development.

A PaaS provider builds and supplies a resilient and optimized environment on which users can install applications and data sets. Users can focus on creating and running applications rather than constructing and maintaining the underlying infrastructure and services.

Many PaaS products are geared toward software development. These platforms offer compute and storage infrastructure, as well as text editing, version management, compiling and testing services that help developers create new software more quickly and efficiently. ++**A PaaS product can also enable development teams to collaborate and work together, regardless of their physical location.**++


# **What are Environment Variables?**
 Environment variables hold values related to the   current environment, like the Operating System or    user sessions.

**Path**
One of the most well-known is called PATH on Windows, Linux and Mac OS X. It specifies the directories in which executable programs are located on the machine that can be started without knowing and typing the whole path to the file on the command line.

Other variables might tell programs what kind of terminal is used (TERM on Linux/Mac OS X)

**Creating new environment variables**
In Windows, Linux and Unix, it's possible to create new environment variables, whose values are then made available to all programs upon launch.

You can use this when writing scripts or programs that are installed or deployed to multiple machines and need to reference values that are specific to these machines. While a similar effect can be achieved using program-specific configuration settings, it's easier to do this using an environment variable if multiple programs need to access the same value.

**Unix derivatives (FreeBSD, GNU / Linux, OS X)
Environment Variables in Linux are prefixed with a dollar sign ($) such as $HOME or $HOSTNAME. Many well-known and standard variables are spelled out in capital letters to signify just that. Keep in mind that variable names are case-sensitive, meaning that $User and $USER are entirely unrelated from the shell's point of view.**

Unix derivatives define system wide variables in shell scripts located mostly in the /etc folder, but user-specific values may be given to those variables in scripts located in the home folder (e.g., /etc/profile, $HOME/.bash_profile). The .profile file in the home folder is a common place to define user variables.

# Setting variables

These files are regular shell scripts and can contain more than just environment variable declarations. To set an environment variable, use export. To show your currently defined environment variables in a terminal, **run env**.

The export command is a standard way to define variables. The syntax is very intuitive. The outcome is identical for these two lines, but the first alternative is preferable in case portability to pre-POSIX Bourne shell is necessary.

var=value; export var
export var=value
The C shell and its descendants use a completely different syntax; there, the command is setenv.

- **WHAT IS PAAS?**
**Platform as a Service (PaaS) or application platform as a Service (aPaaS)**




- PaaS, is a category of cloud computing that provides a platform and environment to allow developers to build applications and services over the internet. PaaS services are hosted in the cloud and accessed by users simply via their web browser.


- **A PaaS provider** hosts the hardware and software on its own infrastructure. As a result, PaaS frees users from having to install in-house hardware and software to develop or run a new application.  


- **Software developers** can take advantage of a PaaS solution to build an application which they are planning to offer over the internet or software to be sold out of the box


- **Web developers can** use individual PaaS environments at every stage of the process to develop, test and host their websites

- http://www.clouds360.com/paas.php

---

 **deploying node.js app to heroku**

 - In many environments (e.g. Heroku), and as a convention, you can set the environment variable PORT to tell your web server what port to listen on.

- So process.env.PORT || 3000 means: whatever is in the environment variable PORT, or 3000 if the process.env.PORT is undefined.

 - So you pass that app.listen, or to app.set('port', ...), and that makes your server be able to accept a parameter from the environment what port to listen on.

![](https://i.imgur.com/0XwJZeh.png)
