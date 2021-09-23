---
title: Linux Üzerinde Mplayer İle Radyo Yayını Dinlemek
date: 2013-08-02T03:32:37+00:00
author: Hakan
layout: post
permalink: /linux-uzerinde-mplayer-ile-radyo-yayini-dinlemek/
categories:
  - Linux
tags:
  - dinle
  - how to
  - konsol
  - linux
  - mplayer
  - nasıl
  - radio
  - radyo
  - stream
---
Linux üzerinde radyo yayını dinlemek isteyebilirsiniz. Bunun için vlc,mplayer gibi medya oynatıcıları kullanabilirsiniz. Renkli renkli grafiklerden haz etmeyen biriyseniz mplayer sizin aradığınız şey. Mplayer ile konsol üzerinde radyo yayını dinlemek için;
  
Örnek olarak Özgür radyo stream için "canliyayin.ozgurradyo.com" adresi üzerinden 8100 portunu kullanıyor. 

{% highlight bash %}
mplayer -nolirc http://canliyayin.ozgurradyo.com:8100
{% endhighlight %}

komutunu kullanmak yeterli.