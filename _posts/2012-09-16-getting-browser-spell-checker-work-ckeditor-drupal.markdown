---
layout: post
identifier: "blog109"
title: "Getting the browser spell-checker to work with CKEditor in Drupal"
date: "2012-09-16 13:36:00 +0000"
tags: [ "Drupal" ]
permalink: "blog/getting-browser-spell-checker-work-ckeditor-drupal"
---
Most modern browsers, such as Firefox 15, Chrome 21 and Internet Explorer 9, have a nifty spell-checker built in to help us 'auto-correct' generation write, but when you install the CKEditor some of this functionality is hijacked by the default javascript used by the text editor. Fortunately, if you're using CKEditor for Drupal, it's a quick fix to get the browser default spell-checker working again. If you're not using Drupal you may still be able to apply the fix by noting the configuration settings and using them in your setup.

<!--more-->

First, go to: **Administer > site configuration > CKEditor > [the profile you are using] > Advanged options tab > Custom JavaScript configuration text area**

Add the following configuration options:

```javascript
config.disableNativeSpellChecker = false;
config.removePlugins = 'scayt,menubutton,contextmenu';
config.browserContextMenuOnCtrl = true;
```

Save the profile and you're done. Naturally, you may need to refresh your browser and clear any caches for the changes to take effect.