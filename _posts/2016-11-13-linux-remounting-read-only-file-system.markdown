---
layout: post
title:  "Linux remounting read only file system"
date:   2016-11-13 17:26:00 +0000
---

When you stuck with read only file system, remember [mount](https://linux.die.net/man/8/mount) can help.

{% highlight shell %}
$ mount -n -o remount /
{% endhighlight %}

