---
layout: post
title:  "FreeBSD watching user activity"
date:   2016-11-21 16:02:05 +0000
---

Whenever you need to help another user or see what's going on another terminal you can use [watch](http://man.freebsd.org/watch).


To determine user terminal.

{% highlight shell %}
$ who
Brop            pts/0        Nov 17 21:25 (...)
Athu            pts/1        Nov 17 21:25 (...)
Vorturnal       pts/2        Nov 20 16:38 (...)
Operi           pts/3        Nov 21 16:05 (...)
Xisan           pts/4        Nov 21 16:32 (...)
Sadec           pts/5        Nov 21 16:38 (...)
{% endhighlight %}


Connect to terminal.

{% highlight shell %}
$ sudo watch pts/2
{% endhighlight %}


Connect with write access to observed terminal.

{% highlight shell %}
$ sudo watch -W pts/2
{% endhighlight %}


Exit watch.

{% highlight shell %}
<control-G>
{% endhighlight %}


Clear screen.

{% highlight shell %}
<control-W>
{% endhighlight %}


Change attached tty.

{% highlight shell %}
<control-X>
{% endhighlight %}

