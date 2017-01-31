---
layout: post
title:  "FreeBSD ttyv0 auto login"
date:   2017-01-30 13:00:00 +0000
---

Sometimes there's a need for auto login user over **serial** or **ttyv**

{% highlight shell %}
$ cat << EOF >> /etc/gettytab
autoLogin.Pc:\
  :ht:np:sp#9600:al=USER_NAME
EOF
{% endhighlight %}

{% highlight shell %}
$ grep ^ttyv0 /etc/ttys
ttyv0 "/usr/libexec/getty autoLogin.Pc"   xterm on  secure
{% endhighlight %}

[/etc/gettytab(5)](https://man.freebsd.org/gettytab(5)), [/etc/ttys(5)](https://man.freebsd.org/ttys(5))

