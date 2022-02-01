---
layout: post
title:  "Migrating Jekyll Blog's SSL certificate to LetsEncrypt"
date: 2022-01-31 21:51:00 -0000
categories: jekyll ssl certificate letsencrypt
---

I recently got a notice from my domain provider that my SSL certificate for www.rubaniuk.com will expire in 1 month and that I need to renew it. I opened this blog and noticed that the certificate has expired already, I decided to dig deeper and found out that GitHub Pages aren't receiving new cert from my Certificate Authority!

This wasn't great user experience and that got me thinking: what if I swithced to free LetsEncrypt Certificate Authority? Let's do just that! 

First, let's delete existing CNAME file with domain in it:

{% highlight md %}
git rm CNAME 
git commit -m "Deleting custom domain"  
git push
{% endhighlight %}

Second, let's configure <a href="https://support.dnsimple.com/articles/caa-record/" target="_blank">Certification Authority Authorization record</a> (CAA record) - you can do it in settings for your domain at your domain registrar's website. For my custom domain the settings were as follows:

{% highlight md %}
Type        Host                Value                       TTL
CAA Record  www.rubaniuk.com    0 issue "letsencrypt.org"   Automatic
{% endhighlight %}


Third step - let's re-create CNAME file with the custom domain as the only line in it:

{% highlight md %}
echo www.rubaniuk.com > CNAME 
git add CNAME 
git commit -m "Re-enable custom domain after configuring CAA record/letsencrypt"
git push
{% endhighlight %}

The TLS certificate was issued nearly instantly and I was able to check "Enforce HTTPS".

LetsEncrypt updates TLS certificates every 90 days. The cert was had an expiration date of "Saturday, April 30, 2022 at 9:03:18 PM Pacific Daylight Time" at the moment of writing this post. 

The certificate should auto-renew in 90 days and I will post an update if I see any issues.
