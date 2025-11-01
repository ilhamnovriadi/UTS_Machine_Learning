# Deskripsi Dataset: Bank Marketing

- Sumber dataset: `https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset`
- Lokasi file di repo: `data/bank_marketing.csv`
- Digunakan oleh notebook: `Machine-Learning-UTS-IlhamNovriadi.ipynb`

## Ringkasan

- Tujuan: Memprediksi apakah seorang nasabah akan membuat `deposit` berjangka (binary classification: `yes`/`no`).
- Ukuran data: 11.162 baris, 17 kolom.
- Target: `deposit` (label tujuan, nilai `yes` atau `no`).
- Distribusi target (dari EDA pada notebook): `no = 5.873`, `yes = 5.289` (sekitar 52.6% vs 47.4%, relatif seimbang).
- Nilai hilang: Tidak terdeteksi pada seluruh kolom (0 missing per kolom).

## Fitur dan Penjelasan Kolom

- `age`: Usia nasabah (integer).
- `job`: Jenis pekerjaan (kategori, mis. `admin.`, `technician`, `services`, dll.).
- `marital`: Status pernikahan (kategori: `single`, `married`, `divorced`).
- `education`: Tingkat pendidikan (kategori: `primary`, `secondary`, `tertiary`, `unknown`).
- `default`: Ada kredit macet? (kategori: `yes`/`no`).
- `balance`: Saldo rata-rata tahunan dalam rekening (integer, satuan mata uang bank).
- `housing`: Memiliki kredit perumahan? (kategori: `yes`/`no`).
- `loan`: Memiliki pinjaman pribadi? (kategori: `yes`/`no`).
- `contact`: Jenis kontak (kategori: `cellular`, `telephone`, `unknown`).
- `day`: Hari dalam sebulan saat kontak terakhir (integer).
- `month`: Bulan saat kontak terakhir (kategori: `jan`–`dec`).
- `duration`: Durasi panggilan terakhir, dalam detik (integer).
- `campaign`: Jumlah kontak selama kampanye berjalan (integer).
- `pdays`: Hari sejak kontak terakhir dalam kampanye sebelumnya (integer; `-1` berarti belum pernah dihubungi).
- `previous`: Jumlah kontak dalam kampanye sebelumnya (integer).
- `poutcome`: Hasil kampanye sebelumnya (kategori: `success`, `failure`, `other`, `unknown`).
- `deposit`: Target—apakah nasabah membuat deposit berjangka? (kategori: `yes`/`no`).

## Tipe Data

- Numerik: `age`, `balance`, `day`, `duration`, `campaign`, `pdays`, `previous` (7 kolom).
- Kategorikal: `job`, `marital`, `education`, `default`, `housing`, `loan`, `contact`, `month`, `poutcome`, `deposit` (10 kolom).

## Catatan Data & Pra-Pemrosesan

- `pdays = -1` menandakan nasabah belum pernah dihubungi pada kampanye sebelumnya.
- `contact = unknown` dan beberapa nilai kategori `unknown` umum pada dataset ini.
- Langkah pra-pemrosesan yang lazim:
  - Encoding kategori (mis. One-Hot Encoding untuk kolom kategorikal).
  - Opsi normalisasi/standarisasi untuk fitur numerik (terutama `duration`, `balance`).
  - Pemisahan data latih/uji (mis. 80/20).
  - Evaluasi dengan metrik klasifikasi: akurasi, precision, recall, F1, ROC-AUC.
