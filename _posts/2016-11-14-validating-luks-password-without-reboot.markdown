---
layout: post
title:  "Validating LUKS password without reboot"
date:   2016-11-14 7:29:00 +0000
---

Before rebooting a "new" server for the first time, is worth to check for encrypted drives and validate the password.
For [LUKS](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup) we can use [cryptsetup](https://linux.die.net/man/8/cryptsetup).

{% highlight shell %}
$ cryptsetup luksOpen /dev/drive_name tmp_name --verify-passphrase --verbose
{% endhighlight %}

