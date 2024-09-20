# Yapay Sinir Ağları Kullanarak El Yazısı ile Yazılmış Sayıların Tanınması

## Proje Genel Bakış

Bu proje, yapay sinir ağları (ANN) kullanarak el yazısı ile yazılmış sayıları tanıma üzerine odaklanmaktadır. Proje, yaygın olarak bilinen MNIST veri setinden el yazısı rakamların (0'dan 9'a kadar) yüksek doğruluk oranıyla sınıflandırılmasını amaçlar. Proje, veri ön işleme, model oluşturma, modelin eğitilmesi, değerlendirilmesi ve son olarak görülmemiş veriler üzerinde tahminler yapılması sürecini kapsar.

## Veri Seti

Bu projede kullanılan veri seti, 60.000 eğitim ve 10.000 test görüntüsünden oluşan MNIST veri setidir. Her bir görüntü, 0'dan 9'a kadar olan el yazısı rakamları temsil eden 28x28 piksel gri tonlamalı bir görüntüdür. MNIST veri seti, makine öğrenimi alanında bir kıyaslama veri seti olarak kabul edilir ve yeni modelleri ve algoritmaları test etmek için sıklıkla kullanılır.

## Proje Yapısı

- **Veri Ön İşleme:** 
  - MNIST veri setinden elde edilen görüntüler, ANN modeline hazırlık için yeniden şekillendirilir ve normalize edilir.
  - Yeniden şekillendirme, her bir görüntünün 784 elemanlı (28x28) bir diziye dönüştürülmesini sağlar.
  - Normalizasyon, piksel değerlerini 0 ile 1 arasında ölçeklendirerek eğitim sürecinin hızlanmasına yardımcı olur.
  
- **Model Mimarisi:**
  - Model, birkaç katmandan oluşan bir ardışık sinir ağıdır:
    - **Girdi Katmanı:** Girdi katmanı, 784 boyutlu girdi vektörünü kabul eder.
    - **Gizli Katmanlar:** ReLU aktivasyon fonksiyonları ile kullanılan iki yoğun (tam bağlı) katman, modele doğrusal olmayanlık kazandırır.
    - **Çıkış Katmanı:** Son yoğun katman, 10 nörona sahiptir ve softmax aktivasyon fonksiyonu ile her sınıf için olasılık değerlerini verir.

- **Model Eğitimi:**
  - Model, çok sınıflı sınıflandırma görevleri için yaygın olarak tercih edilen kategorik çapraz entropi (categorical cross-entropy) kayıp fonksiyonu kullanılarak eğitilir.
  - Adam optimizasyon algoritması, eğitim sürecinde kayıp fonksiyonunu minimize etmek için kullanılır.
  - Eğitim, birkaç dönem boyunca (epoch) gerçekleştirilir ve hem eğitim hem de doğrulama doğruluğu ve kaybı izlenir.

- **Değerlendirme:**
  - Eğitimden sonra, model test veri seti üzerinde değerlendirilir.
  - Doğruluk, kayıp, kesinlik ve geri çağırma gibi önemli metrikler, modelin performansını değerlendirmek için hesaplanır.
  
- **Tahminler:**
  - Eğitilen model, bireysel el yazısı rakam görüntüleri üzerinde tahminlerde bulunur.
  - Tahmin edilen sınıf ve her rakam için ilgili olasılık değeri gösterilir, ayrıca diğer sınıflar için olasılıklar da sunulur, bu da modelin güveni hakkında fikir verir.

## Sonuçlar

Model, test veri setinde yaklaşık %98 doğruluk oranına ulaşarak el yazısı rakamları tanımadaki etkinliğini göstermektedir. Karışıklık matrisi ve diğer değerlendirme metrikleri, modelin çoğu rakamda oldukça başarılı olduğunu, ancak bazı durumlarda (örneğin, şekil benzerliği nedeniyle 3 ile 8'i karıştırma) hafif yanlış sınıflandırmaların olabileceğini göstermektedir.


## Sonuç

Bu proje, derin öğrenmenin, özellikle de yapay sinir ağlarının gerçek dünya sınıflandırma sorunlarını çözmedeki gücünü göstermektedir. El yazısı rakamlarının başarılı bir şekilde tanınması, yapay sinir ağlarının görüntü tanıma, doğal dil işleme gibi çeşitli alanlarda nasıl uygulanabileceğine dair bir örnektir. Bu proje, makine öğrenimi alanında daha ileri düzeyde araştırma ve denemeler için sağlam bir temel sunar.
