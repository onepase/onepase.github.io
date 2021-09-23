---
title: 'Email Adres Formatı, PHP filter_var Fonksiyonu ve RFC 5321'
date: 2018-07-07T00:15:06+00:00
author: Hakan
layout: post
permalink: /email-adres-formati-php-filter-var-fonksiyonu-ve-rfc-5321/
categories: Genel
tags: [email adres formatı, php filter_var fonksiyonu, rfc 5321]
img: email.jpg
---

Email adres formatı Rfc 5321 ile belirlenmiş durumda. Fakat pratikte işler biraz değişiyor. Rfc5321 bir email adresinin şu şekilde olabileceğini bize söylüyor. 

local-part@domain

Domain bölümü herhangi bir domain veya sub-domain olabilir, hatta tld olmayan local bir domain de olabilir. Fakat local-part bölümü için şu kısıtlar var.

- A-Z, a-z latin karakterler
- 0-9 rakamlar
- İlk ve son karakter olmamak kaydıyla nokta (.) karakteri
- Özel karakterler !#$%&'*+-/=?^_`{|}~

Özel karakterler arasında - ve _ karakterlerine aşinayız fakat diğer özel karakterler hiç yaygın değil. Popüler email servislerinden Google'ın email servisi özel karakterlere izin vermezken, Microsoft'un email servisi ise yalnızca - ve _ özel karakterlerine izin veriyor. Farklı bir servis için ise şöyle bir adres mümkün olabilir.

{% highlight php %}
john`doe{software-developer}@domain.sub-domain.com
{% endhighlight %}

PHP filter_var fonksiyonu ile email adres formatının kontrolü sağlandığında

{% highlight php %}
filter_var('john`doe{software-developer}@domain.sub-domain.com',FILTER_VALIDATE_EMAIL)
{% endhighlight %}

bize Rfc 5321'de açıklanan formata uyduğu için false bir değer döndürmeyecek ancak domain bölümünün gmail olması durumunda, gmail implementasyonu farklı olduğu için olmaması gereken bir email adresini doğru kabul etmiş olacağız. Standart dışı bir kütüphane veya farklı bir yöntemle doğrulama yapmaya çalışıldığı zaman ise işler iyice içinden çıkılmaz bir hal alacaktır. Olası bir senaryoda, popüler email servislerine yönelik bir doğrulama Rfc 5321'e göre uygulanmış bir başka email servisi için hatalı sonuç verecektir. Çok dilli bir sistemde, bölgesel ve farklı dillerde kullanılan email servislerinin olması durumunda ise sonuç tam anlamıyla facia!
