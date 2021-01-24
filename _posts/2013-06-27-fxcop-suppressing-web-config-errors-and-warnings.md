---
# id: 156
title: 'FxCop: suppressing Web.config errors and warnings'
date: 2013-06-27T09:01:11-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=156
# permalink: /?p=156
categories:
  - Software Development
---
Recently I had an issue where I had to suppress certain errors coming out of ASP.NET configuration files. Since Web.config isn&#8217;t a code per se we need to use global suppression file to suppress errors coming out of config file.

<span style="line-height: 1.714285714; font-size: 1rem;">The real problem was that the issues where reported not in the project where the file Web.config is located but from a<strong> different project</strong> in solution:</span>

_d:\BuildTest\Any CPU\Release\DeploymentDrop\Web.config(27): warning : CA3114 : Microsoft.Security.Web.Configuration : Always_  
 _enable custom errors to return generic error information. Set mode attribute to &#8220;On&#8221; in unit MyProject file d:\BuildTest\Any CPU\Release\DeploymentDrop\Web.config line 14 column 4 [**D:\PathInTFS\MyProject\MyProject.csproj**]_

The issue was solved by adding **GlobalSuppressions.cs** to MyProject where there issue was showing up (not where Web.config lives!):

<pre class="brush: csharp; gutter: true">// This file is used by Code Analysis to maintain SuppressMessage 
// attributes that are applied to this project.
// Project-level suppressions either have no target or are given 
// a specific target and scoped to a namespace, type, member, etc.
//
// To add a suppression to this file, right-click the message in the 
// Code Analysis results, point to "Suppress Message", and click 
// "In Suppression File".
// You do not need to add suppressions to this file manually.

[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Security.Web.Configuration", "CA3114:SetCustomErrorsModeToOn")]</pre>

Note that SuppressMessage above will suppress all CA3114 messages in the project.