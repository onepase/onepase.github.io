---
id: 41
title: 'TinyMCE Kullanılan Textarea&#8217;ya Ekleme Yapma'
date: 2012-02-29T03:34:37+00:00
author: Hakan
layout: post
permalink: /tinymce-kullanilan-textareaya-ekleme-yapma/
categories:
  - Javascript
---
TinyMCE kullanışlı bir editör. Web uygulamalarında içeriklerin tekrar elden geçirilmesi hususunu bir nebze olsun hafifleten bir editör. Gel gelelim TinyMCE kullanılan bir alanda manipülasyon yapılması gerektiğinde farklı bir yöntem kullanılması gerektiğinden bihaber yazılımcının canını biraz sıkar.

Hemen konuya geçelim;

Mesela web uygulamamızın panel kısmından haber ekleme modülünde TinyMCE kullandık ve kullanıcı bu alana butonlar aracılığıyla eklemeler yapmak istedi. Örneğin kullanıcı editörü kullanırken yazı içine resim eklemek istedi. Önce yazının o anki hali tutulacak, her resim ekleme işleminde bu işlem tekrarlanacak ve iş anlamsızlaşacak. Kullanıcı her bir eklemede bir önceki veriyi kısmen kaybedecek. Bu noktada  jquery maalesef pek işe yaramıyor. Şöyle ki;

&nbsp;

- Şu anki içeriği önbellekle
- Eklenen resmi içerikle birlikte bas
  
ile ekleme yapmaya çalıştığınızda ne yazık ki her eklemede bir önceki veriyi kaybediyoruz. Bu noktada TinyMCE imdadımıza koşuyor ve

{% highlight javascript %}
tinyMCE.execCommand(&#039;mceInsertContent&#039;, false, &#039;&lt;img witdh="100%" src="http://www.mysite.com/myImage.jpg"  /&gt;&#039;);
{% endhighlight %}

tinyMCE.execCommand vasıtası ile yazı içerisine rahatlılla ekleme yapabiliyoruz. Pek tabi resim ekleme dışında her hangi bir içerik eklemek bu yolla mümkün. Bu kullanımı TinyMCE&#8217;ye bir image uploader yazarken kullanmak zorunda kaldım. Maalesef TinyMCE image upload eklentisini ücretsiz olarak dağıtmıyor ve bu noktada kendi çözümünüzü üretmeniz ya da ücreti karşılığında almanız gerek.
  
Bu arada yazı başlığı biraz garip oldu galiba. Saat sabah 05:30 idare edelim  <img src="http://www.eksihayaller.com/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />