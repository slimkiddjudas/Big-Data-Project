# Global Terrorism Database Analizi

## 📊 Proje Özeti

Bu proje, Global Terrorism Database (GTD) üzerinde terörist grup tahmini ve terörizm eğilim analizi odaklı kapsamlı bir analiz ve makine öğrenimi yaklaşımı sunar. Analiz; veri ön işleme, keşifsel veri analizi, makine öğrenimi modeli geliştirme ve tahminler için interaktif bir web arayüzü içerir.

## 🎯 Amaçlar

- **Veri Analizi**: 1970-2020 yılları arasındaki küresel terörizm örüntülerinin kapsamlı incelenmesi
- **Tahmine Dayalı Modelleme**: Saldırı özelliklerine göre terörist grupları tahmin eden makine öğrenimi modelleri geliştirilmesi
- **Görselleştirme**: Zaman, coğrafya ve saldırı türlerine göre terörizm eğilimlerini gösteren interaktif grafikler oluşturulması
- **Kullanıcı Arayüzü**: Gerçek zamanlı terörist grup tahmini için Gradio tabanlı web uygulaması
- **Coğrafi Analiz**: Bölgesel ve ülke bazında terörizm profillerinin incelenmesi

## 📋 Veri Seti Bilgisi

**Data Source**: START (National Consortium for the Study of Terrorism and Responses to Terrorism)

**Citation**: START (National Consortium for the Study of Terrorism and Responses to Terrorism). (2022). Global Terrorism Database, 1970 - 2020 [data file]. https://www.start.umd.edu/data-tools/GTD

**Copyright Notice**: Copyright University of Maryland 2022.

**Website**: https://www.start.umd.edu/gtd-download

### Veri Seti Özellikleri
- **Zaman Aralığı**: 1970-2020
- **Coğrafi Kapsam**: Küresel (200+ ülke ve bölge)
- **Olay Sayısı**: 200.000+ terörizm olayı
- **Değişkenler**: Olay özellikleri, failler, hedefler, silahlar ve sonuçlar dahil 135+ değişken

## 🛠️ Teknik Altyapı

### Programlama Dili & Kütüphaneler
- **Python 3.x**
- **Veri İşleme**: pandas, numpy
- **Görselleştirme**: matplotlib, seaborn
- **Makine Öğrenimi**: scikit-learn
- **Web Arayüzü**: Gradio
- **Model Saklama**: pickle

### Temel Bağımlılıklar
```python
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
gradio>=3.0.0
openpyxl>=3.0.0
```

## 🔧 Kurulum & Başlangıç

1. **Projeyi klonlayın veya dosyaları indirin**
2. **Gerekli paketleri yükleyin:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn gradio openpyxl
   ```
3. **GTD veri setini [START websitesinden](https://www.start.umd.edu/gtd-download) indirin**
4. **Veri setini** `gtd_db.xlsx` olarak proje dizinine yerleştirin
5. **Jupyter notebook'u çalıştırın:** `GTD_Big_Data.ipynb`

## 📁 Proje Yapısı

```
BigData/
├── GTD_Big_Data.ipynb          # Ana analiz notebook'u
├── gtd_db.xlsx                 # GTD veri seti (dahil değil - ayrıca indirilmeli)
├── README.md                   # Bu dosya
├── best_random_forest_model.pkl # Eğitilmiş model (oluşturulacak)
├── label_encoders.pkl          # Label encoder'lar (oluşturulacak)
└── label_mappings.pkl          # Label mapping'ler (oluşturulacak)
```

## 🧪 Analiz Akışı

### 1. Veri Ön İşleme
- **Eksik Değer İşlemi**: %90'dan fazla eksik veriye sahip sütunlar çıkarılır
- **Özellik Seçimi**: 10 anahtar öngörücü özelliğe odaklanılır
- **Label Encoding**: Kategorik değişkenler sayısal formata dönüştürülür
- **Veri Filtreleme**: En aktif 50 terörist gruba odaklanılır

### 2. Keşifsel Veri Analizi
- **Zamansal Eğilimler**: Yıllara göre terörizm olaylarının analizi
- **Coğrafi Dağılım**: Ülke ve bölge bazında saldırı örüntüleri
- **Saldırı Özellikleri**: Saldırı türü, hedef türü ve silah türüne göre analiz
- **Kayıp Analizi**: Ölüm ve yaralanma profillerinin farklı boyutlarda incelenmesi
- **Grup Aktivitesi**: En aktif terörist organizasyonlar

### 3. Makine Öğrenimi Modelleri

#### Uygulanan Modeller
1. **Random Forest Classifier** (Ana Model)
2. **K-Nearest Neighbors (KNN)**
3. **Decision Tree Classifier**

#### Model Özellikleri
- **Girdi Değişkenleri**: Yıl, Ülke, Saldırı Türü, Hedef Türü, Silah Türü, Kayıplar, Başarı Oranı, İntihar Saldırısı
- **Hedef Değişken**: Terörist Grup Adı
- **Performans Optimizasyonu**: GridSearchCV ile hiperparametre ayarı
- **Değerlendirme Metrikleri**: Accuracy, Precision, Recall, F1-Score, Confusion Matrix

#### En İyi Model Performansı
- **Algoritma**: Optimize edilmiş parametrelerle Random Forest
- **Eğitim Verisi**: Filtrelenmiş veri setinin %80'i
- **Test Verisi**: Filtrelenmiş veri setinin %20'si
- **Özellik Önemi**: En öngörücü değişkenlerin analizi

### 4. İnteraktif Web Uygulaması
- **Framework**: Gradio
- **Fonksiyonellik**: Gerçek zamanlı terörist grup tahmini
- **Girdi Parametreleri**: Saldırı özellikleri ve lokasyon
- **Çıktı**: Tahmin edilen grup ve güven skoru

## 📈 Temel Bulgular

### Zamansal Eğilimler
- 2000'li yıllardan itibaren terörizm olaylarında belirgin artış gözlenmiştir
- Büyük küresel çatışmalar sırasında zirve dönemleri yaşanmıştır
- Yıllık kayıp eğilimleri, jeopolitik olaylarla korelasyon göstermektedir

### Coğrafi Bulgular
- Orta Doğu ve Güney Asya başlıca sıcak noktalardır
- Ülke bazında analizler, bölgesel örüntüleri ortaya koymaktadır
- Kentsel ve kırsal olay dağılımı incelenmiştir

### Saldırı Özellikleri
- En yaygın saldırı türü: Bombalama/Patlama
- Ana hedefler: Sivil ve özel mülkler
- Tercih edilen silahlar: Ateşli silahlar ve patlayıcılar

### Organizasyonel Analiz
- En aktif 10 terörist grup belirlenmiştir
- Gruba özgü operasyonel profiller ve tercihler analiz edilmiştir
- Grup aktivitelerinin zamansal değişimi incelenmiştir

## 🎯 Model Uygulamaları

### Tahmine Dayalı Yetenekler
- **Grup Tanımlama**: Saldırı özelliklerine göre olası failleri tahmin etme
- **Risk Değerlendirmesi**: Gelecekteki olaylarda grup katılımı olasılığını değerlendirme
- **Örüntü Tanıma**: Farklı organizasyonların operasyonel imzalarını belirleme

### Kullanım Alanları
- **Akademik Araştırma**: Terörizm çalışmaları ve çatışma analizi
- **Politika Analizi**: Politika geliştirme için terörizm eğilimlerinin anlaşılması
- **Güvenlik Planlaması**: Risk değerlendirmesi ve tehdit analizi
- **Eğitim Amaçlı**: Makine öğrenimi uygulamalarını öğrenme

## 🙏 Teşekkürler

- **START Consortium** for providing the Global Terrorism Database
- **University of Maryland** for maintaining the GTD
- **Academic Community** for terrorism research methodologies
- **Open Source Libraries** used in this analysis

## ⚠️ Disclaimer

This analysis is conducted solely for academic and educational purposes. The findings and models should not be used for any harmful activities or to promote violence. The analysis aims to contribute to the understanding of terrorism patterns for prevention and academic research.

---

**Data Citation**: START (National Consortium for the Study of Terrorism and Responses to Terrorism). (2022). Global Terrorism Database, 1970 - 2020 [data file]. https://www.start.umd.edu/data-tools/GTD

**Copyright Notice**: Copyright University of Maryland 2022.
