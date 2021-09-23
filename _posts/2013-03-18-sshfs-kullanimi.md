---
title: Sshfs Kullanımı
date: 2013-03-18T01:58:28+00:00
layout: post
permalink: /sshfs-kullanimi/
img: linux-terminal.jpg
tags:
  - ssfs
  - sshfs kullanımı
  - sshfs nedir
  - sshfs ubuntu kurulumu
---
İki uç sistem arasında dosya transferi çoğu zaman zahmetli bir iştir. Çeşitli dosya aktarım protokolleri bu işler için kullanılmakta. Sshfs ile herhangi bir uç sistemdeki dosya sistemini kendi makinenize bağlayabilirsiniz. SSHFS ile bağlanan dosya sistemi kendi makinenizdeymiş gibi davranır ve üzerinde işlem yapmak gayet kolaydır. 

Öncelikle kullandığınız paket yöneticisi ile sshfs (Secure Shell Filesystem) kurulumunu gerçekleştiriyoruz. Örnek olarak Ubuntu: 

{% highlight bash %}
apt-get install sshfs
{% endhighlight %}


Kurulum gerçekleştikten sonra konsoldan;

{% highlight bash %}
sshfs kullanici@bağlanacak_ip:/dizin /localdizin formatında dosya sistemini bağlayabiliriz. 
{% endhighlight %}

Örnek olarak local ağınızdaki 192.168.1.65 ip adresine sahip sisteminize pase kullanıcısı olarak bağlanarak, /var/www dizinini kendi sisteminizde /home/server dizinine bağlayacaksanız;

{% highlight bash %}
sshsf pase@192.168.1.65:/var/www /home/server 
{% endhighlight %}

komutunu kullanmalısınız. Komut verildikten sonra ssh bağlantısı için onay istenecek ve 192.168.1.65 ip adresindeki sistem için pase kullanıcısının şifresi sorulacaktır. Sonrasında dosya sistemi bağlanacaktır.