# BLG-307 Yapay Zeka Sistemleri – 1. Proje Ödevi

## Genetik Algoritma ile Numune Karışımı Optimizasyonu (Senaryo 7)

**Öğrenci:** Ali Uçma  
**Numara:** 2212721007  
**Ders:** BLG 307 – Yapay Zeka Sistemleri  
**GitHub Repo:** https://github.com/Alu0320/genetik_optimizasyon  

---

## Proje Açıklaması

Bu proje, bir biyoteknoloji laboratuvarında en verimli test çözeltisini elde etmek amacıyla **Genetik Algoritma (GA)** kullanılarak geliştirilmiştir. Amaç; Reaktif A (x1) ve Reaktif B (x2) oranlarını belirli kısıtlar altında optimize ederek **maksimum Test Hassasiyeti Puanını** elde etmektir.

Problem, doğrusal olmayan bir amaç fonksiyonuna ve birden fazla kısıta sahip olduğu için klasik optimizasyon yöntemleri yerine, küresel arama yeteneği güçlü olan **evrimsel hesaplama tabanlı Genetik Algoritma** tercih edilmiştir.

---

## Problem Tanımı ve Matematiksel Model

### Amaç Fonksiyonu (Maksimizasyon)

$$y = 3x_1 + 2x_2 + x_1x_2 - 0.5x_2^2$$


### Değişkenler

- **x1:** Reaktif A oranı (%) → [10, 80]  
- **x2:** Reaktif B oranı (%) → [10, 80]

### Kısıtlar

- **Toplam Karışım Kısıtı:**  
x1 + x2 ≤ 100

- **Minimum Reaktif A Kısıtı:**  
x1 ≥ 25

---

## Algoritma Tasarımı ve Kullanılan Yöntemler

Bu çalışmada, problem yapısına uygun olarak özelleştirilmiş bir **Genetik Algoritma** uygulanmıştır.

### Birey Temsili
Her birey `[x1, x2]` şeklinde iki genli bir kromozom ile temsil edilmektedir. Genetik işlemler sonrasında bireyler **onarım (repair) mekanizması** ile kısıtlara uygun hale getirilmekte ve **tamsayı değerlere yuvarlanmaktadır**.

### Popülasyon
Algoritma, başlangıçta **40 bireyden** oluşan rastgele bir popülasyon ile çalışmaktadır.

### Uygunluk (Fitness) Fonksiyonu
Amaç fonksiyonu temel alınmış, kısıt ihlallerinde **ceza (penalty)** terimleri uygulanmıştır. Bu sayede kısıt dışı çözümler düşük fitness değeri alarak elenmiştir.

### Kısıt Yönetimi
Kısıtları ihlal eden bireyler doğrudan silinmek yerine, matematiksel olarak sınırlar içerisine çekilmiştir. Bu **hibrit ceza + onarım yaklaşımı**, algoritmanın geçerli çözüm uzayında kalmasını sağlamıştır.

### Seçim (Selection)
**Rulet Tekerleği Seçimi (Roulette Wheel Selection)** kullanılmıştır. Fitness değeri yüksek olan bireylerin ebeveyn seçilme olasılığı daha fazladır.

### Çaprazlama (Crossover)
**Uniform Crossover** yöntemi uygulanmıştır. Ebeveyn genleri %50 olasılıkla çocuk bireylere aktarılmıştır.

### Mutasyon
Genler, belirli bir olasılıkla `±1` veya `±5` değerleriyle değiştirilerek çeşitlilik sağlanmıştır. Mutasyon sonrası bireyler tekrar onarım işlemine tabi tutulmuştur.

### Elitizm
Her nesilde en iyi birey, bir sonraki nesle **doğrudan aktarılmıştır**.

---

## Sonuçlar

Algoritma **50 nesil** boyunca çalıştırılmış ve aşağıdaki en iyi çözüme ulaşılmıştır:

| Parametre | Değer |
|---------|------|
| Reaktif A (x1) | %67 |
| Reaktif B (x2) | %33 |
| Toplam Oran | %100 |
| Maksimum Fitness | 1933.50 |


### Yorum
Sonuçlar incelendiğinde, algoritmanın toplam karışım sınırını (%100) tam olarak kullandığı görülmektedir. Amaç fonksiyonunda **x1 katsayısının daha baskın olması**, çözümün x1 yönünde artmasına neden olmuştur. Ancak x2 değişkeninin pozitif katkısı sebebiyle optimum denge yaklaşık **%67 – %33** oranında oluşmuştur.

---

## Grafik Analizi

Fitness–Nesil grafiği incelendiğinde:

- Algoritmanın ilk nesillerde hızlı bir yakınsama gösterdiği,  
- Erken aşamada küresel maksimuma ulaştığı,  
- Sonraki nesillerde bu değeri koruyarak **kararlı (stabil)** bir çözüm ürettiği  

gözlemlenmiştir.

Bu durum, kullanılan GA parametrelerinin problem için uygun seçildiğini göstermektedir.

---

## Kurulum ve Çalıştırma

Proje **Python** dili ile geliştirilmiştir.

### Gerekli kütüphaneler:
pip install numpy matplotlib

Kodu kopyala

### Çalıştırma:
`YZS_1_Proje.ipynb` dosyasını **Jupyter Notebook** veya **Google Colab** ortamında açarak çalıştırabilirsiniz.
