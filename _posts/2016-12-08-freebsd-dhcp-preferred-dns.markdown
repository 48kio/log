---
layout: post
title:  "FreeBSD DHCP Preferred DNS"
date:   2016-12-08 12:00:00 +0000
---

When you system is configured to use DHCP.

{% highlight shell %}
$ sysrc -n ifconfig_re0
DHCP
{% endhighlight %}

*/etc/resolv.conf* file will be regenerated on each system boot via [/sbin/dhclient-script](https://github.com/freebsd/freebsd/blob/release/11.0.0/sbin/dhclient/dhclient-script#L194).

However one would prefer to use [Public DNS Servers](https://duckduckgo.com/?q=Public+DNS+Servers&t=ffab&ia=answer&iax=1) instead the ones provided by the DHCP server.

According to [dhclient-script](https://man.freebsd.org/dhclient-script(8)#OPERATION) man page, we can change the behavior by overeating the **add_new_resolv_conf** function in */etc/dhclient-enter-hooks* file.

{% highlight shell %}
$ cat << EOF > /etc/dhclient-enter-hooks
add_new_resolv_conf() {
       return 0
}
EOF
{% endhighlight %}

Now we can safely edit */etc/resolv.conf* file - all changes will be persistent across system reboots.

