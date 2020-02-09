---
layout: post
identifier: "blog127"
title: "Cache Busting with Jekyll"
date: "2020-02-09 11:00:00 +0000"
tags: [ "Jekyll" ]
permalink: "blog/cache-busting-with-jekyll"
---
If you're running Jekyll and updating styles fairly regularly, you may want to add a cache busting line to your styles and scripts to ensure you (and your visitors) are always accessing the latest version of your assets.

<!--more-->

Firstly, [head over to the Minima theme GitHub repo](https://github.com/jekyll/minima/blob/2.5-stable/_includes/head.html) and copy the `head.html` contents. Create a new `head.html` file in your `_includes` folder (or create the folder if you haven't already done so). This will allow you to modify the included headers for the minima theme. If you're using another theme, just do a search for that theme's repository and look for the file which includes the styles and scripts, then follow the same process.

Next, we want to add a unique timestamp to the CSS url so that when a new build occurs, the link will be updated and any browser with the previous version will be forced to download the new version.

```liquid{% raw  %}
{% assign cacheBust = site.time | date:'?v=%s' %}
<link rel="stylesheet" href="{{ "/assets/main.css" | relative_url | append: cacheBust }}">{% endraw %}
```

This will result in something like the following

```html
<link rel="stylesheet" href="/assets/main.css?v=1581246285">
```

You should be able to use a similar technique for your JavaScript assets and anything else you need to cache bust.

![Busted!](https://media.giphy.com/media/l0ExeAkpaMaEAuX5e/giphy-downsized-large.gif)