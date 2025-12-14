# BLG-307 Yapay Zeka Sistemleri – 1. Proje Ödevi

## Genetik Algoritma ile Numune Karışımı Optimizasyonu (Senaryo 7)

Öğrenci: Ali Uçma
Numara: 2212721007
Ders: BLG 307 - Yapay Zeka Sistemleri
GitHub Repo Bağlantısı: https://github.com/Alu0320/genetik_optimizasyon


---

### Proje Açıklaması

Bu proje, bir biyoteknoloji laboratuvarında en verimli test çözeltisini elde etmek amacıyla Genetik Algoritma (GA) kullanılarak geliştirilmiştir. Amaç, Reaktif A ve Reaktif B oranlarını belirli kısıtlar altında optimize ederek maksimum Test Hassasiyeti Puanını elde etmektir.

Problem, doğrusal olmayan bir amaç fonksiyonuna ve katı kısıtlara sahip olduğu için evrimsel hesaplama yöntemleri tercih edilmiştir.

---

### Problem Tanımı ve Matematiksel Model

Amaç Fonksiyonu (Maksimizasyon):
$$y = 3x_1 + 2x_2 + x_1x_2 - 0.5x_2^2$$

Değişkenler:
* x1: Reaktif A oranı (%) → [10, 80]
* x2: Reaktif B oranı (%) → [10, 80]

Kısıtlar:
1. Toplam Karışım Kısıtı: $x_1 + x_2 \le 100$
2. Minimum A Reaktif Kısıtı: $x_1 \ge 25$

---

### Algoritma Tasarımı ve Yöntemler

Bu projede problemin doğasına uygun olarak Sürekli (Real-valued) Genetik Algoritma kullanılmıştır. Kodda kullanılan yöntemler şunlardır:

* Birey Temsili: Her birey [x1, x2] şeklinde ondalıklı (float) sayılardan oluşan bir kromozoma sahiptir.
* Popülasyon: Algoritma, belirlenen aralıklarda rastgele oluşturulmuş 30 bireylik bir popülasyon ile çalışır.
* Kısıt Yönetimi: Kısıtları ihlal eden (örneğin toplamı 100'ü geçen) bireyler silinmek yerine, matematiksel olarak sınırlar içine çekilerek geçerli hale getirilmiştir. Bu sayede algoritma geçerli çözüm uzayında kalmaktadır.
* Seçim (Selection): Turnuva Seçimi (Tournament Selection) kullanılmıştır (k=3). Rastgele seçilen 3 birey arasından en iyisi ebeveyn olarak seçilir.
* Çaprazlama (Crossover): Uniform Crossover kullanılmıştır. Ebeveynlerin genleri olasılıksal olarak takas edilir.
* Mutasyon: Genlere ± 2.0 aralığında rastgele küçük değerler eklenerek (random.uniform) yerel arama ve çeşitlilik sağlanmıştır.

---

### Sonuçlar

Algoritma 50 nesil boyunca çalıştırılmış ve aşağıdaki en iyi sonuçlara ulaşılmıştır:

| Parametre | Değer |
| :--- | :--- |
| Reaktif A (x1) | % 67.08 |
| Reaktif B (x2) | % 32.92 |
| Toplam Oran | % 100.00 |
| Maksimum Skor (Fitness) | 1933.49 |

Yorum:
Sonuçlar incelendiğinde, algoritmanın toplam sınırını (100) tam olarak kullandığı görülmektedir. x1 değişkeninin katsayısı denklemde daha baskın olduğu için algoritma bu oranı artırma eğilimine girmiş, ancak x2 değişkeninin de denklemdeki pozitif etkisi nedeniyle dengeyi %67 - %33 civarında kurmuştur.

---

### Grafik Analizi

Elde edilen Fitness - Nesil grafiğinde:
* Algoritma ilk nesillerde çok hızlı bir şekilde geçerli ve yüksek skorlu çözümlere ulaşmıştır.
* İlerleyen nesillerde grafik yatay seyretmiştir; bu durum algoritmanın Global Maksimum noktasına (1933.49) çok erken ulaştığını ve bu noktayı koruyarak hassas ayar (fine-tuning) yaptığını göstermektedir.

---

### Kurulum ve Çalıştırma

Proje Python dili ile yazılmıştır.

1. Gerekli kütüphaneleri yükleyin:
   pip install numpy matplotlib

2. YZS_odev1.ipynb dosyasını Jupyter Notebook veya Google Colab ile açarak çalıştırın.
