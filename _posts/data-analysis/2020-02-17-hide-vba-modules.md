---
layout: post
title: Hide VBA Modules
categories: ['data analysis']
tags: ['vba']
---

I’ve been using VBA for a while now and I usually lock the VBA project or use Unviewable+ when I need to deter others from viewing or messing with the code.  However, I found that pressing `ALT+F8` brings up a list of all available procedures.  Which makes me wonder, what if someone else who knows about this trys to run a procedure they're not supposed to?  I could easily see how that might cause some unitened harm to the workbook, or whatever else it is connected to.

### Solution 
To solve this I thought, no problem I’ll just capture the ALT + F8 key stroke and cancel it, similar to what I’ve done with other key combinations.  But then I stumbled upon something so simple I couldn’t believe that I had not seen it before.  

```vb
	Option Private Module
```

By adding this to the very top of any module, it will block all procedures from being exposed to users (and potential problems that may come with that).  Behind the scenses all your procedures are still exposed to other modules so you don’t need to change anything else in your project.  Just go through each of the modules, paste the line at the top, and you're set.
