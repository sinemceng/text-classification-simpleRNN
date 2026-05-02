# News Category Classification with Simple RNN

Bu proje, Kaggle üzerindeki "News Category Dataset" kullanılarak, haber başlıkları ve kısa açıklamalarından haberin kategorisini (Spor, Teknoloji veya Siyaset) tahmin eden bir derin öğrenme modelini içermektedir. Model, metin verilerinin ardışık yapısını öğrenmek için **Simple RNN** (Simple Recurrent Neural Networks) mimarisini kullanır.

## 🚀 Proje Özeti
- **Veri Seti:** 40 farklı kategoriden 200.000'den fazla haber içeren [News Category Dataset](https://www.kaggle.com/datasets/rmisra/news-category-dataset/data).
- **Kapsam:** Veri seti sadeleştirilerek **SPORTS**, **TECH** ve **POLITICS** sınıflarına odaklanılmıştır.
- **Teknolojiler:** Python, TensorFlow/Keras, Pandas, Scikit-learn, NLTK, Matplotlib, Seaborn.
- **Donanım:** Google Colab Pro üzerinde L4 GPU hızlandırıcısı kullanılmıştır.

## 🛠️ Uygulanan Adımlar

### 1. Veri Keşfi ve Temizleme (EDA)
- JSON formatındaki veri seti okunarak analiz edildi.
- Tahminleme için gereksiz olan `link`, `authors` ve `date` sütunları kaldırıldı.
- Sınıf dengesizliği kontrol edildi ve modelin başarısını artırmak için birbirinden belirgin 3 ana kategori seçildi.

### 2. Metin Önişleme
- Haber başlıkları (`headline`) ve özetleri (`short_description`) birleştirilerek zengin bir metin içeriği oluşturuldu.
- Tüm metinler küçük harfe çevrildi.
- URL'ler, noktalama işaretleri ve rakamlar Regex kullanılarak temizlendi.
- **Stopwords:** İngilizce dilindeki anlamsız kelimeler (the, is, and vb.) NLTK kütüphanesi ile temizlendi.
- Kelime uzunluğu 3'ten küçük olan veriler veri setinden çıkarıldı.

### 3. Görselleştirme
- Haber kategorilerinin dağılımı Seaborn ile grafikleştirildi.
- **WordCloud:** Metin verisindeki en sık geçen kelimeler görselleştirilerek veri setinin içeriği analiz edildi.

### 4. Model Mimarisi (Simple RNN)
Model, metinleri sayısal dizilere dönüştürmek için `Tokenizer` ve `pad_sequences` işlemlerinden geçtikten sonra şu katmanlarla eğitilmiştir:
- **Embedding Layer:** Kelimelerin anlamsal ilişkilerini yakalamak için.
- **Simple RNN Layer:** Metnin ardışık yapısını işlemek için.
- **Dropout Layer:** Aşırı öğrenmeyi (overfitting) engellemek için.
- **Dense Layer:** Softmax aktivasyonu ile 3 farklı sınıf için olasılık üretimi.
