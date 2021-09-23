---
title: 'Memcached Kurulumu ve PHP Memcache Kullanımı'
date: 2018-08-20T00:22:16+00:00
author: Hakan
layout: post
permalink: /memcached-kurulumu-ve-php-memcache-kullanimi/
categories: Genel
tags: [memcached, php, memcache, kullanim, ornek]
img: memcached-logo.png
---

Yüksek trafiğe sahip web sunucular, özellikle CRUD işlemlerinin fazla olduğu web sunucular, yüksek trafik sonucunda çok fazla yük altına girecektir. Böyle bir durumda, kod kaynakları yeterince verimli kullanabilecek şekilde yazılmışsa, ağır yük altında hizmet verebilmek için ilk ihtiyaç duyulanlardan biri, bir önbellek mekanizmasıdır. 

Memcahced nedir?

Memcached 2003 yılında, alanının ilklerinden olan popüler blog servisi LiveJournal için yazılmış ve sonrasında özellikle web uygulamalarında çokça kullanılmaya başlanmış ücretiz, açık kaynak, yüksek performanslı ve dağıtık bir önbellekleme sistemidir. Basit ama güçlü bir önbellekleme sistemidir. Günümüzde Facebook tarafından aktif olarak kullanılmakta ve geliştirilmesine katkı sunulmaktadır. Yine popüler web uygulama ve servisleri tarafından (Wikipedia, Youtube, Flickr) aktif olarak kullanılmaktadır. 

Memcached bir in-memory storedur. Tüm önbellekleme hafıza(ram) üzerindedir. Dolayısıyla kritik verilerin yalnızca memcached üzerinde saklanmaması gerekir. Memcached üzerinde veri, key-value çiftleri olarak saklanır. Memcached özellikle veritabanı işlemlerinin fazla olduğu web uygulamalarında hayat kurtarıcıdır. 

Memcached Kurulum

Debian tabanlı Linux dağıtımlarında;

{% highlight bash %}
apt-get install php-memcached
apt-get install memcached
{% endhighlight %}

RedHat/Fedora tabanlı Linux dağıtımlarında; 

{% highlight bash %}
yum install php-memcached
yum install memcached
{% endhighlight %}

komutu ile Memcached ve Php-Memcached paketleri kolayca kurulabilir. Memcached TCP/IP tabanlıdır. Herhangi iki yazılım arasında memcached ile haberleşme sağlanabilir.

Memcached'i başlatmak için

{% highlight bash %}
memcached -d -m 512 -l 127.0.0.1 -p 11211 -u nobody
{% endhighlight %}

komutu kullanılabilir. Bu komut ile, 512 MB bir önbellek alanı kullanan, 11211 tcp ve udp portunu dinleyen bir memcached servisi başlatılacaktır. Memcached servisi başlatılırken oluşturulan önbellek alanı sabittir. İşletim sistemi mimarilerindeki bellek yönetimine benzer şekilde, eğer önbellek alanı dolduysa ilk yazılan verinin üzerine yazacaktır. Memcached için x86 sistemlerde maksimum 4GB önbellek alanı tanımlayabilirsiniz.

Memcached başlatıldıktan sonra servisle ilgili daha fazla detay almak için;

{% highlight bash %}
echo "stats settings" | nc localhost 11211
{% endhighlight %}

komutunu kullanabilirsiniz. Varsayılan olarak, Memcached key uzunlukları 250 karakterdir. Value ise maksimum 1MB olabilir. 

PHP Memcached Kullanımı

PHP ile memcached'e bağlanmak için;

{% highlight php %}
$memcache = new Memcache;
$memcache->connect('127.0.0.1', 11211) or die ("Memcached ile bağlantı kurulamıyor");
{% endhighlight %}

Memcached üzerine veri yazmak için;

{% highlight php %}
$exampleValue = 2;
$exampleValue = 'Example String';
$exampleValue = array('0','1','2','3');

$memcache->set('exampleKey', $exampleValue, false, 1800);
//Birinci parametre anahtar, ikinci parametre değer, üçüncü parametre memcached sıkıştırma true/false, dördüncü parametre saniye cinsinden önbellekleme süresi
{% endhighlight %}

Memcached üzerindeki bir anahtarın değerine ulaşmak için;

{% highlight php %}
$exampleValue = $memcache->get('exampleKey');
{% endhighlight %}

Örnek bir senaryoda, web uygulamamızdaki çok sık değişmeyen bir değer, veritabanında saklanıyor olsun. Sayfa her render edildiğinde veya her api çağrısında bu değerin veritabanından okunması gerekecektir. Biz memcached ile bu değeri her seferinde veritabanından okumak yerine önbellekte tutmak istiyor olalım. 

{% highlight php %}
//Veritabanı bağlantıları vs.

$memcache     = new Memcache;
$memcache->connect('127.0.0.1', 11211) or die ("Memcached ile bağlantı kurulamıyor");

$exampleValue = $memcache->get('exampleKey');

if($exampleValue === true){
	return $exampleValue;
}
else{
	$exampleValue = $db->get_var(sprintf("SELECT exampleValue FROM %s WHERE id = '%d'",'exampleTable',1));
	if($exampleValue){
		$memcache->set('exampleKey', $exampleValue, false, 1800);
		return $exampleValue;
	}
	else{
		return false;
	}
}
{% endhighlight %}

Bu sayede veritabanından dolayı oluşacak disk i/o işlemleri azalacak, doğrudan bellek üzerinden erişilerek performans artışı sağlanabilecektir. Memcached'in doğru implement edilmesi, memcached üzerinde önbelleklenecek verilerin doğru seçilmesi ve yarış durumu oluşturabilecek işlemlerin önceden tespit edilmesi ile web sunucularında oluşabilecek yük azaltılabilecektir.


