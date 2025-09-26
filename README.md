# 🧠 Brain Tumor MRI Classification — Akbank DL Bootcamp

Bu repo, **Akbank Derin Öğrenme Bootcamp (Eylül 2025)** kapsamında geliştirilmiştir.  
Amaç, **MRI beyin görüntülerinden tümör tiplerini** (glioma, meningioma, notumor, pituitary) derin öğrenme tabanlı bir model ile sınıflandırmaktır.

---

## 📌 Proje Özeti
- **Veri Seti:** [Brain Tumor MRI Dataset (Kaggle)](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)  
  > Not: Kaggle lisans koşulları nedeniyle veri seti bu repoda paylaşılmamıştır.  
- **Model:** EfficientNetB0 (ImageNet transfer learning)  
- **Mimari:** Data Augmentation → EfficientNetB0 → Dropout → Dense (Softmax, 4 sınıf)  
- **Optimizer:** Adam (lr=1e-3; fine-tuning aşamasında 1e-4)  
- **Loss:** Categorical Crossentropy  
- **Metric:** Accuracy  

---

## 📊 Eğitim Süreci
- Faz 1 (base frozen): 12 epoch  
- Faz 2 (fine-tuning, son katmanlar serbest): 6 epoch  
- **Toplam:** 18 epoch  
- **Donanım:** Kaggle GPU T4 ×2  

---

## ✅ Sonuçlar
- **Validation Accuracy (en iyi):** ~0.944  
- **Test Accuracy:** ~0.93  
- **Macro F1:** ~0.92  

**Sınıf Bazında Precision / Recall / F1:**  
- Glioma → 0.92 / 0.88 / 0.90  
- Meningioma → 0.89 / 0.84 / 0.86  
- No Tumor → 0.97 / 0.98 / 0.97  
- Pituitary → 0.91 / 1.00 / 0.95  

📌 Eğitim eğrileri, confusion matrix ve Grad-CAM görselleri notebook çıktıları içinde bulunmaktadır.

---

## 🔮 Gelecek Çalışmalar
- Daha büyük modeller (EfficientNetB1+, ResNet50, Vision Transformer) denenebilir.  
- Data augmentation stratejileri çeşitlendirilebilir.  
- Hasta bazlı split ile klinik olarak daha doğru sonuçlar alınabilir.  
- Streamlit arayüzü ile web demo hazırlanabilir.  

---

## 🔗 Linkler
- Kaggle Notebook: [Brain Tumor MRI Classification — Akbank DL Bootcamp](https://www.kaggle.com/code/eceemgunay/brain-tumor-mri-classification-akbank-dl-bootcam)  
