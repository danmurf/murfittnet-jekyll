---
layout: post
title:  "Email access becomes slow when lots of messages are left on the server"
date:   2008-01-27 15:14:00 +0000
tags: [ Email ]
permalink: blog/email-access-becomes-slow-when-lots-messages-are-left-server
---
I noticed recently that if you're using POP with leave mail on server (LMOS) enabled, authenticating and downloading new messages can become progressively slower. So much so that the email client can even time out, leaving the mailbox locked so you can't even log in again for a while.

## What is POP?

POP stands for Post Office Protocol and it's how email clients like Outlook Express and Thunderbird are commonly configured to collect messages from a mailbox. One of the advantages of POP is that a connection to the server is only required when messages are being checked/downloaded to the email client. Once this is complete, the client can disconnect and continue to read/reply/delete messages 'offline'. Once a message has been downloaded and stored on the client a message is sent back to the server telling it to delete the message. This means the only place the message now exists is on the client, not the server. If you want to also be able to download the same message on another machine, you will need to leave the message on the server.

## What is 'Leave Mail on Server' (LMOS)?

This is the feature which stops the client deleting the message from the server so that the next client to log on will still be able to download the same message. Instead of deleting the mail from the server some mail clients will mark the message as 'read', which can be a handy feature, but this is non-standard and doesn't really help with this slow down problem.

## Why does checking for email become progressively slower with LMOS enabled?

In the POP sequence the mail client will request a Unique ID List (UIDL) which lets the client know what messages are in the mailbox. As messages have been previously left on the server, the mail will accumulate over time and the UIDL will get bigger and bigger and will take longer to check which message IDs the client hasn't already downloaded.

I noticed that the primary email client (the one which was set to delete the messages after download) seemed to access the mail quite rapidly - it only seemed to impact the clients which had LMOS enabled. I guess this could be because the primary client just downloads the accumulated messages (which in itself takes a long while) where as the LMOS enabled client will check all the messages and wait for the ones which it hasn't already got.

To fix this problem the mailbox simply needs to be kept more tidy, either by leaving the messages for only, say, 7 days (to give the other clients a chance to download the messages too), or just regularly purging old messages from the mailbox.

## References

* [The Leave Mail On Server (LMOS) FAQ](http://www.labridge.com/site/pages/configure/my/lmos.html)
* [POP3 Tutorial Sequence Diagram (PDF)](http://www.eventhelix.com/RealtimeMantra/Networking/POP3.pdf)
* [Post Office Protocol - Wikipedia](http://en.wikipedia.org/wiki/Post_Office_Protocol)