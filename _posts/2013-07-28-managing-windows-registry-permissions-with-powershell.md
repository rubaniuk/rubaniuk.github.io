---
# id: 192
title: Managing Windows registry permissions with PowerShell
date: 2013-07-28T14:53:29-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=192
# permalink: /?p=192
categories:
  - PowerShell
  - Software Development
---
&#8230; is simple. But before jumping into code sample make sure to familiarize yourself with <a title="http://msdn.microsoft.com/en-us/library/system.security.accesscontrol.objectsecurity.setaccessruleprotection.aspx" href="http://msdn.microsoft.com/en-us/library/system.security.accesscontrol.objectsecurity.setaccessruleprotection.aspx" target="_blank">ObjectSecurity.SetAccessRuleProtection</a>.

And here&#8217;s the PowerShell script code:

{% highlight powershell %}$acl = Get-Acl HKLM:\Software\Foobar\Product

# Disable inheritance for this key (true), remove inherited access rules (false):
$acl.SetAccessRuleProtection($true, $false)

# Remove all permissions for "NT AUTHORITY\SYSTEM":
$acl.Access | where {$_.IdentityReference.Value -eq "NT AUTHORITY\SYSTEM"} | %{$acl.RemoveAccessRule($_)}
Set-Acl HKLM:\Software\Foobar\Product $acl

# Set Read-only permissions for "NT AUTHORITY\SYSTEM":
$acl = Get-Acl HKLM:\Software\Foobar\Product
$rule = New-Object System.Security.AccessControl.RegistryAccessRule ("NT AUTHORITY\SYSTEM","ReadPermissions","Allow")
$acl.AddAccessRule($rule)
Set-Acl HKLM:\Software\Foobar\Product $acl

# Now if you create subkey it will not inherit permissions from parent key:
$rootRegPath = Join-Path -path $rootRegPath -childPath SomeProduct
new-item -path $rootRegPath{% endhighlight %}