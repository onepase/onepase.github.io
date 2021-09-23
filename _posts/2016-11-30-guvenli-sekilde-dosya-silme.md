---
title: 'Güvenli Şekilde Dosya Silme'
date: 2016-11-30T00:00:00+00:00
author: Hakan
layout: post
permalink: /guvenli-sekilde-dosya-silme/
categories: Genel
tags: [güvenli dosya silme, kalıcı dosya silme, shred, osx srm, eraser]
img: post/guvenli-sekilde-dosya-silme.jpg
---

Bilgisayar sistemlerinde, dosya sistemi üzerinden kullanıcı tarafından silinen bir dosyanın çoğu zaman geri getirilmesi mümkündür. Sistemler çoğu zaman performansı iyileştirmek adına, dosyaları silmek yerine sadece işletim sistemi tarafından görüntülenmesini durdurur. Esasında kullanıcı tarafından verilen, windows kullanıcıları için delete,shift+delete linux ve osx kullanıcıları için rm ve masaüstü yöneticisinden yapılan sil komutu ve tüm çöp/geri dönüşüm kutusu işlemleri disk üzerinde gerçek bir silme işlemi gerçekleştirmez.

Bilgisayarın el değiştirmesi, geri dönüşüme kazandırılması, ticari veya bireysel kaygılar güvenli dosya silmenizi gerektirecek başlıca sebepler.

Tam ve güvenli bir dosya silme işlemi genellikle ilgili dosyanın disk üzerindeki alanına rastgele veri yazılması-silinmesi işleminin tekrarlanması sonucunda gerçekleşir. Manyetik diskler üzerindeki dosya izleri bu sayede silinen dosyayla ilgili bir veri içermeyecek hale getirilir.

**Linux Kullanıcıları**

Linux kullanıcıları, çoğu dağıtımda önyüklü olarak gelen shred aracı ile tam ve güvenli bir silme işlemi gerçekleştirebilir. Shred komut satırı üzerinden çalışan bir araçtır.

{% highlight c %}
shred -uzfv -n 20 ornekdosya.txt
{% endhighlight %}

Yukarıdaki komut ile ornekdosya.txt dosyasının disk üzerindeki alanına 20 kez rastgele veri yazılır ve 21.kez tüm dosya alanı 0 ile doldurulur. Dosya ismi defalarca değiştirilir ve sonucunda güvenli bir şekilde dosya silme işlemi gerçekleşmiş olur.

![Linux Shred]({{ site.baseurl }}/assets/images/post/linux-shred-dosya-silme.png "Linux Shred")

**OsX Kullanıcıları**

OsX kullanıcıları ise işletim sistemi üzerinde gelen, komut satırı üzerinden kullanılan srm aracı ile güvenli silme işlemi gerçekleştirebilirler.

{% highlight c %}
srm ornekdosya.txt

srm -r ornekdizin
{% endhighlight %}

**Windows Kullanıcıları**

Windows kullanıcıları benzer işlemleri gerçekleştirerek güvenli dosya silme işlemi için https://eraser.heidi.ie/ adresindeki aracı kullanabilir.

Son olarak Bilgisayar sistemlerinde 100% güvenlidir ifadesi her zaman için doğru olmayabilir. Anlatılan silme işlemleri sonucunda, özellikle manyetik disklerde ilgili dosyayla ilgili bazı küçük izlere ulaşmak imkansıza yakın olmakla birlikte mümkündür.
