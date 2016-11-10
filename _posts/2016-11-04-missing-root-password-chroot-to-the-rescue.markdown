---
layout: post
title:  "Missing root password - chroot to the rescue!"
date:   2016-11-04 20:12:00 +0000
---

Few days ago I was recovering a lost root password on one of my FreeBSD servers - no sudo or NIS to override.

But there's always [chroot](https://www.freebsd.org/cgi/man.cgi?chroot(8)), below pieces of the process.

{% highlight shell %}
$ gpart show

=>       63  976773105  ada0  MBR  (466G)
         63  976773105     1  freebsd  [active]  (466G)

=>        0  976773105  ada0s1  BSD  (466G)
          0   40960000       1  freebsd-ufs  (20G)
   40960000  934762496       2  freebsd-ufs  (446G)
  975722496    1050609       4  freebsd-swap  (513M)

=>       63  976773105  diskid/DISK-MSK421Y21NH0SB  MBR  (466G)
         63  976773105                           1  freebsd  [active]  (466G)

=>        0  976773105  diskid/DISK-MSK421Y21NH0SBs1  BSD  (466G)
          0   40960000                             1  freebsd-ufs  (20G)
   40960000  934762496                             2  freebsd-ufs  (446G)
  975722496    1050609                             4  freebsd-swap  (513M)
{% endhighlight %}


So the drive got 3 partition 2 ufs and swap, let's try to mount first partition.

{% highlight shell %}
$ fsck -t ufs /dev/ada0s1

ada0s1%  ada0s1a% ada0s1b% ada0s1d%
{% endhighlight %}


{% highlight shell %}
$ fsck -t ufs /dev/ada0s1a

** /dev/ada0s1a

USE JOURNAL? [yn] y

** SU+J Recovering /dev/ada0s1a
** Reading 33554432 byte journal from inode 4.

RECOVER? [yn] y

** Building recovery table.
** Resolving unreferenced inode list.
** Processing journal entries.

WRITE CHANGES? [yn] y

** 305 journal records in 11264 bytes for 86.65% utilization
** Freed 0 inodes (0 dirs) 150 blocks, and 0 frags.

***** FILE SYSTEM MARKED CLEAN *****


$ mount -t ufs /dev/ada0s1a /mnt
{% endhighlight %}


In situation like this is always worth to check fstab.

{% highlight shell %}
$ cat /mnt/etc/fstab
# Device                Mountpoint      FStype  Options         Dump    Pass#
/dev/ada0s1a            /               ufs             rw      1       1
/dev/ada0s1b            /usr            ufs             rw      2       2
/dev/ada0s1d            swap            swap            sw      0       0
proc                    /proc           procfs  rw              0       0
{% endhighlight %}

Time to mount the second disk to get access to the /usr partition.

{% highlight shell %}
$ fsck -t ufs /dev/ada0s1b
** /dev/ada0s1b

USE JOURNAL? [yn] y

** SU+J Recovering /dev/ada0s1b
** Reading 33554432 byte journal from inode 4.

RECOVER? [yn] y

** Building recovery table.
** Resolving unreferenced inode list.
** Processing journal entries.

***** FILE SYSTEM MARKED CLEAN *****


$ mount -t ufs /dev/ada0s1b /mnt/usr
{% endhighlight %}


Seems like everything's in place, time to chroot into the system and reset the password.

{% highlight shell %}
$ chroot /mnt

$ passwd
Changing local password for root
New Password:
Retype New Password:

$ exit

$ reboot
{% endhighlight %}

