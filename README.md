# Protein Yapı Sınıflandırma Projesi

Bu proje, protein dizilerini üç farklı yapısal sınıfa (Helix, Sheet, Turn) sınıflandırmak için makine öğrenmesi yöntemleri kullanır.

## 📋 Proje Özeti

Proje, protein dizilerini analiz ederek yapısal sınıflandırma yapmayı amaçlar. İki farklı makine öğrenmesi modeli (SVM ve 1D-CNN) kullanılarak protein yapıları tahmin edilir ve performans metrikleri karşılaştırılır.

## 🎯 Özellikler

- **Protein Dizi Analizi**: FASTA formatındaki protein dizilerinin okunması ve işlenmesi
- **EIIP Kodlaması**: Amino asitlerin Electron-Ion Interaction Potential (EIIP) değerleri ile kodlanması
- **Yapısal Sınıflandırma**: Helix, Sheet ve Turn olmak üzere üç sınıfa sınıflandırma
- **İki Farklı Model**: 
  - Support Vector Machine (SVM)
  - 1D Convolutional Neural Network (CNN)
- **Kapsamlı Değerlendirme**: Accuracy, Precision, Recall, MCC, Kappa ve AUC metrikleri
- **Görselleştirme**: Confusion matrix ve ROC eğrileri

## 📦 Gereksinimler

Projeyi çalıştırmak için aşağıdaki Python kütüphaneleri gereklidir:

```bash
pip install biopython scikit-learn tensorflow openpyxl numpy pandas matplotlib
```

### Kütüphaneler

- **biopython**: FASTA dosyalarını okumak için
- **scikit-learn**: SVM modeli ve metrikler için
- **tensorflow**: CNN modeli için
- **openpyxl**: Excel dosyalarını okumak için
- **numpy**: Sayısal işlemler için
- **pandas**: Veri işleme için
- **matplotlib**: Görselleştirme için

## 📁 Veri Dosyaları

Proje çalıştırıldığında aşağıdaki dosyaların yüklenmesi gerekmektedir:

- `proteinStructure.fasta`: Protein dizilerini içeren FASTA formatındaki dosya
- `PSSP.xlsx`: Protein yapı verilerini içeren Excel dosyası (opsiyonel)

## 🔬 Metodoloji

### 1. Veri Ön İşleme

- FASTA dosyasından protein dizileri okunur
- Her protein için Helix (Pa), Sheet (Pb) ve Turn (Pt) eğilim skorları hesaplanır
- En yüksek skora sahip sınıf, proteinin etiket sınıfı olarak belirlenir

### 2. Özellik Çıkarımı

- Amino asitler EIIP (Electron-Ion Interaction Potential) değerleri ile kodlanır
- Diziler maksimum uzunluğa kadar padding yapılır

### 3. Model Eğitimi

#### SVM Modeli
- RBF kernel kullanılır
- Olasılık tahminleri etkinleştirilir

#### 1D-CNN Modeli
- İki Conv1D katmanı (64 ve 128 filtre)
- MaxPooling katmanları
- Dense katmanlar
- 30 epoch eğitim

### 4. Değerlendirme Metrikleri

- **Accuracy**: Genel doğruluk oranı
- **Precision**: Kesinlik
- **Recall**: Duyarlılık
- **MCC**: Matthews Correlation Coefficient
- **Kappa**: Cohen's Kappa
- **AUC**: ROC eğrisi altındaki alan

## 📊 Sonuçlar

Proje, her iki modelin performansını karşılaştırarak sonuçları görselleştirir:

- Confusion Matrix grafikleri
- ROC eğrileri
- Metrik karşılaştırma grafikleri
- Eğitim geçmişi grafikleri (Loss ve Accuracy)

## 🚀 Kullanım

1. Gerekli kütüphaneleri yükleyin:
```python
!pip install biopython scikit-learn tensorflow openpyxl
```

2. Veri dosyalarını yükleyin (Google Colab kullanıyorsanız `files.upload()` ile)

3. Notebook'u hücre hücre çalıştırın

4. Sonuçları inceleyin

## 📝 Notlar

- Veri seti küçük olduğu için model performansları sınırlı olabilir
- Daha iyi sonuçlar için daha büyük veri setleri önerilir
- Model hiperparametreleri veri setine göre ayarlanabilir

## 🔧 Model Yapıları

### SVM
- Kernel: RBF
- Probability: True

### 1D-CNN
- Conv1D(64, 3) → MaxPooling1D(2)
- Conv1D(128, 3) → MaxPooling1D(2)
- Flatten
- Dense(64)
- Dense(num_classes, softmax)

## 📈 Performans

Model performansları veri setine ve eğitim parametrelerine bağlı olarak değişiklik gösterebilir. Detaylı sonuçlar notebook çıktılarında görülebilir.

## 👤 Geliştirici

Bu proje biyoinformatik ve makine öğrenmesi alanlarında protein yapı tahmini için geliştirilmiştir.




# Proje Dosyaları ve Açıklamaları

## 📘 Notebook ve Python Script
### 🧪 bioenformatik.ipynb
Projenin tüm adımlarını içeren ana notebook: FASTA okuma, Chou–Fasman analizi, EIIP özellik çıkarımı, SVM & CNN modelleri, metrik hesaplama ve tüm grafiklerin üretimi.

### 🧬 bioenformatik.py
Notebook’un script formatı. Komut satırından çalıştırılabilir.

---

## 📄 Veri Dosyaları
### proteinStructure.fasta
Protein aminoasit dizilerinin bulunduğu FASTA dosyası.

### eiip_dataset.xlsx
EIIP değerleri ile sayısal olarak kodlanmış veri seti.

### chou_fasman_results.xlsx
Chou–Fasman eğilim skorları ve tahmin edilen sınıfları içerir.

---

## 🧠 CNN Modeli Çıktıları
### cnn_accuracy_plot.png
CNN eğitim doğruluk grafiği.

### cnn_loss_plot.png
CNN eğitim kayıp grafiği.

### cnn_confusion_matrix.png
CNN confusion matrix grafiği.

### cnn_roc_curves.png
CNN ROC eğrileri grafiği.

### cnn_report.txt
CNN classification report çıktısı.

---

## 🧠 SVM Modeli Çıktıları
### svm_confusion_matrix.png
SVM confusion matrix grafiği.

### svm_metrics_plot.png
SVM ve CNN metrik karşılaştırma grafiği.

### svm_report.txt
SVM classification report çıktısı.

