---
title: 'Mükemmel Sayılar - C Programlama Dili İle Örnek Kodlar'
date: 2018-03-25T00:15:12+00:00
author: Hakan
layout: post
permalink: /mukemmel-sayilar-c-programlama-dili-ile-ornek-kodlar/
categories: Genel
tags: [mükemmel sayı, mükemmel sayılar, c ile mükemmel sayı, c programlama mükemmel sayılar, mükemmel sayılar örnek kod, mükemmel sayı fonksiyon]
img: numbers.jpg
mathjax: true
---

Mükemmel sayılar, kendisi hariç pozitif tam bölenlerinin toplamına eşit olan sayılardır. En küçük mükemmel sayı 6'dır.

6'nın pozitif tam bölenleri: 1,2,3 ve 6 kendisi hariç tam bölenlerinin toplamı: 1+2+3 = 6'dır ve 6 bir mükemmel sayıdır.

Yine aynı şekilde 28'in pozitif tam bölenleri: 1,2,4,7,14,28 kendisi hariç tam bölenlerinin toplamı: 1+2+4+7+14 = 28'dir ve 28 bir mükemmel sayıdır.

Yeterince büyük bir sayının tam bölenlerinin tespit edilmesi için gereken zaman miktarı, bilgisayarın işlem gücüyle orantılı olacak şekilde değişecektir. Esasında tam bölenlerin bulunması için yapılacak işlem 1'den n'e kadar tüm tamsayıların n'in bir tam böleni olup olmadığının kontrolünden ibarettir. Mükemmel sayıları matematiksel olarak ifade etmek mümkündür. Öklid yaptığı çalışmalar neticesinde ilk dört asal sayı için bir formül keşfetmiştir. Sonrasında ise formülün -şimdiye kadar- hesaplanabilen tüm mükemmel sayılar için geçerli olduğu ispat edilmiştir. Daha doğru bir ifadeyle formülün geçersiz olduğu bir mükemmel sayı henüz keşfedilmemiştir. 

Mükemmel sayılar için keşfedilen formül p ve $$2^p-1$$ sayıları asal sayı olmak koşuluyla şöyledir:

$$2^{p-1}(2^p-1)$$

p=2 için $$2^1(2^2-1) = 6$$

p=3 için $$2^2(2^3-1) = 28$$

p=5 için $$2^4(2^5-1) = 496$$

Mükemmel sayılarla ilgili diğer bir formül ise, mükemmel bir sayının 1 hariç tüm pozitif tam bölenlerinin tersinin toplamı 1'e eşittir. 

6 için 1/2 + 1/3 + 1/6 = 1

28 için 1/2 + 1/4 + 1/7 + 1/14 + 1/28 = 1 olacaktır.

Şimdiye kadar hesaplanabilen tüm mükemmel sayılar çifttir. Henüz keşfedilmiş tek mükemmel sayı yok. İlk on mükemmel sayı ise şöyledir;

6

28

496

8128

33550336

8589869056

137438691328

2305843008139952128

2658455991569831744654692615953842176

191561942608236107294793378084303638130997321548169216

Mükemmel sayıların bulunması için C programlama dilinde yaklaşımımız, sayının tüm pozitif tam bölenlerini hesaplamak ve toplamak yönünde olacak. Dolayısıyla ilk 4 mükemmel sayı hızlı bir şekilde bulunabilse de, sonraki mükemmel sayılar için iterasyon bir hayli artacağı için hesaplama süresi de bir o kadar artacaktır. Geleneksel yöntemin haricinde her tam bölen bulunduktan sonra, sonraki bölenlerin bulunması sürecinde tekrar hesaplamak yerine işaretleyerek, algoritmayı geliştirmek ve işlem süresini kısaltmak mümkün. 

Mükemmel sayıların bulunması için örnek bir C programı şöyle;

{% highlight c %}
#include <stdio.h>

int main(){
	//1'den 10000'e kadar olan mukemmel 
	//sayilari bulmaya calisiyoruz
	for (int i=1; i <10000 ; i++) {
		//Her sayi icin pozitif tam bolenlerini 
		//bularak kendisi haric toplamini hesapliyoruz
		int sum = 0;
		for(int j=1; j<i; j++){
			if(i%j==0){
				sum = sum + j;
			}
		}
		//Kendisi haric pozitif tam bolenlerinin 
		//toplami kendisine esit mi diye kontrol ediyoruz
		if(sum == i){
			printf("%d\n",i );
		}
	}	
	return 0;
}
{% endhighlight %}

Herhangi bir sayının mükemmel sayı olup olmadığını kontrol eden örnek bir C programı ise şöyle olacaktır;

{% highlight c %}
#include <stdio.h>
int main(){
	int sayi;
	printf("Sayi? \n");
	scanf("%d",&sayi);
	int sum = 0;
	for(int j=1; j<sayi; j++){
		if(sayi%j==0){
			sum = sum + j;
		}
	}
	if(sum == sayi){
		printf("%d bir mukemmel sayidir\n",sayi );
	}
	else{
		printf("%d bir mukemmel sayi degildir\n",sayi );
	}

	return 0;
}
{% endhighlight %}
