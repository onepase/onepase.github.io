---
title: "ANNOY Kütüphanesi İle Yaklaşık En Yakın Komşu Arama"
date: 2023-02-06T09:00:00+00:00
author: Hakan
layout: post
permalink: /annoy-kutuphanesi-ile-yaklasik-en-yakin-komsu-arama/
categories: Genel
tags: [annoy, yaklaşık en yakın komşu arama]
---
ANNOY, büyük veri setlerinde hızlı ve verimli bir şekilde en yakın komşu arama işlemi gerçekleştirmek için geliştirilmiş bir kütüphanedir. Bu yazıda, ANNOY'un ne olduğunu, neden kullanıldığını ve uygulamalı bir örnekle nasıl kullanılabileceğini ele alacağız.

## ANNOY Nedir?

ANNOY (Approximate Nearest Neighbors Oh Yeah), Spotify tarafından geliştirilmiş ve büyük veri setlerinde hızlı ve verimli en yakın komşu aramayı sağlayan bir kütüphanedir. ANNOY, özellikle yüksek boyutlu veri setlerinde benzer vektörleri bulmak için kullanılır. "Approximate" ifadesi, kütüphanenin kesin sonuçlar yerine yaklaşık sonuçlar sunduğunu belirtir, bu da arama işlemlerinin çok daha hızlı olmasını sağlar.

## ANNOY'un Temel Özellikleri
- Hız ve Verimlilik: ANNOY, büyük veri setlerinde ve yüksek boyutlu vektörlerde hızlı arama yapabilir.
- Yaklaşık Sonuçlar: Kesin sonuçlar yerine yaklaşık sonuçlar sunarak arama süresini azaltır.
- Düşük Bellek Kullanımı: Bellek dostu yapısı sayesinde büyük veri setlerini bellekte verimli bir şekilde tutar.
- Kolay Kullanım: Basit ve anlaşılır bir API sunar, bu da veri bilimciler ve mühendisler için kullanımını kolaylaştırır.

## ANNOY'un Kullanım Alanları
ANNOY, çeşitli alanlarda kullanılabilir. Bazı yaygın kullanım alanları aşağıdaki gibidir:

- Öneri Sistemleri: Kullanıcılara benzer ürünler veya içerikler önermek için.
- Veri Keşfi: Büyük veri setlerinde benzer veri noktalarını keşfetmek için.
- Görüntü ve Ses Tanıma: Görseller veya sesler arasında benzer olanları bulmak için.
- Doğal Dil İşleme: Kelime veya cümle vektörleri arasında en yakın olanları bulmak için.

## ANNOY ile Uygulamalı Örnek: Film Öneri Sistemi
ANNOY'un nasıl çalıştığını anlamak için bir film öneri sistemi oluşturalım. Bu örnekte, IMDb veri setini kullanarak benzer filmleri bulan bir script geliştireceğiz. Örnek veri setinde her bir film 2 boyutlu bir vektörle ifade edilmekte ve filmler arasındaki benzerliği vektörlerin birbirine olan uzaklığını ANNOY hesaplayarak bulacak. ANNOY'un tam olarak yaptığı şey zaten bu olduğu için, örneğimizde 2 boyutlu vektörler arasında elbette çok hızlı arama yapacaktır. Ancak özelliklerin çok daha yüksek boyutlu vektörlerle ifade edildiği durumlarda bile ANNOY hızlı bir şekilde arama yapabilmektedir.

ANNOY mesafe ölçümü için 5 farklı metrik kullanabilmektedir. Mesafe metrikleri ayrı bir yazının konusu olacağı için ANNOY'da ölçüm için kullanılabilecek metrikler; Öklid Mesafesi, Manhattan Mesafesi, Kosinüs Benzerliği, Hamming Mesafesi ve Nokta Çarpımdır.

Annoy indexi oluşturulurken "angular", "euclidean", "manhattan", "hamming" veya "dot" parametrelerini kullanabilirsiniz. Aşağıdaki örnekte index öklid mesafesi kullanılarak oluşturulmuştur.

### Gerekli Kütüphaneleri Yükleme
İlk olarak, gerekli kütüphaneleri yükleyelim:
{% highlight bash %}
pip install annoy
pip install annoy pandas
{% endhighlight %} 

### Veri Hazırlığı
Film veri setimizi yükleyip ön işleme tabi tutalım:

{% highlight bash %}
import pandas as pd
from annoy import AnnoyIndex

# Örnek film veri seti
data = {
    'id': [0, 1, 2, 3, 4],
    'title': ['Movie1', 'Movie2', 'Movie3', 'Movie4', 'Movie5'],
    'features': [[0.1, 0.3], [0.2, 0.6], [0.4, 0.1], [0.6, 0.7], [0.9, 0.2]]
}

movies = pd.DataFrame(data)

# Özellikleri ve film id'lerini hazırlıyoruz
features = movies['features'].tolist()
movie_ids = movies['id'].tolist()

{% endhighlight %} 

### ANNOY Modeli Oluşturma ve Eğitme
ANNOY modelimizi oluşturup, veri setimizle eğitelim:

{% highlight bash %}
# Vektör boyutu (örnek veri setinde 2)
vector_length = 2

# ANNOY index oluşturma
annoy_index = AnnoyIndex(vector_length, 'euclidean')

# Veri setindeki filmleri ekliyoruz
for i, feature in enumerate(features):
    annoy_index.add_item(movie_ids[i], feature)

# Index'i inşa ediyoruz
annoy_index.build(10)  # 10 ağaç kullanarak

{% endhighlight %} 

### Benzer Filmleri Bulma
Şimdi, belirli bir film için benzer filmleri bulalım:

{% highlight bash %}
# Belirli bir film id'si için en yakın komşuları buluyoruz
movie_id = 0  # İlk film
num_neighbors = 3  # 3 benzer film bul

similar_movies = annoy_index.get_nns_by_item(movie_id, num_neighbors)
print(f'Film {movie_id} için benzer filmler: {similar_movies}')
{% endhighlight %} 

### Sonuçları Görüntüleme
Benzer filmleri daha okunabilir hale getirelim:

{% highlight bash %}
# Benzer film isimlerini görüntüleme
similar_movie_titles = movies[movies['id'].isin(similar_movies)]['title'].tolist()
print(f'Film {movie_id} için benzer filmler: {similar_movie_titles}')
{% endhighlight %} 

Bu örnekle, ANNOY kütüphanesini kullanarak hızlı ve verimli bir şekilde benzer film önerileri yapabileceğinizi uygulamalı olarak gösteren bir script geliştirmiş olduk. Bu basit uygulamayı daha büyük veri setleri ve daha karmaşık öneri sistemleriyle genişletebilirsiniz.

Sonuç olarak ANNOY kütüphanesi, büyük veri setlerinde hızlı ve etkili en yakın komşu arama yapmayı sağlayan güçlü bir araçtır. Bu gönderide, ANNOY'un temel özelliklerini ve nasıl kullanılacağına dair temel adımları gördünüz. Ayrıca, basit bir film öneri sistemi örneği ile ANNOY'un gerçek dünyada nasıl uygulanabileceğini görmüş oldunuz. ANNOY, özellikle öneri sistemleri, veri keşfi ve benzer veri noktalarını bulma gibi alanlarda oldukça kullanışlıdır.