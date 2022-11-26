---
title: "Karar Ağacı (Decision Tree)"
date: 2022-11-25T09:00:00+00:00
author: Hakan
layout: post
permalink: /karar-agaci-decision-tree/
categories: Genel
tags: [karar ağacı]
---

Karar ağacı, belirli koşullar altında bir karara varılmasını sağlayan ve olası çözüm kümesinin ağaç üzerinde grafiksel gösterimini sağlayan bir yöntemdir. Karar ağaçları işletmelerde yaygın bir şekilde yönetimlerin alacağı tercihlerin, risklerin ve belirlemek istediği hedeflerin tanımlanmasında kullanılmaktadır. Aynı zamanda makine öğrenmesi sınıflandırma problemlerinde kullanılan bir yöntemdir. Karar ağaçları, bir ağaç veri yapısı üzerinde sınıflandırma ve regresyon modelleri oluşturmakta kullanılmaktadır.

Karar ağaçları, bir dizi basit testi mantıksal olarak birleştiren sıralı modellerdir; her test sayısal bir özniteliği bir eşik değeriyle veya bir nominal özniteliği bir dizi olası değerle karşılaştırır. Bu tür sembolik sınıflandırıcılar, sinir ağları gibi “kara kutu” modellerine göre anlaşılabilirlik açısından bir avantaja sahiptir. Bir karar ağacının izlediği mantıksal kuralların yorumlanması, bir sinir ağındaki düğümler arasındaki bağlantıların sayısal ağırlıklarından çok daha kolaydır. Karar vericiler, anlayabilecekleri modelleri kullanma konusunda kendilerini daha rahat hissetme eğilimindedir [1]. 

Karar ağaçları ile sınıflandırma yapılırken, bir veri kümesi giderek daha küçük alt kümelere ayrılarak karar ağacı kademeli olarak geliştirilir. Sonuç olarak elde edilen ağaç, karar düğümleri ve yaprak düğümlerinden oluşan bir karar ağacıdır. Oluşturulan karar ağacında bir karar düğümünün iki veya daha fazla sayıda elemanı vardır. Yaprak düğümler ise bir sınıfı veya kararı temsil eder. Karar ağacı ile sınıflandırma yapılırken, veri setinden elde edilen karar ağacının olabildiğince az sayıda düğümden oluşturulması hedeflenmektedir.


![Örnek bir karar ağacı]({{ site.baseurl }}/assets/images/post/karar-agaci.jpg "The IT Crowd")*Örnek Bir Karar Ağacı*

Karar ağacının oluşturulması için Quinlan tarafından ID3 olarak adlandırılan bir algoritma geliştirilmiştir. ID3 algoritması, karar ağacını oluşturmak için yukarıdan aşağıya, bir geri izleme olmadan açgözlü arama yaparak çalışır. ID3 algoritması ile karar ağacı oluşturulurken Entropi ve Bilgi Kazancı kullanılmaktadır [2].

Bir karar ağacı kök düğümden başlayarak yukarıdan aşağıya doğru oluşturulur. Karar ağacı oluşturulurken verilerin homojen bir şekilde dağılması hedeflenmektedir. ID3 algoritması homojenliği hesaplamak için entropiyi kullanır. Bir karar ağacı oluşturulurken öncelikli olarak veri setinden faydalanarak sıklık tabloları oluşturulur. Özelliklerin seçimi için sıklık tabloları kullanılarak iki tür entropi hesaplanır. Bir özellik için entropi hesabı denklem 1’de gösterildiği şekilde hesaplanmaktadır. İki özellik için entropi hesabı denklem 2’de gösterildiği şekilde hesaplanmaktadır.

![Denklem 1]({{ site.baseurl }}/assets/images/post/other/karar-agaci-denklem-1.png "Denklem 1")*Denklem 1*

|Yürüyüşe Çık|Yürüyüşe Çık|
|---|---|
|Evet|Hayır|
|9|5|
Tablo: Tek Özellik İçin Entropi Örneği

Entropi(YuruyuseCik) = Entropy(5,9) = Entropy(0.36,0.64) = 0.94


![Denklem 2]({{ site.baseurl }}/assets/images/post/other/karar-agaci-denklem-2.png "Denklem 2")*Denklem 2*


|Tahmin|Hava Durumu|Yürüyüşe Çık|Yürüyüşe Çık||
|---|---|---|---|---|
|||Evet|Hayır||
||Güneşli|3|2|5|
||Bulutlu|4|0|4|
||Yağmurlu|2|3|5|
|||||14|
Tablo: Tek Özellik İçin Entropi Örneği


E(YuruyuseCik, Tahmin) = P(Güneşli) * E(3,2) + P(Bulutlu) * E(4,0) + P(Yağmurlu) * E(2,3) = 0.693


Bilgi kazancı ise, bir veri kümesinin özniteliklerinin belirlenmesinden sonra entropideki azalmaya dayanır. Bir karar ağacı oluşturulurken hedeflenen amaç, en homojen şekilde yani en yüksek bilgi kazancını döndüren özniteliği bulmaktır. Bilgi kazancı hesaplanırken önce hedefin entropisi hesaplanır. Veri kümesi daha sonra farklı özniteliklere bölünür. Her bir dal için entropi hesaplanır. Daha sonra her bir dala ait toplam entropiyi hesaplamak için orantılı olarak eklenir. Hesaplanan entropi, veri setinin bölünmeden önceki entropisinden çıkarılarak bilgi kazancı elde edilir. Karar ağacında yer alacak karar düğümlerinin belirlenmesi için en büyük bilgi kazancına sahip olan öznitelik seçilerek veri seti dallara ayrılır. Her dal için aynı işlemler tekrarlanarak karar ağacı oluşturulur.

ID3 algoritması ile karar ağacı oluşturulurken entropisi 0 olarak hesaplanan dal bir yaprak düğüm olarak belirlenir. Entropisi 0’dan büyük olan dallar ise daha alt dallara bölünmelidir. ID3 algoritması tüm verilerin sınıflandırması yapılana kadar, yaprağa sahip olmayan dallarda recursive olarak çalıştırılır.

Karar ağaçları ile sınıflandırma yapılırken eğitilen modelin, eğitim için kullanılan veri seti üzerinde aşırı öğrenme göstermesi durumunda ağaç üzerinde budama işlemi gerçekleştirilir. Bir karar ağacının budanmasına yönelik genellikle iki yöntem tercih edilmektedir. Pre-pruning olarak adlandırılan yöntemle, bir karar ağacı oluşturulurken ağaçta olması istenmeyen düğümler temizlenir. Post-pruning olarak adlandırılan yöntemle ise öncelikli olarak karar ağacı oluşturulur ve sonrasında karar ağacında yer alan gereksiz kısımlar temizlenir. Budama işleminin ağaç oluşturulurken yapılması durumunda, budama işleminin yapılacağı koşulların  belirlenmesinde yaşanacak olan zorluklar sebebiyle genellikle ağaç oluşturulduktan sonra budama işlemi yapılması tercih edilmektedir. 

Sınıflandırma problemlerinde bir karar ağacı oluşturulurken öznitelik seçimi için bilgi kazancının yanında, kazanç oranı (gain ratio) ve gini index yöntemleri de ayrıca kullanılmaktadır. Bu gönderide kısaca karar ağaçlarından ve ağacın oluşturulması süresince uygulanan yöntemlerden bahsedilmiştir.


[1] Kotsiantis, S. B. (2013). Decision trees: a recent overview. Artificial Intelligence Review, 39(4), 261-283.

[2] Quinlan, J. R. (1986). Induction of decision trees. Machine learning, 1(1), 81-106.