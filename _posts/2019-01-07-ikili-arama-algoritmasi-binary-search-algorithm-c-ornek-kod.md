---
title: 'İkili Arama Algoritması (Binary Search Algorithm) - C Örnek Kod'
date: 2019-01-09T00:00:00+00:00
author: Hakan
layout: post
permalink: /ikili-arama-algoritmasi-binary-search-algorithm-c-ornek-kod/
categories: Genel
tags: [ikili arama, ikili arama algoritması, binary search, binary search algorithm, ornek, c programı, c kod]
img: binary-search.jpg
---
İkili arama algoritması, bir dizide arama yapmaya yarayan bir arama algoritmasıdır. İkili arama algoritmasında, aranan elemanın bulunabilmesi için her seferinde dizinin ortasındaki elemana bakılır. Ortadaki eleman aranan elemana eşit değilse, aranan elemanın bulunduğu diğer yarı alanda arama işlemi tekrar edilir. Bu sayede her adımda arama uzayı yarıya indirilmiş olur. 

İkili arama algoritmasında arama yapılacak dizinin sıralı bir dizi olması gerekir. Sıralı olmayan dizilerde, ikili arama yapabilmek için öncelikle dizinin herhangi bir sıralama algoritması ile sıralanması gerekir.

İkili arama algoritmasında izlenecek adımlar şu şekildedir

1- Dizinin ortasındaki elemanı seç
2- Seçilen elemanı aranan elemanla karşılaştır, aranan elemana eşitse sonlandır
3- Aranan eleman seçilen elemandan büyükse dizinin seçilen elemandan büyük kısmında arama işlemini tekrarla
4- Aranan eleman seçilen elemandan küçükse dizinin seçilen elemandan küçük kısmında arama işlemini tekrarla
5- Arama uzayındaki en küçük indis en büyük indisten küçük veya eşit oluncaya kadar adımları tekrarla

Örnek olarak; 2,3,4,5,6,7,8,9,22,33,45 elemanlarından oluşan sıralı bir dizi içerisinde, 4 elemanının ikili arama ile bulunması için sırasıyla şu adımlar izlenecektir.


Dizinin ortadaki elemanı 7 olarak seçilir ve aranan elaman olan 4 ile karşılaştırılır. Aranan eleman (4) ortadaki elemana (7) eşit olmadığı için, dizinin ortasındaki elaman olan 7'den küçük olan kısmına bakılır. Yeni arama dizimiz : 2,3,4,5,6 olur.

Yeni arama dizimizin ortadaki elemanı 4 olacaktır ve arama işlemi tamamlanır.

İkili arama algoritmasında, sıralı bir dizide en fazla log2N karşılaştırma yapılarak sonuca ulaşılır.


İkili arama algoritmasını, örnekteki gibi sıralı bir dizide uygulamaya çalışırsak örnek bir C kodu aşağıdaki gibi olacaktır.


Örnek C Kodu

{% highlight c %}
#include <stdio.h>
int main()
{
	int array[11] = {2,3,4,5,6,7,8,9,22,33,45};
	int low       = 0;
	int high   	  = 10;
	int flag      = 0;
	int s         = 4;
	
	while(low <= high){
		int index = low+(high-low)/2;
		if(array[index] == s){
			flag = 1;
			printf("Founded: %d \n",index);
			break;
		}
		else if(array[index] < s){
			low   = index+1;
		}
		else{
			high = index-1;
		}
	}
	if(flag == 0){
		printf("Not Found!\n");
	}

	return 0;
}
{% endhighlight %}
