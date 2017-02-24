---
layout: post
title:  "ESXi 5 and nested virtualization"
date:   2017-02-24 10:00:00 +0000
---

Trying to use [virtualization](https://en.wikipedia.org/wiki/Virtualization) inside a guest OS but error pops up?

{% highlight shell %}
KVM: no hardware support
{% endhighlight %}

on a ESXi host one can easy turn on the [nested virtualization](https://en.wikipedia.org/wiki/Virtualization#NESTED) by editing the .vmx file

{% highlight shell %}
$ vim-cmd vmsvc/getallvms
{% endhighlight %}

make a note of vmID, file name and data store

{% highlight shell %}
$ cat << EOF >> /vmfs/volumes/$DATA_STORE/$FILE_NAME.vmx
vhv.enable = "TRUE"
EOF

$ vim-cmd vmsvc/reload $vmID
{% endhighlight %}

