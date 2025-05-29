
# 📘 NLP_HW_1 – Metin Benzerliği Analizi (TF-IDF & Word2Vec)

Bu proje, [Doğal Dil İşleme](https://github.com/ahmetmetinakan/NLP_HW_1) dersi kapsamında gerçekleştirilmiş olup, kullanıcı yorumlarına dayalı olarak metinler arası benzerliklerin hem TF-IDF hem de Word2Vec yöntemleriyle hesaplanmasını ve karşılaştırılmasını içermektedir.

---

## 📌 Projenin Amacı

- Eğitilen TF-IDF ve Word2Vec modelleriyle, giriş metnine en çok benzeyen 5 metni tespit etmek
- Modellerin çıktıları üzerinden anlamsal ve istatistiksel karşılaştırmalar yapmak
- Jaccard benzerlikleriyle model sıralama tutarlılığını analiz etmek
- En başarılı modelleri ortaya çıkarmak

---

## 📂 Kullanılan Veriler

- `fordlemmatized.csv` – lemmatize edilmiş yorumlar
- `fordstemmed.csv` – stem uygulanmış yorumlar
- 16 adet Word2Vec modeli (`.model` formatında)  
  (CBOW / SkipGram × window=2/4 × dim=100/300)
- 2 adet TF-IDF CSV vektör dosyası

---

## 🧪 Uygulama Aşamaları

### ✅ 1. Ön İşleme
- Cümleler tokenize edildi, gereksiz karakterler kaldırıldı.
- Hem **lemmatized** hem de **stemmed** versiyonlar hazırlandı.

### ✅ 2. TF-IDF Vektörleme
- `TfidfVectorizer()` kullanılarak her metin için sparse vektör matrisi oluşturuldu.
- Cosine similarity ile en benzer 5 metin bulundu.

### ✅ 3. Word2Vec Vektörleme
- Giriş metnindeki kelimelerin vektörleri ortalamaya alınarak cümle vektörü elde edildi.
- Cosine similarity ile 5 en benzer metin hesaplandı.
- Bu işlem 16 model için ayrı ayrı tekrarlandı.

### ✅ 4. Anlamsal Değerlendirme
- Her modelin önerdiği 5 metne anlam benzerliği puanı (1–5) verildi.
- Ortalama skorlar hesaplandı ve sıralandı.

### ✅ 5. Jaccard Benzerliği Analizi
- 16 modelin her birinin önerdiği ilk 5 metin karşılaştırıldı.
- 18x18 Jaccard benzerlik matrisi oluşturuldu.
- En tutarlı model çiftleri belirlendi.

---

## 📈 Öne Çıkan Sonuçlar

- **En Başarılı Model** → `lemmatized_skipgram_w2_d300` (Ortalama Anlam Skoru: 4.2)
- **En Tutarlı Model Çifti** → `lemmatized_skipgram_w4_d300` ↔ `stemmed_skipgram_w4_d300` (Jaccard: 0.43)

---

## 🔍 Giriş Metni (Örnek)
```text
bought mine use 20k ad sct tuner ford cai flowmaster out axle back exhaust car beast now
```

---

## ▶️ Çalıştırma Talimatları

1. Gerekli kütüphaneleri yükleyin:
```bash
pip install pandas numpy gensim scikit-learn matplotlib seaborn
```

2. `main.ipynb` ya da `main.py` dosyasını çalıştırın.

3. Tüm çıktı dosyaları (`jaccard_matrix.csv`, görseller vb.) otomatik olarak oluşacaktır.

---

## 📎 Proje Raporu

> Detaylı PDF/Word raporu proje kök dizininde `NLP_HW_Report.pdf` olarak yer almaktadır.  
> Kodla birlikte değerlendirilmesi önerilir.

---

## 📬 İletişim

> 📛 Hazırlayan: Ahmet Metin Akan  
> 🧑‍💻 GitHub: [@ahmetmetinakan](https://github.com/ahmetmetinakan)
