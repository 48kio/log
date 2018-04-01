---
layout: post
title:  "Fedora kernel lock"
date:   2018-03-25 13:15:00 +0000
---

{% highlight shell %}

$ sed -i -e "s/UPDATEDEFAULT=yes/UPDATEDEFAULT=no/" /etc/sysconfig/kernel

{% endhighlight %}
