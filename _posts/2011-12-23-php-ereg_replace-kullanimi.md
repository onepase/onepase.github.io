---
id: 27
title: 'PHP ereg_replace Fonksiyonu'
date: 2011-12-23T10:33:55+00:00
author: Hakan
layout: post
permalink: /php-ereg_replace-kullanimi/
categories:
  - Genel
tags:
  - ereg_replace
  - ereg_replace fonksiyonu kullanımı
  - php ereg_replace fonksiyonu
---
Bazen PHP’de bir takım manipülasyonlar yapmanız gerekebilir. Bu anlarda kendi fonksiyonlarımız iş gördüğü gibi PHP fonksiyonları da imdadınıza koşuyor.

Şimdi bu fonksiyonlardan sadece birisi olan ereg_replace fonksiyonu hakkında biraz bilgi verelim. ereg\_replace fonksiyonu stringler üzerinde manipülasyon yapmanıza olanak sağlıyor. Örneğin;

"Bugün hava çok sisli" cümlesindeki sisli kelimesini yağmurlu ile değiştirmek için;

{% highlight php %}
<?php
$cumle="Bugün hava çok sisli";
$cumle=ereg_replace("sisli","yağmurlu",$cumle);
?>
{% endhighlight %}

gibi bir yöntem izlememiz gerekiyor. 

ereg_replace fonksiyonunun en basit haliyle kullanımı bu şekilde. İlerleyen safhalarda düzenli ifadelerle kullanılması ile birlikte, iş yükünü çok hafifleteceğini hatırlatayım.

Zamanın ötesinden not: PHP7 ile birlikte ereg_replace fonksiyonu tarihe karıştı.