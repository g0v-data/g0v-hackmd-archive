## 1. Deskripsi Proyek

Proyek ini bertujuan untuk membangun model machine learning untuk melakukan analisis sentimen pada ulasan produk Tokopedia.

Model yang digunakan adalah Logistic Regression dengan representasi fitur TF-IDF untuk mengklasifikasikan ulasan ke dalam kategori sentimen positif, netral, dan negatif.
## 2. Tujuan Proyek

Tujuan dari proyek ini adalah:

- Melakukan analisis sentimen pada ulasan produk Tokopedia.
- Melakukan preprocessing teks agar dapat digunakan oleh model machine learning.
- Mengubah data teks menjadi representasi numerik menggunakan TF-IDF.
- Membangun model Logistic Regression untuk klasifikasi sentimen.
- Mengevaluasi performa model menggunakan metrik evaluasi seperti accuracy, precision, recall, dan F1-score.

## 3. Dataset

Dataset yang digunakan adalah dataset ulasan produk Tokopedia yang telah diberi label sentimen.

| Informasi | Keterangan |
|------------|------------|
| Nama Dataset | Tokopedia Product Reviews |
| Jumlah Data | 5000 |
| Jumlah Fitur | 9 |
| Target | sentiment |
| Jenis Task | Klasifikasi Sentimen |
## 4. Exploratory Data Analysis (EDA)

Pada tahap ini dilakukan analisis awal terhadap dataset untuk memahami karakteristik data yang digunakan.
### Ukuran Dataset

Kode berikut digunakan untuk melihat jumlah baris dan kolom pada dataset:

```python
df.shape
```
![](https://g0v.hackmd.io/_uploads/rJn8pNPefx.png)
Berdasarkan hasil tersebut, dataset memiliki 5000 baris data dan 9 kolom fitur.
### Nama Kolom Dataset

Kode berikut digunakan untuk melihat nama kolom yang tersedia:

```python
df.columns
```
![](https://g0v.hackmd.io/_uploads/BJlYTRNwlfl.png)
Dataset memiliki beberapa kolom yang berisi informasi ulasan produk, rating, kategori produk, serta informasi identitas produk dan toko.
### Pemeriksaan Missing Value

Kode berikut digunakan untuk memeriksa apakah terdapat data yang kosong:

```python
df.isnull().sum()
```
![](https://g0v.hackmd.io/_uploads/HyuZkSwxzl.png)
Hasil pemeriksaan menunjukkan bahwa seluruh kolom memiliki nilai missing value sebesar 0. Dengan demikian dataset tidak memerlukan proses penanganan data kosong sebelum dilakukan preprocessing dan pelatihan model.

