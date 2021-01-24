---
# id: 113
title: 'PowerShell: capturing output to log file and console'
date: 2013-04-09T22:39:33-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=113
# permalink: /?p=113
categories:
  - PowerShell
  - Software Development
---
Recently I had to redirect full PowerShell session to both console and log file. Full means both stdout and stderr needs to be redirected. Working code is worth thousand words:

&nbsp;

<pre class="brush: powershell; gutter: true">$ErrorActionPreference="SilentlyContinue"
Stop-Transcript | out-null
$ErrorActionPreference = "Continue"

$OutputFileLocation = "C:\output.log"
Start-Transcript -path $OutputFileLocation -append

Write-Host "This will go into output.log"

# redirecting both STDOUT and STDERR (2&gt;&1) to transcript:
robocopy.exe C:\ D:\ readme.txt 2&gt;&1 | out-host

Stop-Transcript</pre>

&nbsp;

Line 11 deserves additional explanation. Due to a <a href="http://connect.microsoft.com/PowerShell/feedback/details/315875/unable-to-capture-all-session-output-into-a-transcript" target="_blank">PowerShell bug 315875</a> output from native applications will not be captured. That being said, the workaround is to combine stdout and stderr and redirect it to a out-host.

The only remaining limitation is that stderr will be interpreted by PowerShell as error (and rightly so!) and thus printed out in red. While it is a little annoying, your output log doesn&#8217;t have colors 🙂

&nbsp;