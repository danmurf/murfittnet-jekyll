---
layout: post
identifier: "blog123"
title: "CodeIgniter vs. Laravel"
date: "2016-03-08 22:06:00 +0000"
tags: [ "CodeIgniter", "Laravel" ]
permalink: "blog/codeigniter-vs-laravel"
---
It's not always easy to give a definite winner with these sorts of comparisons, as depends what your requirements and preferences are. So, here are a few areas worth thinking about when weighing up CodeIgniter against Laravel.

## Speed to learn
CodeIgniter is incredibly quick to learn; mainly because it's so easy to set up. You can just download the CodeIgniter package, unzip it to your WAMP or MAMP web root, and you're good to go. I think one of the main reasons CodeIgniter grew in popularity so quickly was because of how easy it was to install and learn. You also don't need to use the command line to develop with CodeIgniter.

Laravel takes a little more time to get to know. If you're only used to writing small php websites - processing forms, etc. - there's a lot to learn in terms of development workflow. You can't really download and install Laravel like you can with CodeIgniter. You need Composer, and the layout of the web root is a little different. As it happens, there's a pre-built development environment - Laravel Homestead - which makes all of this easy to set up, but that in itself will take a bit of time to learn. Not much time, but when comparing the speed to learn with CodeIgniter, I'm afraid I have to give this one to CodeIgniter as pretty much anyone that's ever written a PHP ''Hello World' should be able to set it up in no time at all. Also, one of the advantages of using Laravel is that is has some excellent features which speed up your development time. They speed it up, because you don't have to write so much code to add functionality. The down side of this is that you really need to learn how it works, so you can remain in control while you're building your app. You're almost having to learn another language (for example, Eloquent ORM). This is a good thing, and you should do it, but it does take a little longer to learn as a result.

## Speed to deploy
Laravel has a really powerful migrations system, which makes deployment super quick and easy. Since I started using Laravel (with Laravel Forge), I've been deploying via git (push to deploy). This means you can make changes to your app - including database changes, in the form of migrations - and 'git push' to deploy to your production server. I'm sure you could set up something similar with CodeIgniter (it does have some basic migrations functionality, too) but it doesn't feel quite so streamlined as Laravel. Because of this, I'm going to hand this one to Laravel - as it's really built for streamlining deployment.

Side note: in addition to Laravel Forge - which makes setting up PHP/Laravel servers super easy - you can also deploy via Envoyer, which can automatically test and roll back deployments so that you don't suffer any downtime. Forge and Envoyer are both created by the creator of Laravel, so they work really well together and make deployments so quick and easy (disclaimer: I have no affiliation with these services - I just think they're great).

## Hosting requirements
Due to Laravel having slightly more requirements in terms of hosting (mainly Composer) it may be slightly more tricky to set up on shared hosting. Therefore, I'm going to give this one to CodeIgniter, as it's a bit lighter on the hosting requirements. I've seen a few tutorials on setting up Laravel for shared hosting, so I'm assuming (and I haven't personally had to do it) that this is a bit more difficult to set up.

## Features
When I first started using Laravel I was amazed at how much time I saved by using Eloquent ORM. Your models basically inherit common functionality and can interact with each other without having to write much code at all. This is a big plus for Laravel. You also have a very comprehensive database migrations, system, queues (tasks which run in the background), authentication and authorisation, and a super slick command line interface for tinkering with your app. There's also the upcoming Laravel 'Spark', which is an out-of-the-box SaaS package, allowing you to add subscriptions, plans, payments, and team logic to your app. CodeIgniter has a brilliant active record package, form generation and validation, and a wide range of php helper functions. In comparison though, CodeIgniter's functionality seems pretty basic. For me, Laravel wins on features.

## Frequency of updates
From my experience of working with the two frameworks, Laravel has been moving a lot faster in terms of updates. This is either a good or bad thing, depending on what you want from your framework. Laravel is more cutting edge, has more features and tends to move faster and have more updates. As a developer, you need to keep up. CodeIgniter hasn't really changed a lot since I first started using it - around 7 (cough!) years ago. It's been pretty safe, stable, and easy to stay up to date with. There have been a number of security updates, but it doesn't feel like the functionality has moved on a lot.

## Security
Both frameworks have an excellent set of security features, such as preventing SQL injection (through active record) and cross site request forgery (CSRF) protection. The biggest issue with security is most likely going to be the developer, as it's how you choose to use the features available, and what you then choose to write yourself. Since Laravel has more features - such as out-of-the-box user authentication - you're a little more protected, as you're less likely to write this functionality yourself. That being said, there are a couple of very solid user authentication packages for CodeIgniter. As they don't come officially with the package, you'll have to download and manage them separately. I'd say both packages have very good set of security features, but Laravel has you covered a little more as it offers pre-built functionality for areas which may leave you open if you don't do it properly yourself (such as user authentication).

## Conclusion
Both are great frameworks with an excellent set of security features. CodeIgniter is quicker to learn, easier to set up, and more likely to run on shared hosting. Larvavel takes longer to learn, is a little more tricky to set up, but has more features. Once you're up and running, Laravel is probably quicker to build and deploy changes, due to the comprehensive Eloquent ORM and migrations functionality. CodeIgniter's updates have been much more conservative and easier to keep up with, where as Laravel seems to push new features more often, and has a much quicker release cycle.

I hope this helps. If you've got any other points to add, please mention them in the comments below :)