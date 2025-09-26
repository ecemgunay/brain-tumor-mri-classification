# Brain Tumor MRI Classification — Akbank DL Bootcamp

Bu repo, Akbank Derin Öğrenme Bootcamp (Eylül 2025) kapsamında geliştirilmiştir.  
Amaç, **MRI görüntülerinden beyin tümörünü sınıflandırmak** için CNN tabanlı bir model oluşturmaktır.  

---

## Giriş
Projede kullanılan veri seti: [Brain Tumor MRI Dataset (Kaggle)](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)  
- **Toplam Görüntü:** 7.022  
- **Sınıflar:** `glioma`, `meningioma`, `notumor`, `pituitary`  

Model olarak **EfficientNetB0** (ImageNet ağırlıklarıyla transfer learning) kullanılmıştır.  
- Data Augmentation → EfficientNetB0 → Dropout → Dense (softmax, 4 sınıf)  
- Optimizer: Adam (lr=1e-3, fine-tuning aşamasında 1e-4)  
- Loss: Categorical Crossentropy  
- Metric: Accuracy  

---

## Metrikler
**Eğitim Süreci:**  
- Faz 1 (base frozen): 12 epoch  
- Faz 2 (fine-tuning, son katmanlar serbest): 6 epoch  
- Toplam eğitim: 18 epoch  
- Donanım: Kaggle GPU T4 ×2  

**Sonuçlar:**  
- Validation Accuracy (en iyi): ~0.944  
- Test Accuracy: **0.93**  
- Macro F1: **0.92**  

**Sınıf Bazında Performans (Precision / Recall / F1):**  
- Glioma: 0.92 / 0.88 / 0.90  
- Meningioma: 0.89 / 0.84 / 0.86  
- No Tumor: 0.97 / 0.98 / 0.97  
- Pituitary: 0.91 / 1.00 / 0.95  

**Eğitim Grafiklerinden Örnek:**  
![Accuracy](images/accuracy.png)  
![Loss](images/loss.png)  

**Confusion Matrix:**  
![Confusion Matrix](images/confusion_matrix.png)  

**Grad-CAM Örnekleri:**  
Modelin karar verirken tümör bölgelerine odaklandığı görülmektedir.  
![Grad-CAM 1](images/gradcam1.png)  
![Grad-CAM 2](images/gradcam2.png)  
![Grad-CAM 3](images/gradcam3.png)  

---

## Ekler
Bu projede **deployment** yapılmamıştır.  
İleride Streamlit veya Flask tabanlı bir arayüz geliştirilerek modelin web üzerinde demo edilmesi mümkündür.  

---

## Sonuç ve Gelecek Çalışmalar
Bu proje ile Brain Tumor MRI veri seti üzerinde EfficientNetB0 modeli kullanılarak yüksek doğruluk oranı elde edilmiştir (**%93 test accuracy**).  
Model özellikle **glioma ↔ meningioma** ayrımında zorlanırken, **notumor** ve **pituitary** sınıflarında çok yüksek başarı sağlamıştır.  

**Gelecek geliştirmeler:**  
- Daha büyük modeller (EfficientNetB1+, ResNet50, Vision Transformer) denenebilir.  
- Data augmentation stratejileri çeşitlendirilebilir.  
- Hasta bazlı split ile klinik olarak daha doğru sonuçlar alınabilir.  
- Streamlit arayüzü ile demo hazırlanabilir.  

---

## Linkler
- [Kaggle Notebook Linki](https://www.kaggle.com/code/eceemgunay/brain-tumor-mri-classification-akbank-dl-bootcam)  
