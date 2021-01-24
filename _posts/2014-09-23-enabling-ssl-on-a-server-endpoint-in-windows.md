---
# id: 335
title: Enabling SSL on a server endpoint in Windows
date: 2014-09-23T13:30:49-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=335
# permalink: /?p=335
categories:
  - Uncategorized
---
The task of enabling SSL on your server is very simple. It doesn&#8217;t require any code changes assuming your server is already listening on http**s **and port 443.

Prerequisite:

  * On the server install a server-side certificate (includes private key) that can be verified by the client, i.e. it chains to a Trusted Root certificate that is installed on the client. This certificate should go into **Certificates (Local Computer)\Personal\Certificates\**. Also, make sure that the certificate&#8217;s subject is issued for your URL.

The actual steps of configuring SSL on the server is very simple:

  1. From elevated command line execute following command to **delete all previous bindings** for port 443 (obviously, port can be different): 
  
  <pre class="brush: bash; gutter: true">netsh http delete sslcert ipport=0.0.0.0:443</pre>

  2. From elevated command line establish binding between certificate and port: 
  
  <pre class="brush: bash; gutter: true">netsh http add sslcert ipport=0.0.0.0:443 certhash=YourCertHash appid={YOUR-APP-ID} certstorename=MY</pre>

Successful response to the first command is &#8220;SSL Certificate successfully deleted&#8221;, for the second is &#8220;SSL Certificate successfully added&#8221;. You can also see your SSL bindings using following command:

<pre class="brush: bash; gutter: true">netsh http show sslcert</pre>

At this point you should be good to go &#8211; make a call from the client to your server and SSL should be established.

Good luck and let me know if you run into issues!