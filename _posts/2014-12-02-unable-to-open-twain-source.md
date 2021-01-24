---
# id: 350
title: Unable to open TWAIN source
date: 2014-12-02T20:15:09-08:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=350
# permalink: /?p=350
categories:
  - Uncategorized
---
_This post is a deviation from my general blog theme, but I simply had to post it._

**Issue:** my Canon LiDE 25 scanner was working for several years on Windows 7 x64 English Pro but suddenly started to show error &#8220;Unable to open TWAIN source Please check connection Then re-start Toolbox&#8221;

[<img loading="lazy" class="aligncenter size-full wp-image-351" src="http://www.rubaniuk.com/wp-content/uploads/2014/12/UnableToOpenTWAINsource.jpg" alt="UnableToOpenTWAINsource" width="279" height="184" />](http://www.rubaniuk.com/wp-content/uploads/2014/12/UnableToOpenTWAINsource.jpg)

**Solution:** add _**C:\Windows\twain_32\CNQL25**_ to _**PATH**_ environment variable.  Problem solved!