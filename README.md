
# Proyek Akhir : Menyelesaikan Permasalahan Jaya Jaya Institut

## Business Understanding

Jaya Jaya Institut merupakan salah satu institusi pendidikan perguruan yang telah berdiri sejak tahun 2000. Hingga saat ini ia telah mencetak banyak lulusan dengan reputasi yang sangat baik.

## Permasalahan Bisnis

Meskipun telah berkembang menjadi perguruan tinggi yang baik, Akan tetapi terdapat banyak juga siswa yang tidak menyelesaikan pendidikannya alias dropout. Jumlah dropout yang tinggi ini tentunya menjadi salah satu masalah yang besar untuk sebuah institusi pendidikan. Oleh karena itu, Jaya Jaya Institut ingin mendeteksi secepat mungkin siswa yang mungkin akan melakukan dropout sehingga dapat diberi bimbingan khusus.

## Cakupan Proyek

Dalam proyek ini, kita berkomitmen untuk menggali lebih dalam 🔍. Kita akan mengidentifikasi berbagai faktor yang berkontribusi terhadap tingginya tingkat dropout 📉 melalui pembuatan business dashboard 📊 dan model yan akan membantu memantau faktor-faktor tersebut. Dengan menggunakan data mahasiswa dan alat seperti Looker Studio dan bahasa pemrograman Python serta streamlit, kita akan menciptakan visualisasi dan pengembangan model machine learning ke dalam proyek ini.

## Persiapan
Sumber data: [Dicoding Dataset](https://github.com/dicodingacademy/dicoding_dataset/blob/main/students_performance/data.csv) <br>

Proyek ini dibuat melalui Google Colaboratory (Google Colab).
```
[https://colab.research.google.com/drive/16ZtTSCnY4v9akQoj2ZrQx1CAyNQmh13y?usp=sharing](https://colab.research.google.com/drive/1JUROGxz-SEhfNDTvRKG8q3cyQFTq53E4?usp=sharing)
```
Namun jika tidak menggunakan colab anda bisa menggunakan Jupyter Notebook, ikuti langkah setup environment dibawah ini:
```
pip install streamlit, pandas, joblib, scikit-learn, numpy
```

### 🧰 Struktur File

| File | Deskripsi |
|------|-----------|
| `app.py` | Script utama Streamlit untuk menjalankan aplikasi prediksi dropout mahasiswa. |
| `notebook.ipynb` | Notebook eksplorasi, pembersihan data, dan pelatihan model ML. |
| `finaldata.csv` | Dataset final yang telah dibersihkan dan diproses. |
| `encoder.joblib` | Encoder untuk kolom-kolom kategori (hasil dari LabelEncoder). |
| `outlier_handler_pipeline.joblib` | Pipeline khusus untuk menangani outlier menggunakan metode IQR. |
| `random_forest_pipeline.joblib` | Model random forest yang digunakan untuk deploy. |
| `requirements.txt` | File dependensi untuk menjalankan aplikasi ini. |
| `README.md` | Dokumentasi proyek ini (file ini). |
| `Jaya-Jaya_University_Analytics_Dashboard.png` | Preview Dashboard. |

## Business Dashboard

### 📊 Penjelasan Dashboard

Dashboard yang disusun berperan sebagai alat bantu visualisasi untuk memantau performa dan risiko dropout mahasiswa. Dibuat menggunakan Streamlit dan Google Looker Studio, dashboard ini menyajikan visualisasi dari:

- **Faktor demografis**: status pernikahan, usia, jenis kelamin, dan kebangsaan.
- **Faktor ekonomi keluarga**: pekerjaan orang tua, utang, status pembayaran kuliah.
- **Faktor akademik**: jumlah mata kuliah yang diambil, nilai, dan kehadiran.
- **Faktor eksternal**: tingkat pengangguran, inflasi, dan PDB.

Dashboard dirancang untuk membantu pihak kampus dalam pengambilan keputusan cepat berbasis data terhadap mahasiswa yang berisiko dropout.

#### Link Dashboard:
```
https://lookerstudio.google.com/reporting/8280cfea-3818-4672-87b8-f2c683c4055e
```

##### Dashboard Preview

![Dashboard](https://github.com/user-attachments/assets/ba09b29e-37db-4c11-bb8c-385897d785ed)

## Menjalankan Sistem Machine Learning

### 📦 Cara Menjalankan Aplikasi

1. **Kloning repositori ini dan buka terminal**:
   ```bash
   git clone <url-repo>
   cd <folder>
   ```

2. **Buat virtual environment baru dan aktifkan**:
   ```bash
   conda create --name dropout-predict python=3.10
   conda activate dropout-predict
   ```

3. **Install dependensi**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Jalankan aplikasi Streamlit**:
   ```bash
   streamlit run app.py
   ```

### 📈 Alur Kerja Proyek

1. **Data Understanding**
   - Eksplorasi dataset: deteksi missing values, outlier, dan imbalance.
   - Transformasi kolom kategorikal menjadi deskriptif dan bertipe `category`.

2. **Data Preparation**
   - Outlier ditangani menggunakan metode IQR melalui `OutlierHandler`.
   - Kolom kategorikal di-encode menggunakan `LabelEncoder`.
   - Data dibersihkan dan disimpan ke `finaldata.csv`.

3. **Modeling**
   - Model yang digunakan: `RandomForestClassifier`.
   - Data di-resample menggunakan SMOTE untuk mengatasi imbalance.
   - Pipeline pelatihan dibuat dan disimpan untuk digunakan di aplikasi.

4. **Deployment**
   - Aplikasi dibangun dengan Streamlit menggunakan `app.py`.
   - Preprocessing diintegrasikan agar prediksi real-time dapat dilakukan dari form input user.
  
Jika Anda lebih memilih untuk menjalankan aplikasi melalui link, Anda dapat mengaksesnya di [Jaya Jaya Institute Streamlit App](https://bpds-v2-4zxbytswecfwaujm2bfep7.streamlit.app/)

## Conclusion

- Mahasiswa dengan **status keuangan tidak stabil**, **beban mata kuliah tinggi**, atau **asal dari daerah dengan tingkat pengangguran tinggi** memiliki risiko dropout lebih tinggi.
- **Mahasiswa daytime** memiliki kecenderungan dropout lebih besar dibanding evening class.
- Perlu adanya intervensi dini terhadap mahasiswa dengan nilai awal (admission grade) yang rendah.

## Rekomendasi Action Items

1. Bimbingan akademik dan remedial untuk mahasiswa dengan nilai rendah.
2. Program bantuan keuangan atau beasiswa bagi mahasiswa rentan.
3. Monitoring sistem keuangan untuk menghindari keterlambatan pembayaran.
4. Konseling psikologis dan karier bagi mahasiswa yang memiliki tekanan sosial tinggi.
5. Penyempurnaan kurikulum dan pengawasan beban studi secara berkala.
