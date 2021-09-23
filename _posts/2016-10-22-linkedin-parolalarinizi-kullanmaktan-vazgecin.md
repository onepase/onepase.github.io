---
title: "Linkedin Parolalarınızı Kullanmaktan Vazgeçin"
date: 2016-10-22T00:00:00+00:00
author: Hakan
layout: post
permalink: /linkedin-parolalarinizi-kullanmaktan-vazgecin/
categories: Genel
tags: [linkedin, parola, güvenlik]
img: post/linkedin.jpg
---
Geçtiğimiz yıl Linkedin veritabanı hacklenmiş ve bu veritabanı uzunca bir süre torrent aracılığıyla elden ele dolaşmıştı. Uzunca bir süre bu olay gerek sosyal medya gerek teknoloji forumlarında konuşulmuş ve zamanla unutulmuştu. Ancak geçtiğimiz aylarda Microsoft’un Linkedin’i satın aldığını duyurması üzerine bu meşhur veritabanı tekrardan torrent paylaşımlarında boy göstermeye başladı. Bu ele geçirme ile birlikte yaklaşık olarak milyonlarca kullanıcının e-mail ve linkedin hesap bilgilerinin yanısıra parolaları da rahatlıkla erişilebilir bir formatta yine rahatlıkla erişilebilir noktalarda bulunuyor. Ortaya çıktığı dönemde Linkedin’e ait olduğu iddia edilen ve milyonlarca kullanıcının bilgisini içeren veritabanı dark web üzerinden 5 Bitcoin karşılığında satışa sunulmuştu.

![Linkedin DB İlanı]({{ site.baseurl }}/assets/img/post/linkedin-db-for-sale.png "Linkedin DB İlanı")

Ele geçirilen veritabanında Linkedin kullanıcılarının -en önemli olarak- e-mail ve parola bilgileri yer alıyordu. Parolalar şifrelenmemiş bir şekilde tutulmasa da, parolaların salt kullanılmadan ham bir şekilde SHA1 algoritması ile hashlenerek tutulduğu anlaşılınca parolaların %90’ı 72 saat içerisinde çözülmüştü.

**Not:** Hash algoritmaları şifreleme algoritmaları değildir. Kabaca tek yönlü şifreleme işlemlerinde pratikte yaygın olarak kullanılmaktadır. Veritabanında kullanıcı parolasının hash değeri tutuluyorsa bir şifreleme-çözümleme yapılmaz, sadece kullanıcının giriş yaptığı parolasının hash değeri karşılaştırılır.

Linkedin veritabanından elde edilen parolalar ile geçtiğimiz ay Mark Zuckerberg’in Twitter hesabıda aynı parolayı kullanması sonucu ele geçirilmişti. Eğer farklı servislerde aynı parolayı kullanıyorsanız, güvenliğiniz açısından parolalarınızı güncellemeniz hayati önem taşıyor. Özellikle geçmişte kullandığınız linkedin parolanızı hem linkedin hem de farklı hesaplarınız için kullanmaktan vazgeçmeli, kolay tahmin edilebilir parolalardan uzak durmalısınız.