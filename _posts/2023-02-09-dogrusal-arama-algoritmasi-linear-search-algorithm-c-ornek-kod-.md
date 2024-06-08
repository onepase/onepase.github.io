---
title: "Doğrusal Arama Algoritması (Linear Search Algorithm) - C Örnek Kod"
date: 2023-02-09T09:00:00+00:00
author: Hakan
layout: post
permalink: /dogrusal-arama-algoritmasi-linear-search-algorithm-c-ornek-kod/
categories: Genel
tags: [dogrusal arama algoritmasi, linear search algorithm, c örnek kod]
---
Doğrusal Arama Algoritması (Linear Search), bilgisayar bilimlerinde yaygın olarak kullanılan en basit arama algoritmalarından biridir ve küçük veri setlerinde etkili bir şekilde çalışır. Bu yazıda, Linear Search algoritmasının ne olduğunu, nasıl çalıştığını ve C programlama dilinde nasıl uygulanacağını öğreneceksiniz.

### Linear Search Algoritması Nedir?
Linear Search (Doğrusal Arama) algoritması, bir veri yapısında (genellikle bir dizi veya liste) belirli bir elemanı aramak için kullanılan temel bir arama algoritmasıdır. Linear Search, aranan elemanı bulmak için veri yapısının tüm elemanlarını sırayla kontrol eder. Eğer aranan eleman bulunursa, elemanın konumu (indeksi) döndürülür; aksi takdirde, aranan elemanın bulunamadığı belirtilir.

#### Algoritmanın Çalışma Prensibi

Linear Search algoritmasının çalışma prensibi oldukça basittir:

- 1. İlk elemandan başlayarak, her bir elemanı sırayla kontrol edilir.
- 2. Kontrol edilen eleman, aranan elemana eşitse, elemanın indeksi döndürülür.
- 3. Tüm elemanlar kontrol edildikten sonra, aranan eleman bulunamazsa, -1 veya "bulunamadı" gibi bir değer döndürülür.

#### Zaman Karmaşıklığı
Linear Search algoritmasının zaman karmaşıklığı O(n)'dir, burada n, veri yapısındaki eleman sayısını temsil eder. En kötü durumda, algoritma tüm elemanları kontrol etmek zorunda kalır, bu da O(n) zaman alır. Küçük veri setlerinde etkili olsa da, büyük veri setlerinde daha verimli arama algoritmaları tercih edilmelidir.

#### C ile Linear Search Uygulaması

Bu örnekte, linear_search fonksiyonu bir dizi (arr), dizinin boyutu (size) ve aranan eleman (target) alır. Fonksiyon, dizinin her bir elemanını kontrol eder ve aranan eleman bulunduğunda elemanın indeksini döndürür. Eğer aranan eleman dizide bulunamazsa, fonksiyon -1 döndürür.

{% highlight c %}

#include <stdio.h>

// Linear Search fonksiyonu
int linear_search(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i; // Aranan eleman bulundu, indeksini döndür
        }
    }
    return -1; // Aranan eleman bulunamadı
}

int main() {
    // Örnek bir dizi
    int arr[] = {10, 20, 30, 40, 50};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 30;

    // Linear Search algoritmasını kullanarak arama yapın
    int result = linear_search(arr, size, target);

    if (result != -1) {
        printf("Eleman bulundu: %d indeksinde %d\n", target, result);
    } else {
        printf("Eleman bulunamadı\n");
    }

    return 0;
}

{% endhighlight %}


##### Örnek: Kullanıcıdan Girdi Alma
Şimdi, kullanıcıdan bir dizi ve aranan elemanı alarak Linear Search algoritmasını uygulayan bir örnek yapalım.

Bu örnekte, kullanıcıdan bir dizi ve aranan elemanı girmesini istiyoruz. Kullanıcının girdiği dizi ve aranan eleman, linear_search fonksiyonuna iletilir ve sonuç ekranda gösterilir.

{% highlight c %}
#include <stdio.h>

// Linear Search fonksiyonu
int linear_search(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i; // Aranan eleman bulundu, indeksini döndür
        }
    }
    return -1; // Aranan eleman bulunamadı
}

int main() {
    int size, target;

    // Dizinin boyutunu al
    printf("Dizinin boyutunu girin: ");
    scanf("%d", &size);

    int arr[size];

    // Dizinin elemanlarını al
    printf("Dizinin elemanlarını girin:\n");
    for (int i = 0; i < size; i++) {
        scanf("%d", &arr[i]);
    }

    // Aranan elemanı al
    printf("Aranan elemanı girin: ");
    scanf("%d", &target);

    // Linear Search algoritmasını kullanarak arama yapın
    int result = linear_search(arr, size, target);

    if (result != -1) {
        printf("Eleman bulundu: %d indeksinde %d\n", target, result);
    } else {
        printf("Eleman bulunamadı\n");
    }

    return 0;
}
{% endhighlight %}

#### Linear Search Algoritmasının Avantajları ve Dezavantajları

##### Avantajları

- Basit ve Anlaşılır: Linear Search algoritması, kolay anlaşılır ve uygulanabilir bir algoritmadır.
- Küçük Veri Setlerinde Etkili: Küçük veri setlerinde hızlı ve etkili bir şekilde çalışır.
- Sıralama Gerektirmez: Veri yapısının sıralanmış olmasını gerektirmez.

##### Dezavantajları
- Büyük Veri Setlerinde Verimsiz: Büyük veri setlerinde, zaman karmaşıklığı nedeniyle yavaş olabilir.
- En Kötü Durum Performansı: En kötü durumda, tüm elemanları kontrol etmek zorunda kalır.

Linear Search algoritması, temel ve etkili bir arama algoritmasıdır. Linear Search, küçük veri setlerinde iyi performans gösterse de, büyük veri setlerinde daha verimli arama algoritmalarını örneğin, [Binary Search](https://hakan.io/ikili-arama-algoritmasi-binary-search-algorithm-c-ornek-kod/) kullanmak daha uygun olabilir.