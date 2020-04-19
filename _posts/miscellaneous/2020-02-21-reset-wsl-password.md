---
layout: post
title: Reset Ubuntu Password in WSL on Windows 10
categories: ['miscellaneous']
tags: ['wsl']
---

Who hasn't forgotten a password?  It seems like everywhere we go on the computer we need a password, so it's understandable.  This is one of hte reasons I use a password manager and it works great, except for the fact that I don't like to keep my computer credentials in it. So, as you can guess, a few weeks ago I opened my WSL terminal in Windows 10 and realized I had forgotten my password.  Here's how I went about resetting it.

1. Open Bash on Ubuntu to get your Linux username (this may not match your Windows username)
2. Close Bash on Ubuntu (if it is running the next command will fail)
3. In Windows admin command prompt (Windows Key + X, A) change the default user to root by running `ubuntu config --default-user root`. You should now be logged in as root, without having to provide a password.
    + _note: this has changed for Ubuntu 18.04 in WSL so you'll need to run_ `ubuntu1804 config --default-user root`
4. To change the password for your user account run `passwd your_username` and follow the prompts to set a new password
5. The last thing you need to do is change the default user back to your normal user in Windows command prompt by running `ubuntu config --default-user  your_username`

If you open a new bash prompt and run something requiring elevated privileges, such as `sudo apt-get update` your password should work.  

__WSL Tip__: did you know you could start a new bash shell from inside of PowerShell, simply by running `bash`?
