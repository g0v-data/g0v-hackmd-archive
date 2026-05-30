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
## 5. Preprocessing Data

Pada tahap ini dilakukan beberapa proses preprocessing untuk mempersiapkan data teks sebelum digunakan dalam proses pelatihan model machine learning.
### 5.1 Pembuatan Label Sentimen

Label sentimen dibuat berdasarkan nilai rating produk. Rating 4 dan 5 dikategorikan sebagai sentimen positif, rating 1 dan 2 sebagai sentimen negatif, sedangkan rating 3 sebagai sentimen netral.

```python
def sentiment_label(rating):
    if rating >= 4:
        return "positif"
    elif rating <= 2:
        return "negatif"
    else:
        return "netral"

df['sentiment'] = df['rating'].apply(sentiment_label)
```
![](https://g0v.hackmd.io/_uploads/ry7QfGdgGl.png)
### 5.2 Distribusi Label Sentimen

Distribusi rating pada dataset diperiksa untuk mengetahui sebaran data yang digunakan.

```python
df['rating'].value_counts()
```
![](https://g0v.hackmd.io/_uploads/SyMyQz_gGe.png)
Terlihat bahwa sebagian besar data memiliki rating tinggi, sehingga mayoritas data termasuk ke dalam kategori sentimen positif.
### 5.3 Case Folding

Case folding dilakukan untuk mengubah seluruh huruf menjadi huruf kecil agar penulisan kata menjadi konsisten.

```python
df['text'] = df['text'].str.lower()
```
![](https://g0v.hackmd.io/_uploads/BklSUXzOlGe.png)
Setelah proses case folding, seluruh teks berhasil dikonversi menjadi huruf kecil.
### 5.4 Cleaning Text

Cleaning text dilakukan untuk menghapus karakter selain huruf, seperti angka dan tanda baca.

```python
import re

df['text'] = df['text'].apply(
    lambda x: re.sub(r'[^a-zA-Z\s]', '', str(x))
)
```
![](https://g0v.hackmd.io/_uploads/SyfsQMdgfl.png)
Karakter yang tidak diperlukan berhasil dihapus sehingga teks menjadi lebih bersih untuk proses ekstraksi fitur.
## 6. Ekstraksi Fitur TF-IDF

Metode TF-IDF digunakan untuk mengubah data teks menjadi representasi numerik yang dapat diproses oleh algoritma machine learning.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer()

X = tfidf.fit_transform(df['text'])

y = df['sentiment']
```
TF-IDF menghasilkan representasi fitur numerik berdasarkan tingkat kepentingan kata dalam dokumen.
## 7. Pembagian Data Latih dan Data Uji

Dataset dibagi menjadi data latih dan data uji dengan perbandingan 80:20.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```
![](https://g0v.hackmd.io/_uploads/rJlvsNfOxMg.png)
