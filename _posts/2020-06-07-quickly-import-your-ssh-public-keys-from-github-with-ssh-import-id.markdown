---
layout: post
title: "Quickly import your ssh public keys from Github with ssh-import-id"
date: "2020-06-07 12:00:00 +0100"
tags: [ "Ubuntu", "Security", "ssh" ]
permalink: "blog/quickly-import-your-ssh-public-keys-from-github-with-ssh-import-id"
---
There's a neat Ubuntu command which allows you to easily import your ssh public keys from Github to your server user account.

```
ssh-import-id-gh <github username>
```

By default, it will append the fetched public key (or keys if you specify multiple accounts) to the current user's `~/.ssh/authorized_keys` file. Once you've run the above, you will be able to ssh to your server account using the same key you would use to push code to Github.

<!--more-->

The underlying command also supports launchpad.net as a public key server and allows you to specify multiple accounts at once.

```
ssh-import-id [options] USER_ID_1 [gh:USER_ID_2] ... [lp:USER_ID_n]
```

This command is also used as part of the Ubuntu setup process. When creating a new user, you will be prompted with a choice to download your keys from Github. This is a nice touch, and certainly more convenient than copy and pasting your keys around.

As always, when using a command like this, take care and be sure the account you specify is one you control and only has the keys you expect to be granted access. You'll be allowing anyone with the associated private key full access to your server account without the need for the account password.

For more information about this command, visit <http://manpages.ubuntu.com/manpages/bionic/man1/ssh-import-id.1.html>
