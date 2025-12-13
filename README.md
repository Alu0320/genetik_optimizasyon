# BLG 307 – Yapay Zeka Sistemleri  
## Proje 1: Genetik Algoritma ile Optimizasyon

## Öğrenci Bilgileri

Ad Soyad: Ali Uçma  
Öğrenci No: 2212721007  
Ders: BLG 307 – Yapay Zeka Sistemleri  
Dönem: 2024–2025 Güz  
GitHub Repo: https://github.com/Alu0320/genetik_optimizasyon  


## 1. Proje Tanımı

Bu projede, belirli kısıtlar altında tanımlanmış doğrusal olmayan bir optimizasyon probleminin çözümü amaçlanmıştır. Problem, sürekli değerli karar değişkenleri içerdiği ve klasik yöntemlerle çözümü zor olduğu için **Genetik Algoritma (GA)** yaklaşımı kullanılarak ele alınmıştır.

Amaç, tanımlanan performans fonksiyonunu maksimum yapan karar değişkeni değerlerini bulmaktır.


## 2. Problem Tanımı

### Amaç Fonksiyonu (Performans Skoru)

Sistemin performansı aşağıdaki matematiksel model ile ifade edilmiştir:

\[
y = 5x_1 + 7x_2 - 0.1 \cdot x_1^2 - 0.2 \cdot x_2^2
\]


Burada;  
y: Performans skoru  
x₁: Birinci karar değişkeni  
x₂: İkinci karar değişkeni  

Amaç, verilen kısıtlar altında performans skorunu maksimum yapan x₁ ve x₂ değerlerini belirlemektir.


### Karar Değişkenleri

x₁: 10 – 80 aralığında tanımlı  
x₂: 10 – 80 aralığında tanımlı  


### Kısıtlar

1. Karar değişkenlerinin toplamı 100 değerini geçemez  
   x₁ + x₂ ≤ 100  

2. Birinci karar değişkeni için minimum değer şartı vardır  
   x₁ ≥ 25  


## 3. Kullanılan Yöntem: Genetik Algoritma

Problem, gerçel değerli genler içeren bir genetik algoritma kullanılarak çözülmüştür. Algoritmanın temel bileşenleri aşağıda özetlenmiştir.

Birey Temsili  
Her birey iki gen içeren `[x₁, x₂]` yapısında tanımlanmıştır.

Başlangıç Popülasyonu  
Belirlenen sınırlar içerisinde rastgele bireyler oluşturulmuştur.

Seçilim  
Popülasyondaki bireyler fitness değerlerine göre sıralanmış ve en iyi bireyler seçilmiştir.

Çaprazlama  
Ebeveyn bireylerden yeni bireyler üretmek için ağırlıklı ortalama (aritmetik) çaprazlama yöntemi kullanılmıştır.

Mutasyon  
Belirli bir olasılıkla gen değerlerine küçük rastgele değişiklikler uygulanarak çeşitlilik artırılmıştır.

Kısıt Yönetimi  
Kısıtları ihlal eden bireylere yüksek ceza değeri uygulanarak uygun olmayan çözümler elenmiştir.

Elitizm  
Her neslin en iyi bireyi bir sonraki nesle doğrudan aktarılmıştır.


## 4. Sonuçlar ve Değerlendirme

Algoritma çalıştırıldığında, ilk jenerasyonlarda performans skorunda hızlı bir artış gözlemlenmiş, ilerleyen jenerasyonlarda ise algoritmanın kararlı bir şekilde optimum çözüme yakınsadığı görülmüştür.

Elde edilen sonuçlar, genetik algoritmanın bu problem için etkili ve uygun bir optimizasyon yöntemi olduğunu göstermektedir. Yakınsama süreci grafiklerle desteklenmiştir.


## 5. Kurulum ve Çalıştırma

Projenin çalıştırılabilmesi için aşağıdaki Python kütüphanelerinin yüklü olması gerekmektedir:

```bash
pip install numpy matplotlib
