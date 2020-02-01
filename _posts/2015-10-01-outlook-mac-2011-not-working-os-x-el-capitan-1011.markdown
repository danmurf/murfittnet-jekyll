---
layout: post
identifier: "blog122"
title: "Outlook for Mac 2011 not working on OS X El Capitan (10.11)"
date: "2015-10-01 20:35:00 +0000"
tags: [ "Microsoft", "Apple", "OS X", "El Capitan", "Outlook" ]
permalink: "blog/outlook-mac-2011-not-working-os-x-el-capitan-1011"
---
**tl;dr - If you use Outlook for Mac and you're thinking of upgrading to OS X El Capitain, don't...yet!**

**Edit (Fix): There is an update available now that fixes this problem. You can install it by opening Word, clicking 'Help' in the menu bar then clicking 'Check for updates'. You should see the critical update available. Download, install it, and enjoy Outlook 2011 on your El Capitan Mac :) For more information, visit: <https://support.microsoft.com/en-us/kb/3098229>**

It's been an eventful day, for all the wrong reasons. Usually my Apple updates go well, but today I discovered that if you try and sync Outlook (running on El Capitan) with an Exchange server, you get a (nice,  redesigned) beachball. This is a known bug (<https://support.microsoft.com/en-us/kb/3098396>), and the official workaround at the moment is to stick to using Yosemite.

<!--more-->

The crash seems to kick in when Outlook tries to sync with Exchange, so if you just want to load Outlook and not receive any new email, you can probably do it by opening it and quickly setting it to offline mode. I've seen a few people mention this on the forums, but I've not personally tried it, as it's pretty useless to me in offline mode (obviously - it's email!).

There are a couple of workarounds if you have already upgraded:

**1) Use Outlook web access.** We use Office 365 and this comes with a very nice Outlook web client, which is actually pretty powerful. You might miss that native app feeling, but you'll be able to carry on working, at least until there's an official fix.

**2) Use the Mac Mail app.** You can configure the Mac Mail app to connect to Exchange, and it works as well as Mail on iOS. It's a lot more stripped down than Outlook, and if you use contacts and calendar you'll have to set those up separately on your Mac too, but again, you can carry on working in the meantime.

**3) Revert to Yosemite.** I've put this last as it's probably a last resort, but if you absolutely, positively have to use Outlook for Mac, and you've already upgraded, you can consider reverting to a previous Time Machine backup. Apple have some steps to do this (<https://support.apple.com/kb/PH18846?locale=en_US>) - just make sure you have backed up any data you have created since the last good Yosemite backup.

If anyone has a fix for this in the meantime, please post it in the comments below. I'll update this post as soon as I hear of an official fix or more permanent workaround.