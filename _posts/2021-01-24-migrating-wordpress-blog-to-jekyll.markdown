---
layout: post
title:  "Migrating WordPress blog to Jekyll"
date:   2021-01-24 22:53:00 -0800
categories: jekyll update
---
It was time for me to embrace GitHub Pages and migrate my blog from WordPress to Jekyll.

Why? WP is a great publishing platform, but I wanted something that requires minimal maintenance, doesn't ask me to renew web hosting and allows me to publish from command line. Jekyll checked all the boxes and I mostly followed Bob Gale's <a href="https://www.bawbgale.com/from-wordpress-to-jekyll/" target="_blank">excellent migration guide</a>.

It wasn't as smooth as I anticipated. Even though all blog _posts, _drafts and wp-content were exported, I ran into issue where simply copying exported markdown files (.md) from _posts folder didn't work and I had to comment out id, guid and permalink (see below). After these changes posts showed mostly fine.

{% highlight md %}
# id: 433
title: Failed to connect to a Windows service
date: 2016-06-04T11:39:27-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=433
# permalink: /?p=433
...
{% endhighlight %}

I did write "mostly" because book reviews used WP book review plugin and I still need to do extra formatting in order to properly display these posts. 

Also, in multiple posts iframe wasn't exported at all so I had to do copy it manually from original posts.

After testing locally, I went ahead and <a href="https://www.namecheap.com/support/knowledgebase/article.aspx/9645/2208/how-do-i-link-my-domain-to-github-pages/" target="_blank">linked my domain to GitHub Pages</a> and <a href="https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain" target="_blank">configured custom domain rubaniuk.com</a> in the GitHub Pages settings for rubaniuk.github.io repo.

It took about 30 minutes for DNS settings to change. Note that TLS version wasn't available immediately and after waiting 2-3 hours for TLS certitifcate to be available, I enforced HTTPS in the GitHub Pages settings.

It's pretty liberating to be able to run an incremental Jekyll build and simply refresh your browser to see the changes:
<pre class="brush: bash; gutter: true">bundle exec jekyll serve --trace --watch --incremental</pre>

I still need to figure out custom themes and format book reviews.

Overall, I have no regrets and recommend Jekyll as a lightweight alternative to WP.