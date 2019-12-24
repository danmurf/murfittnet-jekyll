---
layout: post
identifier: "blog68"
title: "CodeIgniter 1.7.0 Released"
date: "2008-10-24 10:30:00 +0000"
tags: [ "Web Development", "PHP", "CodeIgniter" ]
permalink: "blog/codeigniter-170-released"
---
It's that wonderful time again! CodeIgniter 1.7.0 has been released, so it's time to upgrade.

[http://codeigniter.com/user_guide/installation/upgrade_170.html](http://codeigniter.com/user_guide/installation/upgrade_170.html)

Upgrading looks fairly straight forward - here are some notable changes ([http://codeigniter.com/user_guide/changelog.html](http://codeigniter.com/user_guide/changelog.html)):

## Sessions

The Sessions class has been updated so that any custom data being saved gets stored to the database rather than the session cookie (assuming you are using a database to store session data), permitting much more data to be saved.

## New form validation class

Some changes/additions to the new form validation class:

* Simplifies setting rules and field names
* Supports arrays as field names
* Allows groups of validation rules to be saved in a config file
* Adds some helper functions for use in view files

The old Validation class is now deprecated. It will be left in the library folder for some time so that existing applications that use it will not break, but you are encouraged to migrate to the new version.

## PHP Style Guide

There's now a PHP Style Guide ([http://codeigniter.com/user_guide/general/styleguide.html](http://codeigniter.com/user_guide/general/styleguide.html)) in the User Guide. Although this doesn't affect working code it's just good practice to make sure you have a regular style to your code, especially when writing libraries that others will use.

Well done to everyone who has been working hard on this :)