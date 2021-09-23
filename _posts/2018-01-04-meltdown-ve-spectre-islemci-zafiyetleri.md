---
title: "Meltdown ve Spectre İşlemci Zafiyetleri"
date: 2018-01-04T00:00:00+00:00
author: Hakan
layout: post
permalink: /meltdown-ve-spectre-islemci-zafiyetleri/
categories: Genel
tags: [meltdown, spectre, zafiyet, işlemci zafiyet]
img: post/meltdown-spectre.jpg
---
Yeni yılın ilk günleri ile birlikte çok büyük ölçekteki iki güvenlik açığı duyuruldu. Neredeyse şu anda kullanımda olan tüm bilgisayarları, akıllı telefonları, tablet bilgisayarları ve sunucuları etkileyen güvenlik açığı ile parolalarınınız ve hassas verileriniz tehlike altında.

Google Project Zero ekibi tarafından keşfedilen ve duyurulan güvenlik açığı tüm işlemcileri (Intel, AMD, ARM) ve tüm cihazları etkiliyor. Donanım düzeyindeki bu zafiyet iki saldırı olarak kategorilendi. Meltdown ve Spectre.

İki saldırı da modern işlemcilerin performansı artırmak için kullandığı yöntemleri kendi lehine kullanıyor.

**Meltdown**

İlk olarak Meltdown atağı ile saldırgan, hedef makinanın tüm fiziksel hafızasını okuyabiliyor. Bu da diğer programlar ve işletim sistemi tarafından kullanılan tüm hassas verilerin ve parolaların okunabileceği anlamına geliyor.

Meltdown, kullanıcı uygulamaları ve işletim sistemi arasındaki izolasyonu kırmak için spekülatif çalıştırma özelliğini kullanıyor ve herhangi bir uygulamanın çekirdek için ayrılan bellek de dahil olmak üzere tüm sistem belleğine erişmesine izin veriyor.

Meltdown, Intel işlemcilere özgü bir ayrıcalık yükseltme açığından faydalanıyor. Bu da bellek korumasının aşılmasına neden oluyor.

Güvenlik açığının tüm işlemcileri etkilemesinin sebebi çok temel düzeyde bir problem olması. İşletim sistemi mimarilerinde işletim sistemi çekirdeği ile kullanıcı programları bellek üzerinde bir arada bulunur. Bu da böyle bir güvenlik açığına sebep oluyor. Bu durumu önlemenin yolu işletim sistemi çekirdeği ile kullanıcı programlarını farklı page tablelar üzerinde tutmak, kısaca işletim sistemi çekirdeğini ve kullanıcı programlarını izole etmek. Sorunun çözümü basit fakat her sistem çağrısında page tableların yeniden yüklenmesi gerekiyor ve yama sonuç olarak, yapılan testlere göre %5 – %30 arasında bir performans kaybına sebep olacak.

**Spectre**

İkinci olarak iste Spectre atağı ile saldırgan tarafından geliştirilen bir program, sistemde çalışırken diğer programların kendi belleklerinin rastgele bölümlerine erişmesine izin vererek veri sızıntısına yol açıyor ve bir yan kanaldan veriyi okuyabiliyor.

Spectre ile meydana gelen güvenlik açığını yamamak pek kolay görünmüyor. Bu zafiyetin tamamen ortadan kaldırılması için işlemci mimarilerinde köklü değişiklikler yapılması gerekmekte ve bu uzun bir süreç anlamına geliyor.

Zafiyet Intel, AMD, ARM işlemcilerini kullanan masaüstü ve taşınabilir bilgisayarlar, sunucular, akıllı telefonlar dahil tüm sistemleri etkiliyor. Öte yandan internet tarayıcıları tarafında Javascript ile zafiyetten faydalanılması mümkün ve bu durum tüm internet kullanıcılarının hassas verilerinin ve parolalarının güvende olmadığı anlamına geliyor.

Google Project Zero ekibi tarafından keşfedilen ve duyurulan güvenlik açıkları zero day kapsamında çoğu işlemci üreticisi ve işletim sistemi tarafından ciddiyetle karşılandı ve duyurulmadan önce gerekli yamalar hazırlandı.

Nasıl Önlem Alınır?

Kimler etkilendi? – Kısaca herkes!

**Windows :** Microsoft Windows 10 için bir yama yayınladı. Diğer Windows sürümleri için 9 Ocak’ta bir yama yayınlanacak.

**MacOS :** Apple bu güvenlik açıklarının büyük bir kısmını geçen ay yayınlanan High Sierra 10.13.2’de düzeltmişti. High Sierra 10.13.3 sürüm güncellemesi ile eksik kalan kısımları da yamayacak.

**Linux :**  Linux çekirdekleri için, çekirdeği tamamen ayrı bir adres alanına taşıyacak olan kernel page table isolation (KPTI) içeren yamaları yayınlandı.

**Android :**  Google Pixel ve Nexus kullanıcıları için güvenlik yamalarını içeren güncelleme yayınladı. Diğer marka model cihaz kullanıcıları ise üreticilerinin bir güvenlik yaması yayınlamasını beklemek zorunda.