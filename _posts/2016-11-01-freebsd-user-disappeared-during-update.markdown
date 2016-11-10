---
layout: post
title:  "FreeBSD user disappeared during update?"
date:   2016-11-01 12:42:05 +0000
---

When creating new user you hit this error?

{% highlight shell %}
pw: user 'testuser' disappeared during update
adduser: ERROR: There was an error adding user (testuser).
{% endhighlight %}

Try rebuilding your [password database](https://www.freebsd.org/cgi/man.cgi?query=pwd_mkdb).

{% highlight shell %}
$ sudo pwd_mkdb /etc/master.passwd
{% endhighlight %}

