---
layout: post
title:  "FreeBSD securelevel"
date:   2016-11-25 19:00:00 +0000
---

[Securelevel](https://www.freebsd.org/doc/faq/security.html#idp60097128) is a security mechanism implemented in the kernel.


To check current 'secure level':

{% highlight shell %}
$ sysctl kern.securelevel
kern.securelevel: 2
{% endhighlight %}


To change / raise 'secure level':

{% highlight shell %}
$ sysctl kern.securelevel=2
{% endhighlight %}


To enable 'secure level' on boot:

{% highlight shell %}
$ sysrc kern_securelevel_enable="YES"
kern_securelevel_enable:  -> YES

$ sysrc kern_securelevel="2"
kern_securelevel:  -> 2
{% endhighlight %}


[FreeBSD security levels](https://man.freebsd.org/security(7)#SECURING_THE_KERNEL_CORE,_RAW_DEVICES,_AND_FILE_SYSTEMS)

