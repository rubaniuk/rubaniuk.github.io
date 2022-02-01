---
layout: post
title:  "Updating Ruby on Apple M1 MacBook"
date: 2022-01-31 22:49:00 -0000
categories: jekyll apple m1
---

After a 12 months long hiatus I started blogging again. Expired TLS certificate and the process of transitioning to LetsEncrypt were the inspiration and motivated me to share the knowledge with the world.

I also need to mention that I had to update Ruby on my Apple M1-powered MacBook as I was getting tons of errors when trying to re-build the blog. Note that I had the latest macOS Monterey which comes with pre-installed Ruby 2.7.0, but it wouldn't work for me. I needed to update the version that I previously installed via Homebrew. 

After some trial and error, I stumbled upon "The Definitive Guide To Installing Ruby Gems on a Mac" by Moncef Belyamani. The guide was excellent and I specifically followed all steps in section <a href="https://www.moncefbelyamani.com/the-definitive-guide-to-installing-ruby-gems-on-a-mac/?utm_source=stackoverflow&utm_campaign=51126403#homebrew-ruby" target="_blank">Install Ruby with Homebrew</a>.

The following version was installed side-by-side with the one Apple provides:

{% highlight md %}
ruby -v                                                 
ruby 3.0.3p157 (2021-11-24 revision 3fb7d2cadc) [x86_64-darwin21]
{% endhighlight %}


Jekyll was still giving me trouble, this time due to missing webrick - apparently Ruby 3.0 lacks that packages: <a href="https://github.com/github/pages-gem/issues/752" target="_blank">Jekyll serve fails on Ruby 3.0 (webrick missing) #752</a>.

I quickly resolved it by adding webrick...

{% highlight md %}
bundle add webrick
{% endhighlight %}


... and re-built and tested my blog:

{% highlight md %}
bundle exec jekyll build --verbose
bundle exec jekyll serve --trace --watch --incremental
{% endhighlight %}