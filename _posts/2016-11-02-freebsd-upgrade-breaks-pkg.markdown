---
layout: post
title:  "FreeBSD upgrade breaks PKG?"
date:   2016-11-02 16:15:00 +0000
---

After Upgrading FreeBSD to new version pkg is throwing similar error?

{% highlight shell %}
$ pkg
Shared object "libssl.so.7" not found, required by "pkg"
{% endhighlight %}


Remember! You can always reinstall pkg using [static version](https://www.freebsd.org/cgi/man.cgi?query=pkg-static).

{% highlight shell %}
$ sudo pkg-static install -f pkg

Updating FreeBSD repository catalogue...
[work] Fetching meta.txz: 100%    944 B   0.9kB/s    00:01
[work] Fetching packagesite.txz: 100%    6 MiB   5.8MB/s    00:01
Processing entries: 100%
FreeBSD repository update completed. 25384 packages processed.
New version of pkg detected; it needs to be installed first.
The following 1 package(s) will be affected (of 0 checked):

Installed packages to be UPGRADED:
        pkg: 1.8.7_3 -> 1.8.8

Number of packages to be upgraded: 1

3 MiB to be downloaded.

Proceed with this action? [y/N]: y
[work] Fetching pkg-1.8.8.txz: 100%    3 MiB   2.9MB/s    00:01
Checking integrity... done (0 conflicting)
[work] [1/1] Upgrading pkg from 1.8.7_3 to 1.8.8...
[work] [1/1] Extracting pkg-1.8.8: 100%
Updating FreeBSD repository catalogue...
FreeBSD repository is up-to-date.
All repositories are up-to-date.
Checking integrity... done (0 conflicting)
The following 1 package(s) will be affected (of 0 checked):

Installed packages to be REINSTALLED:
        pkg-1.8.8

Number of packages to be reinstalled: 1

Proceed with this action? [y/N]: y
[work] [1/1] Reinstalling pkg-1.8.8...
[work] [1/1] Extracting pkg-1.8.8: 100%
{% endhighlight %}

