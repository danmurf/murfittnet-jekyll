---
layout: post
identifier: "blog89"
title: "Trying out Mollom for Drupal"
date: "2010-04-03 08:39:00 +0000"
tags: [ "Drupal", "Security", "Blogging" ]
permalink: "blog/trying-out-mollom-drupal"
---
I've decided to give the web service, [Mollom](http://mollom.com/), a try since my CAPTCHA, which I kept tweaking to the point where I nearly couldn't read it, was letting me down. The problem with CAPTCHA is it logs how many form submissions it blocks, which is great, but this doesn't necessarily mean SPAM submissions; it could be frustrated people not being able to post a comment on your blog. Mollom works by analysing the form submission for SPAM patterns, then determining whether it is suitable or not. It's quite strange to see my forms without a CAPTCHA underneath, but I should know soon enough how well the service works as I have many form submissions blocked by CAPTCHA each day.

Mollom is available for Drupal, Wordpress, Joomla! and many more CMSs. It also has developer libraries for PHP, Java, Ruby, Python and many more.