---
layout: post
title:  "Few tips for working with FreeBSD ports"
date:   2016-11-13 17:19:00 +0000
---

[The FreeBSD Ports and Packages Collection offers a simple way for users and administrators to install applications.](https://www.freebsd.org/ports/index.html)


To initialize ports collection for the first time.

{% highlight shell %}
$ portsnap fetch extract
{% endhighlight %}


To update ports collection.

{% highlight shell %}
$ portsnap fetch update
{% endhighlight %}


When you are building ports and want to skip the configuration questions.

{% highlight shell %}
$ export BATCH=yes
{% endhighlight %}


To clean up port build environment with all dependencies.

{% highlight shell %}
$ make clean clean-depends rmconfig
{% endhighlight %}

