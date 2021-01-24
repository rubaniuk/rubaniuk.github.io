---
# id: 208
title: 'RegEx: string doesnt start with'
date: 2013-10-22T07:35:04-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=208
# permalink: /?p=208
categories:
  - Software Development
---
Recently I had to go through lots of files and find a string that does not start with semicolon ';' and ends with one of the words **status**, **error** or **warning**. Of course, regular expressions will help us here. Without further due, I would like to introduce RegEx:

<p style="text-align: center;">
    <strong>^(.?$|[^;].+)(status|error|warning)</strong>
</p>

<p style="text-align: left;">
  Lots of time saved!
</p>