# CI-til-I-die :octocat: ![Travis Build Status](https://api.travis-ci.org/fac-14/CI-til-I-die.svg?branch=one)

A repo to demonstrate Continuous Integration(CI) :goat:

[See it on Github!](https://github.com/fac-14/CI-til-I-die) :v:

## Meet Grady Booch: His boss is not happy :rage:
![Grady Booch in trouble](https://modeling-languages.com/wp-content/uploads/2014/10/image-83472-full.jpg)
* He has just added a cool new feature to a site that wasn't tested properly
* Now the site is broken :skull:
* Bad Grady Booch.

## What happened Grady? :neutral_face:
![Grady Booch contemplating what went wrong](https://cdn-images-1.medium.com/fit/c/200/200/0*u8Uxdd3h6A7L-P7G.jpeg)
* My colleague changed some code that my feature depended on...and then...
* They didn't consider all the user cases in their tests...and...
* Now when I wrote my cool new feature I didn't have access to my colleague's manual tests...
* Now both our features aren't working and the whole project is f---ed :bomb:


## Continuous integration could be the solution for you, Grady?
### Some benefits to using continuous integration
* **Integration** is the process of pulling **every developer's work** into one common branch.

* **Reduced integration risk**: Integrating frequently makes sure that one dev's code will work happily alongside another's.

* **Higher code quality**: Following TDD principles so bugs are squashed nice and early :shoe: :bug: 

* **The code in version control works**: If you commit something that breaks the build, you and your team get the notice immediately and the problem is fixed before anyone else pulls the “broken” code. :love_letter:

* **Less time deploying**: More time to comb that beautiful mane. 🦁

* **Reduced friction between team members**: You don't need to worry about falling out with your developer buddies, Grady - CI will reduce the chance of your code messing with another dev's work. :crying_cat_face:

* **Increased confidence and morale**: People that don’t work for fear of breaking something, are more likely to produce better results and can focus their energy and concentration on producing instead of worrying about potential consequences of their actions.

:rotating_light: All these benefits add up to **new team members** having a much easier time getting into the project. Having a clear vision of the building process can greatly speed up adaptation of the newest dev on the team! :rotating_light:

![Grady Booch finally welcoming new competent co-workers](https://i.imgur.com/1VaB9u4.jpg)


# I love it! How can I use it?

Follow [this handy guide](https://github.com/dwyl/learn-travis) from the lovely folks at DWYL

## TL;DR:

## 1. Make a repo on Github
* Stick your amazing project in a Github repo
* Don't forget to add tests! ✅

## 2. Use a flashy tool (Travis!) to sync your changes

![Travis single, why does it always rain on me?](https://i.imgur.com/nvX3FaG.jpg)

* Make an account on: travis-ci.org
* Activate travis on the repo you want to add continuous integration to by adding a`.travis.yml` file to the root of the repo.
[simple version](https://docs.travis-ci.com/user/getting-started/) :smile:
[more options](https://docs.travis-ci.com/user/customizing-the-build/) :scream:
* To add a community like FAC14 (and have access to the repos in there) you'll need the community's owner to grant access. :+1: 
* At `git push` Travis automatically runs your test script :boom:
* You will recieve a helpful email: :love_letter:
    * To remember the fun times you have had together 
    * To let your colleagues know **when** you have broken something so they don't pull your broken code :two_hearts:
* Keep adding to your repo, safe in the knowledge that your code is always tested every time you push or make a pull request.
* Add your cool build status icon to your readme, e.g.  ```https://api.travis-ci.org/fac-14/CI-til-I-die.svg?branch=master```
![build status](https://api.travis-ci.org/fac-14/CI-til-I-die.svg?branch=master) so everyone knows how sweet your code is 🤓

Look [here](https://docs.travis-ci.com/) for documentation on all the other nifty things travis can do, like:

* deploy to GitHub pages
* [Test and deploy apps on Heroku](https://docs.travis-ci.com/user/deployment/heroku/)

Other CI tools you can use:

* [CircleCI](https://circleci.com/)- (Hosted service)
* [Shippable](https://www.shippable.com/) - (Hosted service)
* [Jenkins](https://jenkins.io/) - (In-House CI Server)


### How does that sound, Grady? :smirk:

![Grady Booch](https://www.singularityweblog.com/wp-content/uploads/2014/02/Grady-Booch-2.jpg)

## I wish I thought of that! 

You did Grady! :clap: :ok_hand:

# Any advice for us? :warning: 

![A fool with a tool is still a fool](https://image.slidesharecdn.com/thefoundationandfutureofsourcing-cathey-160302212455/95/the-foundation-and-future-of-sourcingcathey-50-638.jpg?cb=1466722278)

Thanks buddy.
