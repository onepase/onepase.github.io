---
id: 34
title: PHP Session Kullanımı
date: 2011-12-28T02:12:01+00:00
author: Hakan
layout: post
permalink: /php-session-kullanimi/
categories:
  - PHP
tags:
  - php
  - session
  - php session kullanımı
  - php oturum yönetimi
---
PHP'de kullanıcı oturumlarını yönetmek için birtakım fonksiyon kullanılır. İnternet sitesini ziyaret eden her bir kullanıcı için, sunucu üzerinde bir dosya oluşturulur ve kullanıcı oturumuna ait veriler bu dosya içerisine kaydedilir. Sunucu üzerinde bulunan session dosyası ile ziyaretçinin eşleştirilmesi için ise, istemci üzerinde bir cookie oluşturulur. Tüm bu işlemler için PHP session fonksiyonları ve başlatılmış oturumlar için kullanılan $_SESSION dizisi ile kabaca oturum yönetimi yapılabilir.

PHP'de bir oturum başlatmak için en yalın haliyle aşağıdaki gibi bir kod çalıştırılabilir.

{% highlight php %}
<?php
session_start();
$username = "Test";
$_SESSION["username"] = $username;
?>
{% endhighlight %}

Buradaki session_start() fonksiyonuyla yeni bir oturum başlatılır. Oturum başlatıldıktan sonra, oturum verilerinin tutulacağı $_SESSION dizisine, username isimli değişkendeki veri atanır.


{% highlight php %}
<?php
session_start();
echo "Kullanıcı Adı:".$_SESSION["username"];
?>
{% endhighlight %}

Burada ise session_start() ile oturum başlatılarak daha önce $_SESSION['username'] değişkenine atanan veri ekrana yazdırılır.

Herhangi bir zaman, oturum sonlandırılmak ve session verileri silinmek istenirse session_destroy() fonksiyonu çalıştırılır.



