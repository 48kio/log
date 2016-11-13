---
layout: post
title:  "MySQL default Character Set and Collation"
date:   2016-11-13 17:09:00 +0000
---

[MySQL default character set and collation is set to latin1 & latin1_swedish_ci](https://dev.mysql.com/doc/refman/5.7/en/charset-applications.html), however most application these days requiring [UTF-8](https://en.wikipedia.org/wiki/UTF-8),  you can always specifying the character set and collation manually using [CREATE DATABASE](https://dev.mysql.com/doc/refman/5.7/en/create-database.html) statement

{% highlight shell %}
CREATE DATABASE dbname CHARACTER SET utf8 COLLATE utf8_general_ci;
{% endhighlight %}


You can also specify character settings at server startup [--character-set-server](https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_character-set-server) and [--collation-server](https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_collation-server) options, or include these lines in configuration file.

{% highlight shell %}
[mysqld]
character-set-server=utf8
collation-server=utf8_general_ci
{% endhighlight %}

