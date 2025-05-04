# **Veri Setinin Kullanım Amaçları**

**1. Duygu Analizi (Sentiment Analysis)**
  Yorumlardaki olumlu ve olumsuz ifadeleri sınıflandırmak.
  Kullanıcı memnuniyet düzeylerini otomatik olarak belirlemek.
  Pazarlama ekipleri için olumlu yorumları ön plana çıkarma veya şikayet odaklarını belirleme.

**2. Tema ve Konu Tespiti**
  Yorumlar içinde en çok tekrar eden konuları tespit ederek:
  “motor”, “yakıt”, “iç tasarım”, “konfor” gibi kategoriler oluşturulabilir.
  Şikayet edilen ve övülen yönler otomatik olarak gruplanabilir.

**3. Ürün Geliştirme ve Geri Bildirim Analizi**
  Ford araçlarının hangi özelliklerinin beğenildiği veya sorun yaşandığı anlaşılabilir.
  Müşteri geri bildirimi doğrudan analiz edilerek, yeni ürün tasarımında kullanılabilir.

**4. Öneri Sistemleri (Recommendation Systems)**
  Benzer görüşe sahip kullanıcıların tercih ettiği modeller belirlenerek öneri sistemleri geliştirilebilir.
  “Bu aracı beğenenler şunu da değerlendirdi” türü yönlendirmeler oluşturulabilir.

**5. Kelime Dağılımı ve Kullanım Frekansı Analizi**
  Zipf yasası uygulamaları, dil istatistikleri çalışmaları, kelime dağılım dengesizliği araştırmaları için uygun.
  Otomobil sektörü özelinde teknik terimlerin ağırlık analizi yapılabilir.

**6. Eğitim ve Araştırma Amaçlı Kullanım**
  NLP projelerinde (TF-IDF, Word2Vec, LSTM, vs.) gerçek dünya verisiyle model eğitimi için kullanılabilir.
  Akademik ödevler, tez çalışmaları veya makine öğrenmesi projelerinde dil modelleme örneği olarak değerlidir.

# **Github Repostory Üzerinden Model Nasıl Kurulur:**

1. "ford.csv" verisetini indiriniz.
2. "nlp.ipynb" dosyasını indiriniz.
3. "ford.csv" ve "nlp.ipynb" dosyalarını aynı klasörün içerisine ekleyiniz.
4. Bilgisayarınızda bulunan derleyiciyi açınız. (tercihen Google Colab)
5. Aşağıda yer alan gerekli sürümleri ile verilmiş kütüphaneleri indiriniz ve kurulumlarını yapınız.
6. "nlp.ipynb" dosyasındaki kodları sırayla gerçekleştiriniz.
7. Pre-Processing adımlarında çalıştırılan her kod verisetine yeni bir sütun ekler.
8. Lemmatization ve Stemming adımları ise yeni ".csv" dosyaları oluşturur.
9. Oluşan bu yeni ".csv" dosyaları vektörleme adımlarında ihtiyaca göre kullanılır.


# **Zorunluluklar:**

| Kütüphane                | Sürüm (Tavsiye edilen / kullanılan) | Amaç / Açıklama                                                                  |
| ------------------------ | ----------------------------------- | -------------------------------------------------------------------------------- |
| `pandas`                 | ≥ 1.3.0 (genelde 1.5.x - 2.x arası) | CSV dosyalarını okumak, sütun eklemek, veri çerçeveleriyle çalışmak.             |
| `nltk`                   | ≥ 3.7                               | Doğal dil işleme araçları (stopwords, tokenizer, stemming, lemmatization).       |
| `re` (yerleşik)          | -                                   | Regular expression işlemleri (noktalama temizliği, metin temizleme).             |
| `ast` (yerleşik)         | -                                   | String içinde tutulmuş Python listelerini (örneğin `"['car', 'drive']"`) çözmek. |
| `sklearn` (scikit-learn) | ≥ 1.0                               | TF-IDF vektörleştirme (`TfidfVectorizer`)                                        |
| `gensim`                 | 4.3.1 veya 4.3.3                    | Word2Vec modellerinin eğitimi (CBOW ve Skip-gram modelleri için kullanıldı).     |
| `numpy`                  | 1.23.5 (gensim uyumlu)              | Gensim, sklearn ve diğer kütüphanelerin içsel hesaplamalarında temel araç.       |
| `scipy`                  | 1.10.1 veya 1.13.1                  | TF-IDF matris işlemleri, sklearn bağımlılığı olarak.                             |

## **Kütüphane Kurulumları:**

pip install gensim==4.3.1 numpy==1.23.5 scipy==1.10.1

pip install pandas scikit-learn nltk

## **NLTK verilerini indirmek için:**

import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
nltk.download('omw-1.4')



##**Kütüphanelerin Kullanım Yerleri Özet**
| İşlem                         | Kullanılan Kütüphaneler             |
| ----------------------------- | ----------------------------------- |
| Stopword temizleme            | `nltk`, `re`, `pandas`              |
| Tokenization (ayrıştırma)     | `re`, `pandas`                      |
| Lowercasing                   | `pandas`                            |
| Lemmatization                 | `nltk.WordNetLemmatizer`, `ast`     |
| Stemming                      | `nltk.PorterStemmer`, `ast`         |
| TF-IDF Vektörleme             | `sklearn.TfidfVectorizer`, `ast`    |
| Word2Vec (CBOW & Skip-gram)   | `gensim.models.Word2Vec`, `ast`     |
| Zipf grafiği (önceki aşamada) | `collections.Counter`, `matplotlib` |


## **Kullanım Uyum Notu:**
Gensim 4.x sürümleri, Python 3.8+ sürümleriyle uyumludur.

Colab ortamında bazen numpy>=2.0 ve gensim<4.4 çakışabiliyor. Bu yüzden numpy==1.23.5 öneriliyor.

nltk her ortamda çalışır, ancak punkt ve wordnet gibi veri dosyaları ilk kullanımda indirilmelidir.
