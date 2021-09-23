---
id: 77
title: 'Irssi &#8211; Konsol Tabanlı IRC Client'
date: 2013-01-13T01:30:14+00:00
author: Hakan
layout: post
permalink: /irssi-konsol-tabanli-irc-client/
categories:
  - Linux
tags:
  - archlinux
  - client
  - irc
  - irssi
  - komut
  - komutları
  - kullanımı
  - kurulum
  - linux
  - setup
---
Irc günümüzde popülerliğini yitirmiş olsa da zamanın en popüler protokollerinden biriydi. Linux kullanıcıları tarafından IRC hala aktif olarak kullanılıyor. 

Linux üzerinde Xchat, Windows üzerinde Mirc en popüler clientlar. Linux üzerinde konsol tabanlı Irssi ise görevini başarıyla yerine getiren bir IRC client. 

Dağıtımınıza göre paket yöneticinizden kurulumu tamamladıktan sonra, konsolda &#8220;irssi&#8221; komutuyla irssi başlatılabilir. Öncelikle bir irc server ekleme işlemi, örnek olarak irc.freenode.net ve kısa isim olarak freenode ile;

{% highlight bash %}
/server add -network freenode irc.freenode.net
{% endhighlight %}

İlgili sunucuya bir kanal eklemek için, örnek olarak freenode ismini verdiğimiz sunucuya #perl kanalı;

{% highlight ruby %}
/channel add #perl freenode
{% endhighlight %}

#perl kanalına katılmak için

{% highlight ruby %}
/join #perl
{% endhighlight %}

komutu kullanılabilir. Irssi her başlangıçta yeniden ekleme işlemlerini tekrarlamamak için;

{% highlight bash %}
/server add -auto -network freenode irc.freenode.net
  
/network add -nick username
  
/channel add -auto #perl freenode
  
/channel add -auto #kanalismi freenode
  
/save
  
/quit
{% endhighlight %}

komutları ile ~/.irssi/config dosyasına kayıt işlemi gerçekleştirilebilir ve irssi başlangıcında otomatik olarak server ve kanal ekleme işlemleri ile birlikte nick belirleme işlemi gerçekleştirilebilir.

Son olarak Irssi ekran görüntüsü;