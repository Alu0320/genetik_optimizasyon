# BLG-307 Yapay Zeka Sistemleri – 1. Proje Ödevi

## Genetik Algoritma ile Numune Karışımı Optimizasyonu (Senaryo 7)

**Öğrenci:** Ali Uçma  
**Numara:** 2212721007  
**Ders:** BLG 307 – Yapay Zeka Sistemleri  
**GitHub Repo:** [https://github.com/Alu0320/genetik_optimizasyon](https://github.com/Alu0320/genetik_optimizasyon)

---

## Proje Açıklaması

Bu proje, bir biyoteknoloji laboratuvarında en verimli test çözeltisini elde etmek amacıyla **Genetik Algoritma (GA)** kullanılarak geliştirilmiştir. Amaç; Reaktif A (x₁) ve Reaktif B (x₂) oranlarını belirli kısıtlar altında optimize ederek **maksimum Test Hassasiyeti Puanını** elde etmektir.

Problem, doğrusal olmayan bir amaç fonksiyonuna ve birden fazla kısıta sahip olduğu için klasik optimizasyon yöntemleri yerine, küresel arama yeteneği güçlü olan **evrimsel hesaplama tabanlı Genetik Algoritma** tercih edilmiştir.

---

## Problem Tanımı ve Matematiksel Model

### Amaç Fonksiyonu (Maksimizasyon)

```math
y = 3x_1 + 2x_2 + x_1x_2 - 0.5x_2^2
```

> Not: GitHub Markdown matematik ifadelerini sınırlı desteklediği için formül kod bloğu içinde gösterilmiştir.

### Değişkenler

* **x₁:** Reaktif A oranı (%) → [10, 80]
* **x₂:** Reaktif B oranı (%) → [10, 80]

### Kısıtlar

* **Toplam Karışım Kısıtı:**  
  x₁ + x₂ ≤ 100

* **Minimum Reaktif A Kısıtı:**  
  x₁ ≥ 25

---

## Algoritma Tasarımı ve Kullanılan Yöntemler

Bu çalışmada, problem yapısına uygun şekilde yapılandırılmış bir **Genetik Algoritma** uygulanmıştır.

### Birey Temsili

Her birey, **[x₁, x₂]** şeklinde iki genli ve sürekli (ondalıklı) değerler içeren bir kromozom ile temsil edilmektedir.

### Popülasyon

Algoritma, başlangıçta **40 bireyden** oluşan rastgele bir popülasyon ile başlatılmaktadır. Başlangıç bireyleri oluşturulurken tüm kısıtlar sağlanmaktadır.

### Uygunluk (Fitness) Fonksiyonu

Uygunluk değeri, doğrudan amaç fonksiyonu kullanılarak hesaplanmıştır. Kısıt ihlali durumunda bireyler ceza puanı verilerek değil, **yeniden üretilerek** çözüm uzayının geçerli bölgesinde tutulmuştur.

### Kısıt Yönetimi

Kısıtları ihlal eden bireyler:

* Çaprazlama veya mutasyon sonrası kontrol edilmekte,
* Geçersiz bireyler, kısıtlara uygun yeni bireylerle değiştirilmektedir.

Bu yaklaşım sayesinde algoritma yalnızca **geçerli çözümler** üzerinde çalışmaktadır.

### Seçilim (Selection)

**Turnuva Seçimi (Tournament Selection)** yöntemi kullanılmıştır. Rastgele seçilen bireyler arasından fitness değeri en yüksek olan birey ebeveyn olarak seçilmektedir.

### Çaprazlama (Crossover)

**Aritmetik Çaprazlama (Arithmetic Crossover)** uygulanmıştır. Ebeveynler, rastgele belirlenen bir α katsayısı ile doğrusal olarak birleştirilerek yeni bireyler üretilmiştir.

### Mutasyon

Mutasyon işlemi, belirli bir olasılıkla gen değerlerine küçük rastgele değişiklikler (±5 aralığında) eklenerek gerçekleştirilmiştir. Mutasyon sonrası bireyler tekrar kısıt kontrolünden geçirilmiştir.

### Nesil Döngüsü

Algoritma **80 nesil** boyunca çalıştırılmış ve her nesilde elde edilen en iyi fitness değeri kaydedilmiştir.

---

## Sonuçlar

Algoritma çalıştırıldığında aşağıdaki en iyi çözüme ulaşılmıştır:

| Parametre        | Değer       |
| ---------------- | ----------- |
| Reaktif A (x₁)   | %68.02      |
| Reaktif B (x₂)   | %31.86      |
| Toplam Oran      | %99.88      |
| Maksimum Fitness | **1927.65** |

---

## Kurulum ve Çalıştırma

Proje **Python** dili ile geliştirilmiştir.

### Gerekli Kütüphaneler

```bash
pip install numpy matplotlib
```

### Çalıştırma

`YZS_1_Proje.ipynb` dosyasını **Jupyter Notebook** veya **Google Colab** ortamında açarak çalıştırabilirsiniz.
