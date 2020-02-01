---
layout: post
identifier: "blog65"
title: "Protecting a Drupal site from hotlinking"
date: "2008-09-18 20:40:00 +0000"
tags: [ "Web Development", "Drupal" ]
permalink: "blog/protecting-drupal-site-hotlinking"
---
## What is hotlinking?

Hotlinking, sometimes called image leeching or hot linking, is where another website embeds an image which is stored on your web host. So, for example, if you want to add an image to your website, you can upload the file to your web host then embed the image into your HTML referencing the source for the image as the location of the file on your web host. When someone accesses the HTML page where the image is embedded the file will be downloaded from your web host. If you don't protect against hotlinking, someone could embed that same image on their web page, which means that every time someone accesses their page, the image will be downloaded from your web host and drain your bandwidth. Don't do this, it's not cool and some sites see it as stealing.

<!--more-->

## How do I know if someone is hotlinking to my site?

Sadly, unless you go looking for this you may never know. One indicator could be that you suffer a sudden surge in bandwidth. I say bandwidth, not traffic, because stats tools such as Google Analytics may not pick this up because they only register web pages, not images. For argument's sake, I'm considering bandwidth as pure data transfer and traffic as people who are visiting your site and reading your web pages. Drupal's access statistics may also not pick this up as they will only register page hits. It may be picked up if you are using the private download method. However, people may still get around this by linking directly to the file.

The best place to check for hotlinking would be your web host's web stats package. In my case, as I'm using an Apache server with Plesk, I'm using Plesk Stat. This logs access at a lower level so I can see everything that hits the server. Somewhere in the stats package you should find 'referrals'. This shows where other sites have linked to your site, which also includes embedded images. You could go visiting the referrals looking for an image, but unless any really stand out I wouldn't bother - the best thing you can do is just to protect against the hotlinking, which we'll look at next.

## How do I stop hotlinking?

Once again, it's htaccess to the rescue! With Drupal there is a default htaccess file in the root directory of your site. We're going to leave that be. I'm assuming that all of your images are stored in the `/files` folder, so this is the folder we will protect. There is already an `htaccess` file in there, so we just need to add a couple of lines to say not to serve images if they are referred from other sites. Here's a sample `htaccess` file showing how to do this:

```conf
SetHandler Drupal_Security_Do_Not_Remove_See_SA_2006_006
Options None
Options +FollowSymLinks
# Block hotlinks
RewriteEngine On
RewriteCond %{HTTP_REFERER} !^$
RewriteCond %{HTTP_REFERER} !^http(s)?://(.*\.)?yourdomain.com [NC]
RewriteRule \.(jpeg|jpg|gif|png)$ http://yourdomain.com/nohotlinking.gif [NC,R,L]
```

Just to recap, this is the `htaccess` file that goes in your `/files` directory, not your root directory. This works by saying allow any blank referrals (some browsers do this, so just to be safe), allow any referrals from yourdomain.com, block any image files (the ones I've specified) and return http://yourdomain.com/nohotlinking.gif instead (which will show on the site trying to hotlink). The reason we add this to the /files folder instead is because if you add this to the root folder htaccess file the nohotlinking.gif will also be protected and try to redirect to itself, causing an infinate loop - so it won't work. Now just create an image called `nohotlinking.gif` and place it in your root folder - this will be the image people see when someone trys to hotlink.

Images which are part of your theme will not be protected by this method. If you want to also protect your theme images, you will need to add the same `htaccess` file to your theme folder.

Thanks to [a tutorial on altlab.com](http://altlab.com/htaccess_tutorial.html) for the info on this - which also has a really helpful tool for testing if you have this set up correctly.

Please feel free to post any comments below.