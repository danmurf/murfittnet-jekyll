---
layout: post
title:  "jQuery UI touch support for iPad and other tablets and smartphones"
date:   2012-07-08 14:22:00 +0000
tags: [ Web Design, User Interfaces, jQuery, jQuery UI ]
permalink: blog/jquery-ui-touch-support-ipad-and-other-tablets-and-smartphones
---
![jQuery UI Logo](/uploads/JQuery_UI_logo_color_onwhite-300x72.png)

The jQuery UI library doesn’t support touch features by default, so trying to use the slider or drag and drop on the iPad won’t work. Fortunately, all that’s required to get this working is a small hack - enter [jQuery UI Touch Punch](http://touchpunch.furf.com).

Just include jQuery and the jQuery UI scripts on your page as per normal:

```html
<script src="http://code.jquery.com/jquery.min.js"></script>
<script src="http://code.jquery.com/ui/1.8.17/jquery-ui.min.js"></script>
```

Then include the jQuery UI Touch Punch library:

```html
<script src="jquery.ui.touch-punch.min.js"></script>
```

That’s it. The existing jQuery UI elements on your page should now work on the iPad, iPhone or any touch screen tablet or smartphone.

There are examples on the jQuery UI Touch Punch website so you can test some of the jQuery UI elements out on your device first.

For more information, or to download the plugin, visit: <http://touchpunch.furf.com>