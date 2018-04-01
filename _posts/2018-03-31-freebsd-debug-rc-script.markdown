---
layout: post
title:  "FreeBSD debug rc.d script"
date:   2018-03-31 10:05:00 +0000
---

Debugging rc.d scripts can be… always remember to set

{% highlight shell %}

sysrc rc_debug="YES"
sysrc rc_info="YES"

{% endhighlight %}

or set **-x** flag in rc script

{% highlight shell %}

$ printf '%s\n' 1a 'set -x' . w | ed -s /etc/rc.d/serviceScriptName

{% endhighlight %}
