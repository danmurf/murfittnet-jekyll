---
layout: post
title:  "XAMPP and mod_rewrite (getting clean URLs to work)"
date:   2007-10-04 18:50:00 +0000
tags: [ Web Development, Apache ]
permalink: blog/xampp-and-modrewrite-getting-clean-urls-work
---
If you're using a CMS or blog app, like Drupal or Wordpress (even if you're not) chances are you'll probably want to enable clean URLs (sometimes called search engine friendly URLs). This cool little feature uses an Apache module called mod_rewrite, and if you're developing your site using XAMPP this is disabled by default (possibly for security reasons).

To enable this module it just takes a little tweak of your `httpd.conf` file which will be found in `xampp\apache\conf`. The conf file already contains the line needed to enable the module, but there is a comment mark (#) just before the code which means Apache will ignore the code. The line you are looking for is:

```
#LoadModule rewrite_module modules/mod_rewrite.so
```

In my `httpd.conf` file this is **line 118**, but it may vary so just search for "mod_rewrite" in the file. Now, simply remove the comment (#) from before the line, and save the file. You'll need to restart Apache for the changes to take affect, and you should now find you can use clean URLs with XAMPP.

Please feel free to leave any comments below.