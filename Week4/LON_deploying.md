# BRINGING SOME YaaS TO YOUR SaaSsy PaaS

![](https://media.giphy.com/media/6FJh5gupDGd9u/giphy.gif)

# DEPLOY THE KNOWLEDGE

# Types of cloud services 

Cloud services are typically categorised based on access, size and proprietorship. 
The following are different deployment models that are used. 

### Public Cloud
This service is provided by an external service provider, it can be operated by whoever uses it. The user however has no say over the location of the infastructure
* Reasonable levels of security

* Easy to implement

* Cost-effective

* Low operational cost
### Private Cloud
Private cloud is owned by a particular company and is designed to meet their own specifications. They have the advantage of being able to change in order to meet data management and uptime needs. Other advantages include: 
* Maximum levels of reliability and Scalibility 
* Designed for enterprises and businesses
* Greater control over cloud infrastructure
* Users get both network access and computational resources


### Hybrid Cloud

As the name suggests hybrid cloud takes aspects of both private and public cloud deployment. It mixes private cloud, with third-party public cloud services with communication between the two or more platforms. The benefits of this are mainly in terms of cost, flexibility and personalisation. Establishing a hybrid cloud requires the availability of:

* A public infrastructure as a service (IaaS) platform, such as Amazon Web Services, Microsoft Azure or Google Cloud Platform;
* The construction of a private cloud, either on premises or through a hosted private cloud provider;
* A connection between these two enviroments




### Platform as a Service (PaaS)

A fairly new technology in the cloud computing scenario when compared to IaaS, Platform as a Service (PaaS) runs atop IaaS. It is mainly targeted towards the developer as it allows them to build applications and services over the internet.

### Infrastructure as a service (IaaS)
Infrastructure as a Service or Cloud Infrastructure is a self-service codes that aims to manage and monitor remote datacenter infrastructure for the following functions: compute, storage and networking.

### Software as a service (SaaS)
Software as a Service (SaaS) is perhaps the most commonly used cloud deployment model. This is because the web delivery model eliminates the need to install and run applications on your computer, apart from making it easier for businesses to streamline their maintenance and support.





# Environment variables: 

Environment variables are what all the cool kids are doing these days to store all their private keys, passwords and sensitive details outside of their code. They are `KEY=value pair` stored on the local system where your code/app is being run and is accessible from within your code. Without stealing the thunder of the other research group, they *separate the concerns* of your code and your deployment. 

**They are not constant variables in your code, ok** :information_desk_person: 

You shouldn't store environment variables in a public place :no_good: because then hackers will invade your server and steal everything you love, and then you'll have to hunt them back down like Liam Neeson in *Taken* :scream: and that means **less time down the pub** :beers: 

If you have Mac or Linux you've definitely got a bunch of environment variables already! So cool! Type `printenv` from a terminal and have a ganders. BUT DON'T SHARE THEM, THAT'S THE ENTIRE POINT :-1: 

We know what you're thinking: 'this is all very well and good, but how do I get at these from node?' :kissing_closed_eyes: `process.env` :kissing_closed_eyes: ([docs](https://nodejs.org/api/process.html))

![](https://i.imgur.com/AQePrlg.png)

the only trickiness with this is that if your terminal doesn't save envionmental variables across sessions (don't @ us - Google yours) you'll need to do this every single time you relaunch the terminal window. Jeepers! 

**BUT WAIT:** our friends/the clever boffins at dwyl even made env2 as a neat way to create and manage *local* persistent environment variables for each project. Nifty! 

An alternative popular npm module is [dotenv](https://www.npmjs.com/package/dotenv). 

Both modules import an .env file of environment variables in your project folder into something you can easily access in node. 

Don't forget, if you're using an .env file to store your environment variables please, *please* **please** do make sure it's in your `.gitignore`. 

![](http://i65.tinypic.com/2zevuvb.png)

*I NEED MOAR READING:* :book: :eyes:
* [The Twelve-Factor App](https://12factor.net/config) (these gandalfs teach you how to be a mobile web app wizard too)
* [DWYL](https://github.com/dwyl/learn-environment-variables) (Prince Dwylliam goes and does it again)

**tl;dr** These various elements of your deployment - your staging, production and external services - are likely to change across deployments, and especially when you head into using a PaaS... 

## What the heck is a PaaS

* Platform as a service = a category of cloud computing :cloud: :computer: services that provides a platform allowing customers to develop, run, and manage applications without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app :rocket: 
* PaaS offers businesses a great deal of flexibility. It can be used for rapid app deployment, in-house testing, or collaborative development between geographically dispersed teams :earth_africa: 
* PaaS can allow developers to produce, test and deploy applications as rapidly as possible, ensuring they work as they should and can be rolled out already fit for purpose. 
* There's also less maintenance involved, as the PaaS provider will manage the hosting and backend, choosing the best infrastructure for the individual application, while developers and those less experienced can focus on creating great, well-functioning products without worrying what’s going on in the background :muscle: :boom: 
* PaaS providers normally offer a much greater level of scalability than is possible by hosting applications on a company’s own server infrastructure. Many PaaS providers offer features such as auto-scaling, allocating increased resources and bandwidth to your applications to cope with traffic spikes as they occur. That means customers won’t be left with blank screens or long load times if demand for a web app grows quickly or unexpectedly.

# I'M READY... I NEED A HERO*KU*

## What is this Heroku

* Heroku is a cloud platform based on a managed container system, with integrated data services and a powerful ecosystem, for deploying and running modern apps.
* All Heroku services are hosted on Amazon's EC2 cloud-computing platform, which is part of Amazon Web Services (AWS), which is also a PaaS - **PAAS-CEPTION!!!!!!!**

* Started out Ruby only, but now supports Java, Node.js, Scala, Clojure, Python, PHP, and Go.

## How to host your first app on Heroku in 10 easy steps!

Hosting an app on heroku is no more difficult than pushing a version of your project to gihub _(so, quite difficult?)_. 

These steps shouldn't look very foreign. It's extremely similar to git. 

1. Create a Heroku account 

2. Click 'create new app!' - select node.js, if that's what you're using.

3. Download the command line interface for heroku (according to your system, this is mac version)

```
brew install heroku/brew/heroku
```
4. Heroku commands now work in your terminal! Log in to heroku with...

```
heroku login
```

5. Heroku needs node, npm and git. Check you have them installed: 

```
node --version
```

6. Prepare the app! Heroku have a handy example app you can clone from git and deploy (code  looks weird though, as they use express)

```
git clone https://github.com/heroku/node-js-getting-started.git
```
7. Nagivage to the directory you are deploying:

```
cd node-js-getting-started
```

8. Create the app on heroku!

```
heroku create
```
9. It gives you a random name. I got https://tranquil-basin-57311.herokuapp.com/

### deployment time 💥💥💥

10. Then **push to heroku master** - is this the only time pushing to master is acceptable?

```
git push heroku master
```

### Its now [deployed](https://tranquil-basin-57311.herokuapp.com/)! It's that simple!! 🎉 

To check an instance of the app is running 

```
heroku ps:scale web=1
```

A shortcut to open your deployed app:
```
heroku open
```

**Can I go home now?**

No, there's more to understand about heroku. :crystal_ball: 

* Learn to see your **logs** with ` heroku logs --tail`. This is a live stream of events happening on your web page.
* Define a **Procfile** including something like: `web: node index.js`. A procfile is a text file in the root directory of your application that explicitly declares what command should be executed to start your app. `Web` is the process type and `node index.js` is the command to run the app.
* **Scaling** #techBuzzwordOfTheDay 
    * The simple app above is running on a single 'Dyno' - a little container running the command in the Procfile. You can check the number of dynos running with `$ heroku ps`
    * By default, your 'hobbyist' account app is deployed on a free dyno. Free dynos will sleep after a half hour of inactivity (if they don’t receive any traffic). This causes a delay of a few seconds for the first request upon waking. 
    * **If my app is so popular that it gets loads of traffic, will I get a bill for $1000000?** No,  Free dynos also consume from a monthly, account-level quota of free dyno hours - as long as the quota is not exhausted, all free apps can continue to run. Heroku free account doesn't ask for your card details.
    * `heroku ps:scale web=0` will scale your application to zero dynos and users will get an 'Application error'
    * `heroku ps:scale web=1` will scale your application to 1 dyno and it will work again. Yay!
* Your **package.json** file is very necessary to host your project on Heroku. It tells Heroku it is a node project and what the dependencies are :)
* Run the project locally with `$ heroku local web`
* **How can I update the hosted version with my local changes??** Funny you should ask... 
`git add .`
`git commit -m "change made"`
`git push heroku master`
_"omg so easy its just like git :D"_ :nail_care: 
* You can get add ons for heroku that do things like customise logs and send you alerts when everything goes to shit. I won't go into this here.




### PaaS Cloud platforms

* Amazon Web Servies
* Google App Engine
* GOV.UK??????
* Cocaine (Configurable Omnipotent Custom Applications Integrated Network Engine)
* IBM Cloud (nee IBM BlueMix)
* Microsoft Azure
