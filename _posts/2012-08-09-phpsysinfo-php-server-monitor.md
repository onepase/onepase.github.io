---
id: 54
title: 'PhpSysInfo &#8211; Php Server Monitor'
date: 2012-08-09T01:16:31+00:00
author: Hakan
layout: post
permalink: /phpsysinfo-php-server-monitor/
categories:
  - PHP
tags:
  - load average
  - php server monitor
  - phpsysinfo
---
Bugünlerde php tabanlı ufak bi server monitor yazma niyetim var. Aslında bana lazım olan load average değerlerini grafik üzerinde göstermekti. Nitekim bi kahve içene kadar yazıldı. Araştırırken PhpSysInfo isimli betiğe rastladım ve deneyince beğendiğimi söyleyebilirim.

Betik için kuruluma gerek yok, direkt olarak <http://phpsysinfo.sourceforge.net/> adresinden betiği edinebilirsiniz. Arşivi server dizinine çıkadıktan sonra arşivden çıkardığınız dosyalar arasında config.php.new isimli bir dosya göreceksiniz. Betik çalışmak için bu ayar dosyasına ihtiyaç duyuyor. config.php.new dosya ismini config.php olarak değiştirmeniz acemi kullanıcı için yeterli olacaktır. Zaten config dosyası içerisinde gerekli açıklamlar yapılmış durumda. Bu arada Türkçe desteği ve tema seçenekleri mevcut.

Ek olarak kaynakları fazla tüketmemek adına default olarak gelen 1 dakikalık yenileme süresini fazla kısaltmamanızı ve işlemci kullanımını göstermemenizi öneririm.

Ekran görüntüsü fikir sahibi olmanıza yardımcı olacaktır.