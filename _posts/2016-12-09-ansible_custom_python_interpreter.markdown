---
layout: post
title:  "Ansible custom Python interpreter"
date:   2016-12-09 10:16:00 +0000
---

**[ansible_python_interpreter](http://docs.ansible.com/ansible/intro_inventory.html#list-of-behavioral-inventory-parameters)** - target host python path, useful for systems with multiple Python interpreters or not located at */usr/bin/python*.


You can change interpreter location using [host variables](http://docs.ansible.com/ansible/intro_inventory.html#host-variables).

{% highlight yml %}
freebsd_host    ansible_python_interpreter=/usr/local/bin/python
{% endhighlight %}


Or by [playbook variables](http://docs.ansible.com/ansible/playbooks_variables.html#hey-wait-a-yaml-gotcha).

{% highlight yml %}
---
- name: main build
  hosts: freebsd_host
  vars:
    ansible_python_interpreter: "/usr/local/bin/python2"
  roles:
    - common
{% endhighlight %}

