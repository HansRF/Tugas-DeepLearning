# Klasifikasi Citra Rock-Paper-Scissors

Notebook ini membandingkan dua model Neural Network dense dan tiga model CNN untuk mengklasifikasikan gambar menjadi `rock`, `paper`, atau `scissors`. Eksperimen dijalankan di Google Colab; seluruh metrik dihitung ketika notebook dijalankan dan tidak berisi skor yang dibuat sebelumnya.

## File proyek

- [Klasifikasi_Citra_Rock_Paper_Scissors.ipynb](Klasifikasi_Citra_Rock_Paper_Scissors.ipynb): notebook eksperimen dan evaluasi.

## Menjalankan di Google Colab

1. Buka [Google Colab](https://colab.research.google.com/).
2. Pilih **File → Upload notebook**, lalu unggah file `.ipynb` dari proyek ini.
3. Jika GPU tersedia, pilih **Runtime → Change runtime type → T4 GPU**. GPU bersifat opsional, tetapi dapat mempercepat pelatihan.
4. Pilih **Runtime → Run all** untuk menjalankan semua sel dari atas ke bawah. Setujui prompt akses atau instalasi yang muncul.
5. Tunggu KaggleHub mengunduh dataset dan semua model selesai dilatih. Waktu proses bergantung pada ketersediaan GPU dan beban Colab.

> Colab memerlukan koneksi internet untuk mengunduh paket dan dataset.

## Akses dataset Kaggle

Notebook mengunduh dataset `drgfreeman/rockpaperscissors` menggunakan KaggleHub. Untuk dataset publik, unduhan dapat berjalan tanpa autentikasi. Jika Kaggle meminta autentikasi:

1. Unduh token API `kaggle.json` dari pengaturan akun Kaggle.
2. Unggah file tersebut ke sesi Colab melalui panel **Files** di sisi kiri.
3. Jalankan sel berikut sebelum sel pengunduhan dataset:

```python
from pathlib import Path
import os

Path.home().joinpath(".kaggle").mkdir(exist_ok=True)
!cp /content/kaggle.json ~/.kaggle/kaggle.json
!chmod 600 ~/.kaggle/kaggle.json
```

Jangan masukkan `kaggle.json` atau kredensial Kaggle ke repository publik. File yang diunggah ke sesi Colab hanya tersedia selama sesi tersebut.

## Hasil yang ditampilkan

Notebook membagi data secara stratified menjadi 70% data latih, 15% validasi, dan 15% pengujian. Setelah pelatihan, notebook menampilkan akurasi dan loss pada data uji, classification report, tabel perbandingan model, grafik, kurva pelatihan, serta confusion matrix model dengan akurasi uji tertinggi. Nilai hasil berbeda sesuai proses pelatihan; gunakan hasil aktual dari sesi Colab.

## Mengunduh model

Notebook menyimpan model terpilih sebagai `model_klasifikasi_rps.keras` di sesi Colab. Untuk mengunduhnya ke komputer, jalankan sel ini setelah sel penyimpanan model:

```python
from google.colab import files
files.download("model_klasifikasi_rps.keras")
```