---
layout: post
identifier: "blog58"
title: "Drupal 5.6 and register_globals"
date: "2008-01-25 19:37:00 +0000"
tags: [ "Drupal", "PHP" ]
permalink: "blog/drupal-56-and-registerglobals"
---
As of Drupal 5.6 you will no longer be able to install the CMS onto a server with `register_globals` enabled. The notice on the Drupal website says:

>  We no longer support servers with the PHP directive register_globals set to on. Attempts to install Drupal 5.6 when register_globals is enabled will fail. Current installations will continue to function, but will display an error on administration pages and the status report.
 
This check was introduced as a fix for the Cross site scripting vulnerability ([DRUPAL-SA-2008-007](http://drupal.org/node/208565)) which occurs when `register_globals` is enabled. I was upgrading my Drupal installation from 5.5 when I found out so I only suffered the error on the status report, but people running a fresh install will find they can’t go any further until they disable `register_globals`.

## What is register_globals?

In php, variables don't need to be initialised; you can simply use any valid variable name and assign a value in one statement. When `register_globals` is enabled form variables are automatically injected into your php script. So, for example:

```php
$_GET['loggedIn']
```

would become

```php
$loggedIn
```

If this variable wasn't declared as `FALSE` previously in the script it could be set to `TRUE` by using

```
yoursite.com/?loggedIn=1
```

I don't have to explain the rest as I think it's pretty clear how this can be used to exploit scripts. This said, `register_globals` isn't a security vulnerability at all, but it starts becoming a problem when using un-initialised variables like above (there's a good explanation of this on php-security.org's blog).

## Why does register_globals suddenly need to be disabled?

The cross site scripting vulnerability mentioned in the latest update means that exposed theme `.tpl.php` files can be exploited by using carefully crafted links (like above), and this is only an issue when register_globals is on.

## How can I disable register_globals?

If you're managing your own server you can disable register_globals in your php.ini file. Servers running php 4.2.0 or higher will have `register_globals` disabled by default, so if it's on there is probably a reason in that some older scripts may require it to work. To disable `register_globals` in your `php.ini` file simply add:

```ini
register_globals = off
```

If you're hosting on a shared platform you probably won't have access to the server's `php.ini` so you might be able to disable it via an `.htaccess` file. Using `php_flag` in `.htaccess` will allow you to override settings in the `php.ini` file, but not all hosts will allow this as they usually like to retain control of server settings. It's worth a try anyway, so just create (or edit the existing) a file called `.htaccess` (you may need to create this as `htaccess.txt` on a Windows machine as it won't like the file name; then upload and rename appropriately) and add the following line:

```ini
php_flag register_globals off 
```

If this results in an error (most likely error 500) then you will have to ask your host to disable `register_globals`. However, they may choose not to do this as if they change `register_globals` for their whole shared server, other customers' websites may stop functioning properly creating more hassle for themselves. If this is the case you'll probably have to move hosts, which is the situation I found myself in a while ago!