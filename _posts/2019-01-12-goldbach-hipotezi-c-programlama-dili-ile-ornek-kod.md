---
title: 'Goldbach Hipotezi / Sanısı - C Programlama Dili İle Örnek Kod'
date: 2019-01-12T00:00:00+00:00
author: Hakan
layout: post
permalink: /goldbach-hipotezi-sanisi-c-programlama-dili-ile-ornek-kod/
categories: Genel
tags: [goldbach hipotezi, goldbach sanısı, asal sayılar, c programlama, c örnek]
img: goldbach.png
---
Goldbach hipotezi veya sanısı, 2'den büyük her çift tam sayının iki asal sayının toplamı şeklinde yazılabileceği iddiasıdır. İspatlanamamış en büyük matematik problemlerinden biridir. Orijinal Goldbach hipotezinde, Goldbach; 2'den büyük her tamsayının 3 asal sayının toplamı şeklinde ifade edilebileceğini iddia eder. 1 sayısının da asal sayı olduğu düşünülerek bu iddia ortaya atılmıştır. Sonrasında 1 asal sayı olarak kabul edilmediği için bu iddia geçerliliğini yitirmiştir. Goldbach hipotezi veya sanısı olarak ele aldığımız bu iddia, Euler'in "2'den büyük her çift tam sayı, iki asal sayının toplamından bulunabilir" şeklindeki düzeltmesini kapsamaktadır. 

Örnek olarak; 4,6,8,10,12 çift tam sayıları şu şekilde iki asal sayının toplamı şeklinde yazılabilir.

4 = 2 + 2
6 = 3 + 3
8 = 3 + 5
10 = 3 + 7
12 = 5 + 7

2'den büyük bir çift tam sayının, iki asal sayının toplamı şeklinde yazılmasının çözüm kümesinde en küçük asal sayıyı içeren ayrışımı bulabilecek örnek bir C kodu şu şekilde olacaktır.

Örnek C Kodu

{% highlight c %}
#include <stdio.h>

//Fonksyion deklarasyonları
int is_prime(int n);
void goldbach(int g);

int main(){
	int number = 0;
	while(1){
		printf("Enter even number:");
		scanf("%d",&number);
		if(number>2 && number%2==0){
			goldbach(number);
		}
		else{
			printf("Incorrect number!\n");
		}
		printf("\n");
	}
	return 0;
}


//Asal sayı kontrolu j < n/2, bir sayinin yarisindan buyuk tam boleni olamaz
int is_prime(int n){
	int flag = 1;
	for (int j = 2; j < n/2; j++)
	{
		if((n%j) == 0){
			return flag-1;
		}
	}
	return flag;
}


//Iki'den buyuk bir cift tam sayinin min goldbach cozumu
void goldbach(int g){
	int i = 2;

	for (int j = g-i; j > 2; j--)
	{
		if(is_prime(i) == 1 && is_prime(j) == 1)
		{
			printf("%d = %d + %d\n",g,i,j);
			break;
		}
		i++;
	}
}
{% endhighlight %}

2'den büyük bir çift tam sayının, iki farklı asal sayının toplamı şeklindeki tüm çözüm kümesini ekrana yazan örnek bir C kodu ise şu şekilde olacaktır.

{% highlight c %}
#include <stdio.h>

//Asal sayilar icin tampon
int primes[100000] = {2};
int j = 0;

//Fonksyion deklarasyonları
int is_prime(int n);
void goldbach(int g);

int main(){
	int number = 0;
	while(1){
		printf("Enter even number:");
		scanf("%d",&number);
		if(number>2 && number%2==0){
			goldbach(number);
		}
		else{
			printf("Incorrect number!\n");
		}
		printf("\n");
	}
	return 0;
}

//Asal sayı kontrolu j < n/2, bir sayinin yarisindan buyuk tam boleni olamaz
int is_prime(int n){
	int flag = 1;
	for (int j = 2; j < n/2; j++)
	{
		if((n%j) == 0){
			return flag-1;
		}
	}
	return flag;
}

//Iki'den buyuk cift tam sayinin iki asal sayi olarak toplamlarini ifade eden tam cozum kumesi
void goldbach(int g){
	int flag = 0;

	if(primes[j]<g){
		for (int i = primes[j]+1; i < g; i++)
		{
			if(is_prime(i) == 1){
				j++;
				primes[j] = i;
			}
		}		
	}

	for (int i = 0; i < j; i++)
	{
		for (int k = 0; k < j; k++)
		{
			if(primes[i] + primes[k] == g){
				printf("%d = %d + %d\n",g,primes[i],primes[k]);
				break;
			}
		}
	}

}
{% endhighlight %}