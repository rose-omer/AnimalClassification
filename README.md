# Animal Classification with CNN

Bu proje, bir **Convolutional Neural Network (CNN)** modeli geliştirerek hayvan türlerini sınıflandırmayı amaçlamaktadır. Proje kapsamında, **10 hayvan sınıfını** (collie, dolphin, elephant, fox, moose, rabbit, sheep, squirrel, giant panda, polar bear) sınıflandıran bir model tasarlanmıştır. Ayrıca, modelin performansı manipüle edilmiş görüntüler üzerinde ve renk sabitliği algoritması uygulanmış görüntüler üzerinde test edilmiştir.

---

## Proje Adımları

### 1. Veri Seti
- **Veri Seti Kaynağı:** [Animals with Attributes 2](https://www.kaggle.com/datasets/rrebirrth/animals-with-attributes-2)
- **Kullanılan Sınıflar:**
  - collie
  - dolphin
  - elephant
  - fox
  - moose
  - rabbit
  - sheep
  - squirrel
  - giant panda
  - polar bear
- **Ön İşleme:**
  - Her sınıf için ilk 650 görüntü seçildi.
  - Görüntüler yeniden boyutlandırılarak normalize edildi.
  - Veriler eğitim (%70) ve test (%30) olarak rastgele ayrıldı.

---

### 2. Veri Artırma (Data Augmentation)
Eğitim setine aşağıdaki veri artırma teknikleri uygulandı:
- Döndürme (rotation)
- Yatay çevirme (horizontal flip)
- Kaydırma (width & height shift)
- Gürültü ekleme

---

### 3. CNN Modeli
Model, aşağıdaki katmanlardan oluşmaktadır:
- **Convolutional** Katmanlar: Özellikleri çıkarmak için.
- **MaxPooling** Katmanları: Boyutları küçültmek için.
- **Flatten** ve **Dense** Katmanlar: Sınıflandırma için.
- **Dropout**: Aşırı öğrenmeyi (overfitting) önlemek için.

**Kayıp Fonksiyonu:** `categorical_crossentropy`  
**Optimizasyon Algoritması:** `adam`  

---

### 4. Model Performansı
Model, farklı test durumları üzerinde değerlendirilmiştir:
1. **Orijinal Test Seti:** Manipüle edilmemiş görüntülerle test edilmiştir.
2. **Manipüle Edilmiş Test Seti:** Aydınlatma ve renk manipülasyonu yapılmış görüntülerle test edilmiştir.
3. **Renk Sabitliği Uygulanmış Test Seti:** Manipüle edilmiş görüntülere **Gray World** algoritması uygulanarak test edilmiştir.

---

## Kurulum ve Çalıştırma

### Gereksinimler
Bu projeyi çalıştırmak için aşağıdaki Python kütüphanelerine ihtiyacınız var:
- `numpy`
- `tensorflow`
- `keras`
- `opencv-python`
- `scikit-learn`

Kurulum için:

```bash
pip install numpy tensorflow keras opencv-python scikit-learn

├── data/
│   ├── train/        # Eğitim verileri
│   ├── test/         # Test verileri
│   ├── manipulated/  # Manipüle edilmiş test verileri
│   └── corrected/    # Renk sabitliği uygulanmış test verileri
├── models/
│   └── cnn_model.h5  # Eğitilmiş model
├── main.py           # Ana Python dosyası
├── utils.py          # Yardımcı fonksiyonlar
└── README.md         # Proje açıklamaları

