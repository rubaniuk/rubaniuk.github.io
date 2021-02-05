---
# id: 298
title: Netstat and System.Net.HttpListenerException (0x80004005)
date: 2014-07-30T11:07:30-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=298
# permalink: /?p=298
categories:
  - Debugging
  - Software Development
---
Recently I was developing web service with several Web APIs. After few check-ins I decided to step through the code.

The service wouldn&#8217;t start. What? &#8220;It worked on my machine&#8221; just few hour ago. What&#8217;s wrong?

The exception was coming out of System.Net.HttpListener (I write in C#) and the message was following: _**System.Net.HttpListenerException (0x80004005): The process cannot access the file because it is being used by another process.**_

Maybe there is a bastard process from the previous run? I checked Process Explorer &#8211; nothing. I also have ISS up and running &#8211; which I decided to stop:

{% highlight bash %}iisreset -stop{% endhighlight %}

I couldn&#8217;t do that either, it would throw a an error. &#8220;That&#8217;s getting more interesting&#8221;, I thought. Well, most likely something is using ports that my web service is listening on. Which port would it be? I had only 80 and 8080 ports opened on my web service. But what is it?

{% highlight bash %}C:>netstat -ano | findstr :80 | findstr LISTENING
  TCP    0.0.0.0:80      0.0.0.0:0  LISTENING       6112{% endhighlight %}

OK, so the PID of the server is 6112, let&#8217;s take a look what it is. Skype! Wow, that&#8217;s interesting &#8211; it was running in the background and I never had issues with it, but for whatever reason it started to listen on that port. I killed skype process and moved on to debugging my code.