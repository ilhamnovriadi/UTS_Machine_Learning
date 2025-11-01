# Hasil dan Pembahasan

- Proyek: UTS Machine Learning — Bank Marketing
- Notebook: `Machine-Learning-UTS-IlhamNovriadi.ipynb`
- Dataset: Bank Marketing (Kaggle/UCI), file: `data/bank_marketing.csv`

## Ringkasan Hasil
- Model terbaik: Logistic Regression.
- Metrik evaluasi yang diperoleh pada notebook:
  - Akurasi: ~84%
  - Precision: ~84%
  - Recall: ~84%
  - F1-score: ~84%
  - ROC-AUC: ~0.92
- Distribusi target (EDA): `no = 5.873`, `yes = 5.289` (relatif seimbang; ±52.6% vs 47.4%).
- Nilai hilang: Tidak ditemukan (0 missing di seluruh kolom).

## Metodologi Singkat
- EDA: Mengecek struktur data (`shape = (11162, 17)`), tipe kolom (7 numerik, 10 kategorikal), dan distribusi target.
- Pra-pemrosesan yang lazim untuk dataset ini:
  - Encoding kategori (mis. One-Hot Encoding untuk `job`, `marital`, `education`, `default`, `housing`, `loan`, `contact`, `month`, `poutcome`).
  - Opsi normalisasi/standarisasi fitur numerik (terutama `balance`, `duration`).
  - Pemisahan data latih-uji (mis. 80/20) untuk evaluasi yang adil.
- Pemodelan: Logistic Regression untuk klasifikasi biner (`deposit` yes/no).

## Pembahasan
- Kinerja model:
  - Akurasi dan F1 ~84% menunjukkan keseimbangan baik antara precision dan recall.
  - ROC-AUC ~0.92 mengindikasikan kemampuan pemisahan kelas yang kuat di berbagai ambang batas.
- Threshold: Hasil dilaporkan pada threshold default 0.5. Jika tujuan bisnis membutuhkan lebih banyak konversi (menekan false negative), menaikkan recall dengan menurunkan threshold bisa dipertimbangkan, dengan trade-off peningkatan false positive.
- Fitur `duration` dan potensi kebocoran informasi:
  - Pada Bank Marketing, `duration` (durasi panggilan terakhir) sering sangat informatif, namun bisa dianggap tidak tersedia sebelum panggilan dilakukan. 
  - Disarankan melakukan eksperimen kedua tanpa `duration` untuk menilai performa yang lebih realistis sebelum kontak.
- Implikasi bisnis:
  - Dengan metrik yang solid, model dapat membantu memprioritaskan nasabah yang berpotensi melakukan deposit berjangka.
  - Kebijakan outreach dapat dioptimalkan: fokus pada segmen dengan skor prediksi tinggi untuk efisiensi kampanye.

## Validasi dan Evaluasi
- Disarankan menambahkan k- fold cross-validation untuk mengestimasi stabilitas performa di berbagai split.
- Tinjau confusion matrix untuk melihat pola kesalahan (mis. apakah banyak false positive atau false negative) guna menyesuaikan threshold kebijakan.
- Pertimbangkan kalibrasi probabilitas (mis. Platt scaling atau isotonic) agar skor lebih representatif.

## Rekomendasi Lanjutan
- Coba model alternatif: Random Forest, XGBoost/LightGBM, SVM, dan Naive Bayes sebagai pembanding.
- Hyperparameter tuning (GridSearch/CV) pada Logistic Regression dan model lain untuk mencari konfigurasi optimal.
- Analisis interpretabilitas: koefisien Logistic Regression, Permutation Importance, atau SHAP untuk memahami kontribusi fitur.
- Penanganan nilai kategori `unknown` (mis. treat sebagai kategori sendiri vs imputasi).
- Pembuatan pipeline terautomasi untuk pra-pemrosesan + model agar reproducible.

## Cara Reproduksi
- Pastikan jalur file dataset sesuai dengan repo: gunakan `data/bank_marketing.csv`.
- Pada notebook saat ini, pembacaan data menggunakan jalur absolut:
  - `df = pd.read_csv("/Volumes/IDEKU/University/Code/data/bank_marketing.csv")`
  - Disarankan mengubah ke: `df = pd.read_csv("data/bank_marketing.csv")` agar konsisten dengan struktur repo.
- Perangkat lunak: Python 3.x, dengan pustaka umum seperti `pandas`, `numpy`, `matplotlib`, `seaborn`, dan `scikit-learn`.
- Jalankan notebook: buka `Machine-Learning-UTS-IlhamNovriadi.ipynb` di Jupyter/Lab dan eksekusi sel berurutan.

## Kesimpulan
- Logistic Regression memberikan performa terbaik pada eksperimen di notebook dengan metrik kuat (Akurasi/F1 ~84%, ROC-AUC ~0.92).
- Untuk penggunaan operasional, pertimbangkan eksklusi `duration`, penyesuaian threshold sesuai tujuan bisnis, dan validasi dengan cross-validation serta kalibrasi.

## Catatan
- Dataset berasal dari kampanye telemarketing; pertimbangan etika dan privasi penting saat penggunaan prediksi.
- Performa bisa berbeda jika diterapkan pada kampanye dan periode berbeda (concept drift). Monitor dan retrain model secara berkala.