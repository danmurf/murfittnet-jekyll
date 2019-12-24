---
layout: post
identifier: "blog121"
title: "Getting Laravel Homestead to work with larger file uploads"
date: "2015-01-12 22:11:00 +0000"
tags: [ "PHP", "Laravel", "Homestead", "Vagrant", "Nginx" ]
permalink: "blog/getting-laravel-homestead-work-larger-file-uploads"
---
<img src="/uploads/laravel-four-icon_0.png" style="width:200px; float:right;margin-left:20px; margin-bottom:20px;" alt="Laravel"/> I've been working on a Laravel project which uses relatively large file uploads (about 30MB - 120MB). My development environment is [Laravel Homestead](http://laravel.com/docs/4.2/homestead) - a great, pre-packaged Vagrant box for Laravel development. If you haven't heard of this I highly recommend you check it out - it's a great way to get up and running with Laravel, but it doesn't seem to play well for larger file uploads through forms (over about 5MB). My forms were either hanging or returning an nginx 'too large' error. Here are some of the settings which I've had to tweak to get Homestead working nicely with larger uploads.

Make a backup of your Homestead settings and files before making any tweaks so that if anything goes wrong you can revert to a working copy. First, increase the limits in your **php.ini**. This can be found in `/etc/php5/fpm/php.ini`. Here are the settings I've overridden (note: these are spread throughout the php.ini file - I've just put them all together for convenience):

```conf
max_execution_time = 500
upload_max_filesize = 128M
post_max_size = 128M
```

The main two settings here are the `upload_max_filesize` and `post_max_size`, but I've also increased the `max_execution_time` to allow for the longer time to process the file and upload. You can set all these accordingly.

Once you've updated your **php.ini** you'll need to reload it by running the following command in your terminal:

```bash
service php5-fpm restart
```

The next set of changes are in the **nginx.conf** file, which you can find at `/etc/nginx/nginx.conf`.

Within the **http section**, set **sendfile** to **off**:

```conf
sendfile off;
```

Just below this line, add another line to specify the `client_max_body_size`:

```conf
client_max_body_size 128M;
```

Once you've done this, save the file and run the following command in terminal to reload the config:

```bash
nginx -s reload
```

That should be it - you can now use your Laravel Homestead environment to upload much larger files. I hope this helps. If anyone has any tips related to this issue, please feel free to share them in the comments below :)

Sources:

<http://blog.elenakolevska.com/debugging-laravel-on-homestead/>
<https://laracasts.com/discuss/channels/general-discussion/homestead-uploading-large-files-l42>