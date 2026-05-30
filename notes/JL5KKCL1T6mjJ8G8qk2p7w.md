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
## 8. Pelatihan Model Logistic Regression

Setelah data berhasil diproses menjadi fitur numerik menggunakan TF-IDF, langkah berikutnya adalah melatih model Logistic Regression.

Model dilatih menggunakan data latih yang telah dibagi sebelumnya dengan parameter `class_weight='balanced'` untuk membantu menangani ketidakseimbangan jumlah data pada setiap kelas sentimen.

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight='balanced')

model.fit(X_train, y_train)
```
![](https://g0v.hackmd.io/_uploads/B1lP6bQdlGg.png)



# 9. Evaluasi Model
Setelah model selesai dilatih, dilakukan evaluasi untuk mengukur kemampuan model dalam melakukan klasifikasi sentimen.
### 9.1 Accuracy

Accuracy digunakan untuk mengukur persentase prediksi yang benar dibandingkan seluruh data uji.

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)

print("Akurasi:", accuracy)
```
![](https://g0v.hackmd.io/_uploads/BJxivfmuxfg.png)
Model memperoleh nilai akurasi sebesar 84%, yang menunjukkan bahwa sebagian besar data uji berhasil diklasifikasikan dengan benar.




### 9.2 Classification Report

Classification Report digunakan untuk melihat nilai precision, recall, dan F1-score pada setiap kelas sentimen.

```python
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))
```
![](https://g0v.hackmd.io/_uploads/SJlYLXmdgMx.png)
Berdasarkan hasil evaluasi, kelas sentimen positif memiliki performa terbaik dengan nilai precision dan F1-score yang tinggi. Hal ini dipengaruhi oleh dominasi jumlah data sentimen positif dalam dataset.



### 9.3 Confusion Matrix

Confusion Matrix digunakan untuk melihat jumlah prediksi yang benar maupun salah pada setiap kelas sentimen.

```python
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

print(cm)
```
![](https://g0v.hackmd.io/_uploads/ByxpkN7uezx.png)
Hasil confusion matrix menunjukkan bahwa sebagian besar data sentimen positif berhasil diprediksi dengan benar oleh model. Namun masih terdapat beberapa kesalahan klasifikasi pada kelas sentimen negatif dan netral karena jumlah datanya relatif lebih sedikit.


# 10. Hasil Output

Setelah model dievaluasi, dilakukan pengujian menggunakan beberapa kalimat baru untuk melihat kemampuan model dalam memprediksi sentimen.

```python
contoh = [
    "barang bagus banget",
    "pengiriman lama dan buruk",
    "packing rapi dan cepat",
    "produk rusak parah"
]

contoh_tfidf = tfidf.transform(contoh)

prediksi = model.predict(contoh_tfidf)

for review, hasil in zip(contoh, prediksi):
    print(review, "->", hasil)
```
![](https://g0v.hackmd.io/_uploads/S1gjs4QOgfg.png)
Hasil pengujian menunjukkan bahwa model mampu mengidentifikasi sentimen positif dan negatif pada kalimat baru dengan baik. Kalimat yang mengandung kata-kata bernada positif diprediksi sebagai sentimen positif, sedangkan kalimat bernada negatif diprediksi sebagai sentimen negatif.


# 11. Kesimpulan

Pada proyek ini berhasil dibangun model analisis sentimen ulasan produk Tokopedia menggunakan metode Logistic Regression dan representasi fitur TF-IDF.

Model memperoleh nilai akurasi sebesar 84% pada data uji. Hasil evaluasi menunjukkan bahwa model mampu mengklasifikasikan sentimen positif dengan baik.

Pengujian pada data baru juga menunjukkan bahwa model mampu membedakan sentimen positif dan negatif secara cukup akurat.
# 12. Kendala dan Solusi

| Kendala | Solusi |
|----------|----------|
| Distribusi data tidak seimbang | Menggunakan class_weight='balanced' |
| Data teks mengandung karakter yang tidak diperlukan | Melakukan preprocessing teks |
| Data teks tidak dapat langsung digunakan model | Menggunakan TF-IDF |
# 13. Link Kodingan

Notebook Google Colab:

[Google Colab Notebook](https://colab.research.google.com/drive/1EjrscXf7Cp54pIejiy58LQ67CCM7odpi?usp=sharing)