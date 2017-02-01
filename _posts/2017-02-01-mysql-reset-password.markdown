---
layout: post
title:  "MySQL reset password"
date:   2017-02-01 19:00:00 +0000
---

Sometimes passwords are lost ..., however in most cases we can find a workaround and reset the missing password.

First stop MySQL service, then we can start it in background without loading [grant
table](https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_skip-grant-tables).

{% highlight shell %}
$ mysqld_safe --skip-grant-tables --skip-networking &
{% endhighlight %}

Now we can connect to MySQL without password ...
Update root password:

{% highlight shell %}
$ mysql -e " \
  UPDATE mysql.user \
  SET \
    authentication_string = PASSWORD('new_password') \
  WHERE \
    User = 'root' \
  AND \
    Host = 'localhost' \
;"
{% endhighlight %}

All done, time to stop current running instance and start MySQL service as normal.

{% highlight shell %}
$ pkill mysql
{% endhighlight %}

