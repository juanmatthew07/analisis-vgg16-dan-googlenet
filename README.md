# Analisis VGG16 vs GoogLeNet

Proyek ini melakukan analisis komparatif mendalam antara dua arsitektur Convolutional Neural Network (CNN) populer yaitu VGG16 dan GoogLeNet. Kedua model dibangun dari nol menggunakan TensorFlow/Keras dan dilatih pada dataset CIFAR-10 untuk mengevaluasi trade-off antara akurasi dan efisiensi komputasi.

---

## Skenario Eksperimen

Untuk mendapatkan perbandingan yang komprehensif, 4 skenario eksperimen utama dirancang dan dieksekusi:

1.  **Baseline:** Pelatihan dengan data standar CIFAR-10 (32x32) tanpa augmentasi.
2.  **Data Augmentation:** Pelatihan menggunakan augmentasi data (random flip, rotation) untuk menguji generalisasi.
3.  **Data Imbalanced:** Pelatihan pada dataset yang sengaja dibuat tidak seimbang untuk menguji ketahanan model.
4.  **Resized Data:** Pelatihan pada resolusi gambar yang di-upscale (64x64 dan 128x128) untuk menganalisis dampak resolusi input.

---

## Hasil Analisis & Temuan Utama

Analisis dari hasil eksperimen menghasilkan beberapa temuan:

* **Efisiensi vs. Akurasi:**
    * **GoogLeNet** terbukti secara signifikan **4-5x lebih efisien** secara komputasi (waktu latih per epoch jauh lebih cepat) berkat arsitektur Inception module-nya.
    * **VGG16**, meskipun jauh lebih berat, secara konsisten mencapai **akurasi validasi yang sedikit lebih tinggi** di sebagian besar skenario.

* **Dampak Resolusi Input:**
    * Ditemukan bahwa resolusi **64x64** memberikan akurasi optimal (**~78.30%**).
    * Meningkatkan resolusi ke **128x128** secara tak terduga **menurunkan performa** (**~74.51%**).
    * **Hipotesis:** Penurunan ini kemungkinan disebabkan oleh noise yang diperkenalkan selama proses upscaling berlebih dari gambar asli 32x32, yang mengganggu proses pembelajaran fitur.

---

## Tools

* Python
* TensorFlow & Keras
* Pandas 
* NumPy
* Matplotlib 