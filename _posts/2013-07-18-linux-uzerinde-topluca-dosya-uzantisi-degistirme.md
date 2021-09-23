---
title: Linux Üzerinde Topluca Dosya Uzantısı Değiştirme
date: 2013-07-18T15:39:15+00:00
layout: post
permalink: /linux-uzerinde-topluca-dosya-uzantisi-degistirme/
img: linux-terminal.jpg
tags:
  - değiştirme
  - dosya
  - içindeki
  - isim
  - klasör
  - linux
  - toplu
  - uzantı
---
Linux üzerinde bir dizin içinde bulunan belirli dosya uzantılarını değiştirmek, örnek olarak .html uzantılarını .htm olarak değiştirmek için;

{% highlight bash %}
rename s/.html/.htm/ *.html
{% endhighlight %}