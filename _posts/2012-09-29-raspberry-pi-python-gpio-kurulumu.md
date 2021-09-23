---
id: 63
title: 'Raspberry Pi &#8211; Python GPIO Kurulumu'
date: 2012-09-29T02:49:37+00:00
author: Hakan
layout: post
permalink: /raspberry-pi-python-gpio-kurulumu/
categories:
  - Linux
tags:
  - gpio
  - kurulum
  - pypi
  - python
  - raspberry
  - raspberry pi
  - raspbian
---
Raspberry Pi Gpio pinlerini Python ile kullanabilmek için Python Gpio modülünü kurmak gerekiyor. Kurulum için terminalden sıkıştırılmış modül arşivinin indirileceği dizine geçtikten sonra sırasıyla aşağıdaki komuları işletmek yeterli.

{% highlight bash %}
$ wget http://pypi.python.org/packages/source/R/RPi.GPIO/RPi.GPIO-0.1.0.tar.gz
  
$ tar zxf RPi.GPIO-0.1.0.tar.gz
  
$ cd RPi.GPIO-0.1.0
  
$ sudo python setup.py install
{% endhighlight %}