---
id: 32
title: 'Ubuntu 11.10 - Ubuntu Classic Kullanmak'
date: 2011-12-25T21:44:53+00:00
author: Hakan
layout: post
permalink: /ubuntu-11-10-ubuntu-classic-kullanmak/
categories:
  - Genel
tags:
  - linux
  - ubuntu
  - ubuntu-classic
---
Ubuntu 11.10 dağıtımı ile birlikte gelen unity klasik Gnome Ubuntu kullanıcılarını çileden çıkarmaya devam ediyor. Klasik Gnome görünümü için Ubuntu 11.04 Natty'de Login kısmında Ubuntu Classic seçilerek sorun çözülüyordu ancak Ubuntu 11.10'da bu durum ortadan kalkmış durumda. Ancak bunu kısmen çözmek mümkün.

Bunun için ubuntu-shell ve ubuntu-session-fallback paketlerinin kurulması gerek. Bunun için;

{% highlight bash %}
apt-get install ubuntu-shell

apt-get install ubuntu-session-fallback
{% endhighlight %}

ile paketleri kuruyoruz ve ardından tekrar login oluyoruz. Login olurken sağdaki seçenekler ikonu vasıtasıyla Ubuntu Classic seçiyoruz. Bu kısmen sorunu çözüyor. Ancak benim gibi root olarak sisteminizi kullanıyorsanız sorun yaşayabilirsiniz. Root olarak login olmak isterseniz Ubuntu Classic kullanamıyorsunuz ancak normal kullanıcı rollerinde bir problem yok.

Şahsen tekrardan Ubuntu 11.04'e ya da Xubuntu'ya geçmeyi düşünüyorum.