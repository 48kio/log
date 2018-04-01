---
layout: post
title:  "Fedora searching for space on /"
date:   2018-03-25 13:00:00 +0000
---

{% highlight shell %}
# let's check for journal disk space
$ journalctl --disk-usage
Archived and active journals take up 11.0G in the file system.

# time to clean up
$ journalctl --vacuum-time=1d
Deleted archived journal ...
Deleted archived journal ...
Deleted archived journal ...

Vacuuming done, freed 10.4G of archived journals from ... .
{% endhighlight %}


{% highlight shell %}

$ du -csh /var/cache/PackageKit/* | sort -h
5G      /var/cache/PackageKit/25
3.1G    /var/cache/PackageKit/26
1.2G    /var/cache/PackageKit/27
9.3G    total


$ pkcon refresh force -c -1
Refreshing cache                    [=========================]
Loading cache                       [=========================]
Downloading repository information  [=========================]
...
...
...
Finished                            [=========================]


# I don't need cache from older releases...
$ rm -rf /var/cache/PackageKit/25 /var/cache/PackageKit/26

$ du -csh /var/cache/PackageKit/* | sort -h
192M    /var/cache/PackageKit/27
192M    total

{% endhighlight %}
