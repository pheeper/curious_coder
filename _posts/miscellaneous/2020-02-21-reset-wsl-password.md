---
layout: post
title: Reset Ubuntu Password in WSL on Windows 10
categories: ['miscellaneous']
tags: ['wsl']
---

If you've forgotten your password for WSL don't worry, it can be easily reset by following the seven steps below.

1. Open Bash on Ubuntu to take note of your Linux username (note that this may or may not match your Windows username)
2. Close Bash on Ubuntu (if you leave it running the next command will fail)
3. Open a Windows command prompt as Admin (Windows Key + X, A) 
4. Enter `ubuntu config --default-user root` to set the default user as root.
    + _note: this has changed for Ubuntu 18.04 in WSL so you'll need to run_ `ubuntu1804 config --default-user root`
5. Open Bash on Ubuntu.  You should notice that you are login in as `root` without having to enter a password.
6. To change your password run `passwd [username]` and follow the prompts to set a new password
7. The last thing you need to do is change the default user back to your normal user in Windows command prompt by running `ubuntu config --default-user  [username]`

You can test if this worked by opening a new bash prompt and running `sudo apt-get update`.  When prompted enter your new password and you should be set.

__WSL Tip__: did you know you could start a new bash shell from inside of PowerShell, simply by running `bash`?
