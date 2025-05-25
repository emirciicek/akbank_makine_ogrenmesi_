# 🏥 No-Show Prediction with Machine Learning

Bu projede, Brezilya’daki hasta randevularına ait geniş bir veri setini kullanarak, hastaların randevu günlerinde **hastaneye gelip gelmeyeceklerini tahmin etmeye** çalıştım. Böylece sağlık kurumlarının hem kaynaklarını daha verimli kullanmasını, hem de hasta hatırlatma süreçlerini geliştirmesini hedefledim.

---

## 📊 Problem Tanımı
Randevuya gitmeme yani “No-show” problemi, hastaneler için büyük bir sorun. Çünkü boş kalan randevular, hem kaynak israfına hem de diğer hastaların hizmet almasının gecikmesine yol açıyor. Bu yüzden hastaların gelme ihtimallerini önceden tahmin etmek, sağlık sistemlerinin işleyişini daha etkin hale getirebilir.

---

## 📁 Veri Seti
Veri seti oldukça geniş ve zengin; 110.000’den fazla randevu kaydı içeriyor. İçinde yaş, cinsiyet, hastanın mahallesi, randevu tarihi ve hastaya gönderilen SMS bildirim gibi pek çok bilgi var. Bu değişkenler üzerinden, hastaların gerçekten randevuya gelip gelmediği bilgisi hedef olarak belirlenmiş.

---

## 🔎 Uygulanan Adımlar

### 📌 Keşifsel Veri Analizi (EDA)

Öncelikle veriyi anlamaya çalıştım. Yaş gruplarının, cinsiyetin veya SMS bildiriminin randevuya gelme oranını nasıl etkilediğini grafiklerle gösterdim. Örneğin, gençlerin daha mı çok “No-show” yaptığı, SMS hatırlatmalarının işe yarayıp yaramadığı gibi sorulara yanıt aradım.

### 🧼 Veri Ön İşleme

Randevu günü ile kayıt gününün farkını gösteren yeni bir değişken (`DaysDiff`) oluşturdum. Kategorik verileri makine öğrenmesi modellerine uygun hale getirmek için kodladım. Ardından veriyi eğitim ve test olarak ikiye ayırdım.

### 🧠 Modelleme
Farklı modeller denedim:

- Logistic Regression ile temel bir tahmin modeli oluşturdum.
- Random Forest ile hem default parametrelerle hem de GridSearchCV ile optimize edilmiş haliyle performans karşılaştırması yaptım.
  
Model başarısını sadece doğrulukla değil, özellikle "No-show" olan hastaları doğru yakalama oranı (recall) ile ölçtüm. Çünkü amaç, gelmeyen hastaları mümkün olduğunca kaçırmamak.

---

## 📈 Sonuçlar

| Model                  | Accuracy | Recall (No-show=1) | F1 Score |
|------------------------|----------|---------------------|----------|
| Logistic Regression    | %56.4    | 0.57                | 0.43     |
| Random Forest (default)| %67.0    | 0.25                | 0.30     |
| ✅ Random Forest (tuned)| **%57.4**| **0.56**            | **0.43** |

> Burada gördüğünüz gibi, accuracy yüksek gözükse de No-show sınıfını yakalamak önemliydi. Bu yüzden recall’u optimize eden Random Forest (tuned) modeli seçtim.

---

## 🔗 Kaggle Notebook Linki

Projeyi adım adım incelemek için (https://www.kaggle.com/code/emirciicek/akbank-makine-ogrenmesi) ulaşabilirsiniz.
 
**Emir Çiçek**  
Akbank ML Bootcamp – 2025 Proje Teslimi  
