# Fiyat Tahmin Datathon Projesi

## 📋 Proje Hakkında

Bu proje, ürün fiyatlarını tahmin etmek için makine öğrenmesi modelleri kullanılan bir veri bilimi yarışması çalışmasıdır. Proje, çeşitli ürün özellikleri, zaman serisi verileri ve ekonomik göstergeleri kullanarak ürün fiyatlarını tahmin etmeyi amaçlamaktadır.

## 🎯 Amaç

Bu yarışmada amacımız her ürünün satış fiyatını tahmin etmektir. Test setindeki her id için ürün fiyatı değişkeninin değerini tahmin etmeniz gerekir.

## 📊 Veri Seti

### Dosyalar

- **train.csv** - Eğitim seti (227,520 satır)
- **testFeatures.csv** - Test seti 
- **GunlukKur.csv** - Günlük USD/TL kuru verileri
- **TuketiciFiyatEndeksi.csv** - Tüketici Fiyat Endeksi (TÜFE) verileri
- **AylikTUIKFiyatEndeksi.csv** - Aylık TÜİK Fiyat Endeksi verileri
- **submissionCAT_v1(17).csv** - Tahmin verileri

### Veri Sütunları

| Sütun | Açıklama |
|-------|----------|
| **tarih** | Ürünün özelliklerinin belirlendiği tarih |
| **ürün** | Ürünün ismi (79 farklı ürün) |
| **ürün besin değeri** | Ürünün sahip olduğu besin değeri |
| **ürün kategorisi** | Ürünün ait olduğu kategori (6 kategori) |
| **ürün fiyatı** | Ürünün fiyatı (hedef değişken) |
| **ürün üretim yeri** | Ürünün üretim yeri (Yurt içi / Yurt dışı) |
| **market** | Ürünün satıldığı market (3 farklı market) |
| **şehir** | Ürünün satıldığı şehir (8 farklı şehir) |

## 🔍 Veri Analizi ve Özellik Mühendisliği

### Keşifsel Veri Analizi (EDA)

- Ürün fiyat dağılımlarının incelenmesi
- Kategorik değişkenlerin fiyat üzerindeki etkilerinin analizi
- Zaman serisi analizi (2019-2023 arası)
- Ürün, kategori, şehir ve market bazlı fiyat analizleri
- Varyans analizi ve açıklama oranları

### Özellik Mühendisliği

Projede aşağıdaki özellikler oluşturulmuştur:

1. **Besin Başına Fiyat**: Ürün fiyatı / Besin değeri
2. **Zaman Özellikleri**: Yıl, ay, gün, hafta günü, mevsim
3. **Kombinasyon Özellikleri**: 
   - Kategori_Market
   - Ürün_Şehir
   - Üretim Yeri_Market
   - Market_Şehir
   - Şehir_Kategori
4. **Yeni Kategoriler**: Ürünler daha detaylı kategorilere ayrılmıştır
5. **Ekonomik Göstergeler**:
   - USD/TL kuru
   - TÜFE (Tüketici Fiyat Endeksi)
   - TÜİK Gıda Fiyat Endeksi
6. **İstatistiksel Özellikler**:
   - Ürün bazlı ortalama fiyatlar
   - Kategori bazlı standart sapma ve varyasyon katsayıları

## 🤖 Modelleme

### Model Karşılaştırması

Projede aşağıdaki modeller test edilmiştir:

| Model | Validation RMSE |
|-------|----------------|
| **CatBoost** | 1.1181 |
| **XGBoost** | 1.1528 |
| **Random Forest** | 1.2272 |
| **LightGBM** | 1.4496 |

### Final Model

En iyi performansı gösteren **CatBoost Regressor** modeli seçilmiştir.

**Model Parametreleri:**
- `depth`: 7
- `iterations`: 900
- `l2_leaf_reg`: 1
- `learning_rate`: 0.1
- `random_state`: 42

**Final Validation RMSE**: 0.9700

## 📈 Model Performansı

- **RMSE**: 0.9700 TL
- **Ortalama Fiyat**: ~17 TL
- **RMSE/Ortalama Oranı**: ~%5.7
- **Performans Değerlendirmesi**: ✅ İyi performans (RMSE ortalamanın %10'undan küçük)

## 📦 Kullanılan Kütüphaneler

```python
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- xgboost
- catboost
- lightgbm
```


## 📝 Değerlendirme Metriği

Ürünün tahmin edilen değeri ile ürünün gerçek fiyatı arasında **Kök-Ortalama-Kare-Hata (RMSE)** üzerinden değerlendirilir.

RMSE formülü:
```
RMSE = √(Σ(y_pred - y_true)² / n)
```

## 📄 Lisans

Bu proje bir datathon yarışması kapsamında geliştirilmiştir.
