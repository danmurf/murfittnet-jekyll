---
layout: post
title:  "MAMP: \"#2006 - MySQL server has gone away\" while importing database"
date:   2013-06-21 21:32:00 +0000
tags: [ Drupal, MySQL, MAMP ]
permalink: blog/mamp-2006-mysql-server-has-gone-away-while-importing-database
---
I was importing a relatively large Drupal database today into MAMP (via phpmyadmin) and MySQL rudely walked off, with the following error:

    #2006 - MySQL server has gone away

Ah, a nice vague error message! It seems that the import statement (from the `cache_menu` table) in the database dump contains packets which are too large to import using the default MAMP settings. To fix this, I created a `my.cnf` file in my `/Applications/MAMP/conf/` folder with the following contents:

    [mysqld]
    max_allowed_packet = 100M

Then I restarted MAMP and imported my database without any trouble. I hope this helps if you've stumbled across the same issue.