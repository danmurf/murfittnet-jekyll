---
layout: post
identifier: "blog56"
title: "How to get WPA2 working on Windows XP"
date: "2007-10-27 10:18:00 +0000"
tags: [ "Wi-fi", "Security" ]
permalink: "blog/how-get-wpa2-working-windows-xp"
---
WPA2 is the latest standard in Wi-Fi security, and it's considered fully secure (for today at least). It's a good idea to run the highest level of security you can, even on a home network. I won't go into the benefits, but as far as I can see there are no reasons not to move to WPA2 - you won't even notice any difference, but your connection will be more secure.

WPA2 isn't a standard option in Windows XP (SP2), so you'll have to download the hotfix from Microsoft:

[The Wi-Fi Protected Access 2 (WPA2)/Wireless Provisioning Services Information Element (WPS IE) update for Windows XP with Service Pack 2 is available](http://support.microsoft.com/kb/893357)

This will run a small hotfix:

![Hotfix](/uploads/wpa2hotfix.png)

As usual, make sure all your data is backed up - you don't want to suffer the irony of data loss due to trying to make something more secure.

Once the hotfix has been installed, you will need to restart, and you should now find that your connection's security is now WPA2.

![WPA2](/uploads/wpa2.png)

When I ran this I was moving from WPA to WPA2, so the connection along with the password was carried across. However, if you're running WEP you will need to enter the security key when setting up the connection.

Please feel free to leave any comments below.