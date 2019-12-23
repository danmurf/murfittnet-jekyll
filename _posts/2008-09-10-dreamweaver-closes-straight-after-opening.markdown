---
layout: post
title:  " Dreamweaver closes straight after opening"
date:   2008-09-10 19:29:00 +0000
tags: [ Web Development, Web Design ]
permalink: blog/dreamweaver-closes-straight-after-opening
---
This really is one of the strangest software bugs I've come across!

## The Problem

Dreamweaver crashes and won't open again. When you try and open Dreamweaver it just closes straight away, with nothing more than a glimpse of the splash screen.

## The Solution

One of the CSS files in the site you were working on has a file size which is a multiple of 8kb (mine was 24kb). You can try anything; rebooting, reinstalling, but Dreamweaver won't play ball if the file is still there. You need open the CSS file in another text editor and add a few dummy lines of comment text to increase the file size slightly; you should then find Dreamweaver will open again normally.

[Thanks to David Powers](http://groups.google.com/group/macromedia.dreamweaver/msg/4f6b8d6385dc3466) for this. Please feel free to leave any comments below.