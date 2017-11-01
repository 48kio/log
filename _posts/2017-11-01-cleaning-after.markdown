---
layout: post
title:  "Cleaning after doF*&r"
date:   2017-11-01 18:00:00 +0000
---

{% highlight shell %}
# kill all running docker containers
$ docker kill $(docker ps -q)
{% endhighlight %}

{% highlight shell %}
# remove all containers
$ docker rm $(docker ps -aq)
{% endhighlight %}

{% highlight shell %}
# remove all images
$ docker rmi $(docker images -q)
{% endhighlight %}

{% highlight shell %}
# remove unused volumes
$ docker volume rm $(docker volume ls -qf dangling=true)
{% endhighlight %}

{% highlight shell %}
# clean network interfaces
$ docker network rm $(docker network ls | awk '$3 == "bridge" && $2 != "bridge" { print $1 }')
{% endhighlight %}


