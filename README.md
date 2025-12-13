# BLG-307 Yapay Zeka Sistemleri – 1. Proje Ödevi  
## Genetik Algoritma ile Numune Karışımı Optimizasyonu

Öğrenci: Ali Uçma  
Numara: 2212721007  
Senaryo: 7 – Laboratuvarda Numune Karışımı  

---

## 📌 Proje Açıklaması

Bu projede, bir biyoteknoloji laboratuvarında en verimli test çözeltisini elde etmek amacıyla iki farklı reaktifin (Reaktif A ve Reaktif B) karışım oranlarının **Genetik Algoritma (GA)** kullanılarak optimize edilmesi hedeflenmiştir.

Problem, doğrusal olmayan bir amaç fonksiyonuna ve çeşitli kısıtlara sahip olduğundan, klasik optimizasyon yöntemleri yerine evrimsel bir yaklaşım olan genetik algoritma tercih edilmiştir.

Amaç, verilen kısıtlar altında **test hassasiyeti puanını maksimum yapan** reaktif oranlarını belirlemektir.

---

## 📐 Problem Tanımı ve Matematiksel Model

### Amaç Fonksiyonu (Test Hassasiyeti)

Test hassasiyeti aşağıdaki matematiksel model ile ifade edilmiştir:


y =  = 3x₁ + 2x₂ + x₁x₂ - 0.5x₂² 

Burada;  
y: Test hassasiyeti puanı  
x₁: Reaktif A oranı (%)  
x₂: Reaktif B oranı (%)  

Bu fonksiyon **maksimize edilmektedir**.

---

## 📌 Değişkenler (Decision Variables)

| Değişken | Açıklama | Aralık |
|--------|---------|--------|
| x₁ | Reaktif A oranı (%) | 10 – 80 |
| x₂ | Reaktif B oranı (%) | 10 – 80 |

---

## 📌 Kısıtlar (Constraints)

- Reaktif oranlarının toplamı %100’ü geçemez  
  x₁ + x₂ ≤ 100 

- Reaktif A oranı en az %25 olmalıdır  
 x₁ ≥ 25 

---

## 🧬 Genetik Algoritma Yapısı

Problem sürekli (float) değişkenler içerdiğinden hassas ayarlamaya uygun bir genetik algoritma tasarlanmıştır.

### ✔ Birey Temsili
Her birey iki gen içeren bir yapıdadır:
[x₁, x₂]

yaml
Kodu kopyala

### ✔ Başlangıç Popülasyonu
Popülasyon büyüklüğü: 30  
Bireyler, değişken sınırları içerisinde rastgele oluşturulmuştur.

### ✔ Seçim Mekanizması
Turnuva seçimi (k = 3) kullanılmıştır.

### ✔ Çaprazlama (Crossover)
Aritmetik (ağırlıklı ortalama) çaprazlama yöntemi uygulanmıştır.

### ✔ Mutasyon
- x₁ genine ±5 aralığında küçük değişimler  
- x₂ genine ±5 aralığında küçük değişimler  
- Mutasyon olasılığı: 0.2  

Bu yöntemle çözüm uzayında ince ayar yapılması sağlanmıştır.

### ✔ Kısıt Yönetimi
Kısıtları ihlal eden bireylere yüksek ceza değeri uygulanarak (ceza fonksiyonu) uygun olmayan çözümler elenmiştir.

### ✔ Nesil Sayısı
Toplam: 100 nesil

---

## 📌 Sonuçlar

Genetik algoritma çalıştırıldığında elde edilen en iyi çözüm aşağıdaki gibidir:

| Parametre | Değer |
|--------|------|
| Reaktif A (x₁) | ≈ 70 – 75 % |
| Reaktif B (x₂) | ≈ 25 – 30 % |
| Maksimum Test Hassasiyeti | ≈ 1800-1900|

Elde edilen sonuçlar, reaktif oranlarının dengeli bir şekilde dağıtılmasının test hassasiyetini artırdığını göstermektedir.

---

## 📈 Fitness Grafiği

Fitness grafiği incelendiğinde:

- İlk nesillerde hızlı bir artış gözlemlenmiştir.
- Orta nesillerden itibaren artış hızı azalmış,
- Son nesillerde algoritmanın **optimum çözüme yakınsadığı** görülmüştür.

(Not: Fitness grafiği notebook dosyasında gösterilmiştir.)

---

## 📁 Dosya Yapısı

├── README.md
├── YZS_ödev1.ipynb
