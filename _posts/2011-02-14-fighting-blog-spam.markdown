---
layout: post
identifier: "blog98"
title: "Fighting blog comment spam"
date: "2011-02-14 20:21:00 +0000"
tags: [ "Security", "Blogging" ]
permalink: "blog/fighting-blog-spam"
---
I've noticed a recent influx of blog spam which seem, to some degree, relevant to the content it's posted on. I think spammers are composing comments targeted to specific subject areas and then searching the web for content on that subject so that when they post the comment it appears at first glance to be genuine. Of course the most telling part is the totally unrelated link to men's watches or postal degrees which seem somewhat out of place in a comment on a php web development framework. Nevertheless, if you're not careful the comments can slip through the net and appear on your blog. The other issue which has become more of a problem lately is the spammer's ability to evade CAPTCHA challenges. I've increased the level of noise and distortion for the CAPTCHA challenge on this blog but some still get through. It's as if there is a person actually typing in a response to the challenge, in which it won't be of much help. There are a few ways in which you can help fight, reduce and manage blog spam, because let's face it - it's not going to stop entirely. So let's have a look at some quick first pointers.

## Filter out HTML 'a' tags

HTML 'a' tags can be used to mask the location of links and there's really no need for people in comments to use them. Instead, use an automatic filter which converts http:// strings into clickable links. This way people can see exactly where they are going to go if they click a link, and spammers can't hide links behind text relevant to the subject of the comment. Also publish the fact you are doing this as it may act as a small deterrent.

## Moderate comments

If you really want to feel in control of what content is allowed to be posted to your blog, moderate the comments. Many content management systems will allow this function and as long as you don't get too many comments it shouldn't be too difficult to keep up with.

Use a comment spam protection service
There are services available which will screen your comments for you in a similar way to email spam filters and determine, based on a spam scoring system, whether the comment is spam or not. One which I've found is quite effective is Mollom ([http://mollom.com](http://mollom.com)). This has both free and enterprise services for use on blogs and more.

## Add a CAPTCHA challenge

You can't always rely on CAPTCHA, but it will most definitely reduce the amount of spam which gets through so it's always a good idea to protect your comment forms with CAPTCHA as a first line of defence.

Spam is never going to go away - in fact, it's probably going to get more sophisticated, so it's a good idea to keep an eye on the spam which doesn't get through on your blog by accessing your logs, look for trends (especially in the search engine referrals) and try to stay ahead of the game by figuring out why the spammers ended up on your site and what they tried to do to evade your anti-spam mechanisms. Please feel free to leave a comment if you have any tips or techniques which you use to help reduce or manage spam.