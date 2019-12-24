---
layout: post
identifier: "blog99"
title: "Optimising Drupal performance"
date: "2011-03-13 10:02:00 +0000"
tags: [ "Web Development", "Drupal", "Hosting" ]
permalink: "blog/optimising-drupal-performance"
---
There are a few great out of the box performance tweaks which Drupal offers to speed up page loading times and minimise server load. First of all, these tweaks wouldn't suit every site. You need to first think about how much traffic you currently get and how often our content changes. You don't necessarily have to add or amend a page for content to change; people can post comments and interact with your site in ways which change the content displayed. This will make a difference to how you chose to optimise your Drupal site performance.

When caching is enabled in Drupal (Administer > Site Configuration > Performance) your pages will be dynamically generated the first time they are hit and then subsequent visits to that page will be loaded from the stored cache. This will speed up page loading times because Drupal doesn't have to pull all of the content together from the database each time. However, new content won't be shown until the cache has expired and is regenerated. It's worth noting that cached pages are only displayed to anonymous users, so if you are testing this out and logged in to your site, you probably won't see any performance differences. In this case you will need to logout, then you will see you site's cached content.

## What is 'minimum cache lifetime'?

This determines how much time should pass before cached content is regenerated from the database. If you set this to 1 day, and you change one of your pages, the cached version of your page will remain the same and the changes won't be visible to anonymous visitors for at least 1 day. If you don't change your content that often or you don't get many comments this may be a good idea, as it makes, in many cases, a noticeable difference to page loading times. If you get lots of comments or you are updating on a daily basis or more, you may wish to decrease this limit to something more reasonable. The trick is to get the time as close as possible to how often your content changes.

## Page caching and the CAPTCHA module

If you are using the CAPTCHA module it's also worth noting that this will disable caching for any pages where a CAPTCHA challenge is present. In this case it would be a good idea to put your comment forms on a separate page from your content (Administer > Content Management > Content Types [Content type] > Comment Settings > Location of comment submission form > Set to display on separate page).

## Bandwidth Optimization

These settings will aggregate CSS and JS files to reduce the number of hits required to load a page. This can make significant difference on high traffic sites because it reduces the number of HTTP requests. Many themes and modules include CSS files and if you look at your page source (with these options disabled) will see the number of linked CSS and JS files required for each page load. With both of these optimization options enabled you will see just one CSS and one JS file linked to in your page source. These linked files, with optimization enabled, will include all CSS and JS code previously loaded but in one file rather than (say) 10.

If anyone knows of any good Drupal performance modules or any other tweaks please feel free to post them in the comments below.