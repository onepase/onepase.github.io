---
title: 'Karışıklık Matrisi (Confusion Matrix)'
date: 2022-10-01T00:00:00+00:00
author: Hakan
layout: post
permalink: /karisiklik-matrisi-confusion-matrix/
categories: Genel
tags: [karışıklık matrisi, confusion matrix, makine öğrenmesi]
---

Karışıklık matrisi (Confusion Matrix) bir sınıflandırma problemindeki tahmin sonuçlarının özetini sunan tablodur. Karışıklık matrisi kullanılarak sınıflandırıcı ile yapılan hatalar hakkında fikir edinilebilir. Karışıklık matrisi aynı zamanda modelin yaptığı hata türleri hakkında da fikir verir. Karışıklık matrisi sınıflandırma problemlerinde, modelin performansını tanımlamak için literatürde sıklıkla kullanılmaktadır. İkili sınıflandırma (binary classification) modelleri için değerlendiricek olursak karışıklık matrisi aşağıdaki tablo gibi görünecektir.

|   |Pozitif Gerçek Durum|Negatif Gerçek Durum|
|---|---|---|
|Pozitif Tahmin|Gerçek Pozitif (TP)|Yanlış Pozitif(FP)|
|Negatif Tahmin|Yanlış Nefatif(FN)|Gerçek Negatif(TN)|


Tablo: Karışıklık Matrisi

Karışıklık matrisi üzerinde temsil edilen değerler aşağıdaki gibidir;

**Gerçek Pozitif (TP):** Gerçekte pozitif bir durumu ifade eden ve sınıflandırıcı tarafından pozitif olarak tahmin edilen örnekleri ifade eder.


**Gerçek Negatif (TN):** Gerçekte negatif bir durumu ifade eden ve sınıflandırıcı tarafından negatif olarak tahmin edilen örnekleri ifade eder.


**Yanlış Pozitif (FP):** Gerçekte negatif bir durumu ifade eden ve sınıflandırıcı tarafından pozitif olarak tahmin edilen örnekleri ifade eder.


**Yanlış Negatif (FN):** Gerçekte pozitif bir durumu ifade eden ve sınıflandırıcı tarafından negatif olarak tahmin edilen örnekleri ifade eder.

Karışıklık matrisleri kullanılarak hesaplanan bazı değerler sınıflandırıcı performansını değerlendirmek için kullanılmaktadır.

Toplam değeri denklem 1 ile hesaplanmaktadır.

Toplam = TP + FN + FP + FN (Denklem 1)

Gerçek pozitifler denklem 2 ile hesaplanmaktadır.

Gerçek Pozitifler = TP + FN (Denklem 2)

Gerçek Negatifler denklem 3 ile hesaplanmaktadır.

Gerçek Negatifler = TN + FP (Denklem 3)

**Doğruluk Oranı (Accuracy Rate)**

Doğruluk oranı sınıflandırıcı tarafından yapılan doğru tahmin sayısının tüm veri setindeki veri sayısına oranıdır. Doğruluk oranı ile sınıflandırıcının ne sıklıkla doğru bir tahminde bulunduğu ölçülmektedir. Doğruluk oranı 0 ile 1 arasında bir değere sahiptir. 0 en kötü oranı, 1 ise en iyi oranı ifade etmektedir. Doğruluk oranı denklem 4’de gösterildiği gibi hesaplanmaktadır.

**Doğruluk Oranı** = (TP + FN) / TOPLAM (Denklem 4)

**Hassasiyet (Precision)**

Hassasiyet tüm sınıflar içerisinden yapılan doğru pozitif tahminlerin, toplam pozitif tahminlere bölünmesiyle elde edilir. Hassasiyet ile doğru olarak ne kadar tahmin yapıldığı ölçülmektedir. Hassasiyet aynı zamanda pozitif tahmin edici değer olarak da isimlendirilmektedir. Hassasiyet denklem 5’da gösterildiği gibi hesaplanmaktadır.

**Hassasiyet** = TP / (TP + FP) (Denklem 5)
  
**Yaygınlık (Prevalence)**

Yaygınlık bir sınıflandırıcının tahminleme yaparken ne sıklıkla pozitif değer tahmin ettiğinin ölçüsüdür. Yaygınlık denklem 6’da gösterildiği gibi hesaplanmaktadır.

**Yaygınlık** = TP / TOPLAM (Denklem 6)


**Kesinlik (Recall)**

Kesinlik doğru pozitif tahmin sayısının, doğru pozitif tahmin sayısı ile doğru negatif tahmin sayısına bölünmesiyle hesaplanan bir ölçüdür. Kesinlik denklem 7’de gösterildiği şekilde hesaplanmaktadır.

**Kesinlik** = TP / (TP + TN) (Denklem 7)

**F Puanı (F Score)**

F puanı, gerçek pozitif değerlerin oranını ifade eden kesinlik(recall) ve hassasiyet(precision)’in harmonik ortalamasıdır. F puanı bir sınıflandırıcının gösterdiği performansın ne kadar iyi olduğunun bir ölçüsüdür. F puanı literatürde sınıflandırıcıların başarısını karşılaştırmak için sıklıkla kullanılmaktadır. F puanı denklem 8’de gösterildiği şekilde hesaplanmaktadır.

**F Puanı** = 2 * Hassasiyet * Kesinlik / Hassasiyet + Kesinlik (Denklem 8)
