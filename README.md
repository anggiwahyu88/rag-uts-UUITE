# 🤖 RAG Starter Pack — UTS Data Engineering

> **Retrieval-Augmented Generation** — Sistem Tanya-Jawab Cerdas Berbasis Dokumen

Starter pack ini adalah **kerangka awal** proyek RAG untuk UTS Data Engineering D3/D4.


**Sistem Rekomendasi Pasal UU ITE — Sistem Rekomendasi Pasal UU ITE Berdasarkan Input Kasus**.

Proyek ini adalah implementasi sistem RAG untuk pemenuhan tugas UTS Data Engineering D4. Sistem ini dikembangkan untuk memproses input berupa deskripsi kasus dari pengguna, kemudian mencari dan merekomendasikan pasal-pasal dalam Undang-Undang Informasi dan Transaksi Elektronik (UU ITE) Tahun 2008 yang paling relevan dengan kasus tersebut.

---

## 👥 Identitas Kelompok

| Nama | NIM | Tugas Utama |
|------|-----|-------------|
| Anggi Wahyu Saputra  | 244311003 | Data Engineer         |
| Azza Auliyaul Fitri  | 244311006 | Data Analyst         |
| Prima Afda Mukhlisin  | 244311024 | Project Manager         |

**Topik Domain:** Hukum  
**Stack yang Dipilih:** LangChain  
**LLM yang Digunakan:** Gemini  
**Vector DB yang Digunakan:** ChromaDB

---

## 🗂️ Struktur Proyek

```
rag-uts-kelompok3/
├── chroma_db/
│   └── chroma.sqlite3       # Vector Db
├── data/                    # Dokumen sumber (PDF, Docx)
│   ├── Persoalan-UU-ITE-dan-Pelanggan-Hak-Digital.docx
│   ├── UU Nomor 19 Tahun 2016.pdf          
│   └── uu-ite.pdf           
├── src/
│   ├── indexing.py          # 🔧 Pipeline indexing
│   └── query.py             # 🔧 Pipeline query & retrieval
├── docs/
│   └── arsitektur.png       # 📌 Diagram arsitektur
├── evaluation/
│   └── hasil_evaluasi.xlsx  # 📌 Tabel evaluasi 10 pertanyaan
├── .env.example             # Template environment variables
├── .gitignore
├── requirements.txt
└── README.md
```

---

## ⚡ Cara Menjalankan (Quickstart)

### 1. Clone & Setup

```bash
# Clone repository ini
git clone https://github.com/[username]/rag-uts-kelompok3.git
cd rag-uts-kelompok3

# Buat virtual environment
python -m venv venv
venv\Scripts\activate   

# Install dependencies
pip install -r requirements.txt
```

### 2. Konfigurasi API Key

```bash
# Salin template env
cp .env.example .env

# Edit .env dan isi API key Anda
# JANGAN commit file .env ke GitHub!
```

### 3. Siapkan Dokumen

Letakkan dokumen sumber Anda di folder `data/`:
```bash
cp uu-ite.pdf data/
cp UU Nomor 19 Tahun 2016.pdf data/
cp Persoalan-UU-ITE-dan-Pelanggan-Hak-Digital.docx data/
```

### 4. Jalankan Indexing 

```bash
python src/indexing.py
```

### 5. Jalankan Sistem RAG

```bash

# CLI
python src/query.py
```

---

## 🔧 Konfigurasi

Semua konfigurasi utama ada di `src/config.py` (atau langsung di setiap file):

| Parameter | Default | Keterangan |
|-----------|---------|------------|
| `CHUNK_SIZE` | 1000 | Ukuran setiap chunk teks (karakter) |
| `CHUNK_OVERLAP` | 200 | Overlap antar chunk |
| `TOP_K` | 3 | Jumlah dokumen relevan yang diambil |
| `MODEL_NAME` | Gemini | Nama model LLM yang digunakan |

---

## 📊 Hasil Evaluasi

*(Isi setelah pengujian selesai)*

| # | Pertanyaan | Jawaban Sistem | Jawaban Ideal | Skor (1-5) |
|---|-----------|----------------|---------------|-----------|
| 1 | apa isi pasal 37? | Setiap orang dengan sengaja melakukan perbuatan yang dilarang sebagaimana dimaksud dalam Pasal 27 sampai dengan Pasal 36 di luar wilayah Indonesia terhadap Sistem Elektronik yang berada di wilayah yurisdiksi Indonesia | Setiap Orang dengan sengaja melakukan perbuatan yang dilarang sebagaimana dimaksud dalam Pasal 27 sampai dengan Pasal 36 di luar wilayah Indonesia terhadap Sistem Elektronik yang berada di wilayah yurisdiksi Indonesia | 5 |
| 2 | pasal 17 berisi tentang? | Berdasarkan dokumen tersebut, Pasal 17 mengatur tentang Penyelenggaraan Transaksi Elektronik dengan rincian sebagai berikut:

*   **Pasal 17 ayat (1):** Penyelenggaraan Transaksi Elektronik dapat dilakukan dalam lingkup publik maupun privat.
*   **Pasal 17 ayat (2):** Para pihak yang melakukan Transaksi Elektronik wajib beriktikad baik dalam melakukan interaksi dan/atau pertukaran Informasi Elektronik dan/atau Dokumen Elektronik selama transaksi berlangsung.
*   **Pasal 17 ayat (3):** Ketentuan lebih lanjut mengenai penyelenggaraan Transaksi Elektronik diatur dengan Peraturan Pemerintah. | (1)Penyelenggaraan Transaksi Elektronik dapat dilakukan dalam lingkup publik ataupun privat. (2)Para pihak yang melakukan Transaksi Elektronik sebagaimana dimaksud pada ayat (1) wajib beriktikad baik dalam melakukan interaksi dan/atau pertukaran Informasi Elektronik dan/atau Dokumen Elektronik selama transaksi berlangsung.(3) Ketentuan lebih lanjut mengenai penyelenggaraan Transaksi Elektronik sebagaimana dimaksud pada ayat (1) diatur dengan Peraturan Pemerintah | 5 |
| 3 | Bab 2 membahas tentang? | Berdasarkan dokumen tersebut, **BAB II** membahas tentang **Asas dan Tujuan**. | Bab 2 membahas tentang Asas dan Tujuan | 5 |
| 4 | apa isi pasal 22? | Berdasarkan dokumen yang Anda berikan, isi dari **Pasal 22** adalah sebagai berikut:

1.  **Pasal 22 ayat (1):** Penyelenggara Agen Elektronik tertentu wajib menyediakan fitur pada Agen Elektronik yang dioperasikannya yang memungkinkan pengguna untuk melakukan perubahan informasi yang masih dalam proses transaksi.
2.  **Penjelasan Pasal 22 ayat (1):** Yang dimaksud dengan “fitur” adalah fasilitas yang memberikan kesempatan kepada pengguna Agen Elektronik untuk melakukan perubahan atas informasi yang disampaikannya, contohnya adalah fasilitas pembatalan (*cancel*), edit, dan konfirmasi ulang.
3.  **Pasal 22 ayat (2):** Ketentuan lebih lanjut mengenai penyelenggara Agen Elektronik tertentu tersebut diatur dengan Peraturan Pemerintah. | Pasal 22 Penyelenggara Agen Elektronik tertentu harus menyediakan fitur pada Agen Elektronik yang dioperasikannya yang memungkinkan penggunanya melakukan perubahan informasi yang masih dalam proses transaksi. Ketentuan lebih lanjut mengenai penyelenggara Agen Elektronik tertentu sebagaimana dimaksud pada ayat (1) diatur dengan Peraturan Pemerintah | 5 |
| 5 | berapa banyak pasal di UU Ite? | Berdasarkan dokumen yang diberikan, Undang-Undang ini memiliki total **54 pasal**. Hal ini merujuk pada **Pasal 54** yang merupakan pasal terakhir dalam **BAB XIII** mengenai **Ketentuan Penutup** | 54 Pasal dan 13 Bab  | 5 |
| 6 | Perusahaan A dan Perusahaan B melakukan transaksi bisnis bernilai besar. Mereka sepakat membuat kontrak perjanjian kerja sama, tetapi kontrak tersebut hanya dibuat dalam bentuk dokumen elektronik dan ditandatangani secara elektronik tanpa kertas fisik. Apakah transaksi dan kontrak elektronik tersebut sah dan mengikat secara hukum? | Berdasarkan dokumen Undang-Undang Republik Indonesia Nomor 11 Tahun 2008 yang Anda berikan, transaksi dan kontrak elektronik antara Perusahaan A dan Perusahaan B tersebut adalah **sah dan mengikat secara hukum**, selama memenuhi ketentuan sebagai berikut:

1.  **Keabsahan Kontrak:** Transaksi Elektronik yang dituangkan ke dalam Kontrak Elektronik mengikat para pihak (**Pasal 18 ayat 1**).   
2.  **Keabsahan Dokumen:** Informasi Elektronik dan/atau Dokumen Elektronik merupakan alat bukti hukum yang sah (**Pasal 5 ayat 1**). Dokumen tersebut dinyatakan sah apabila menggunakan Sistem Elektronik sesuai dengan ketentuan yang diatur dalam Undang-Undang ini (**Pasal 5 ayat 3**).
3.  **Kesetaraan dengan Dokumen Tertulis:** Informasi Elektronik dan/atau Dokumen Elektronik dianggap sah dan disetarakan dengan informasi yang berbentuk tertulis atau asli, sepanjang informasi tersebut dapat diakses, ditampilkan, dijamin keutuhannya, dan dapat dipertanggungjawabkan sehingga menerangkan suatu keadaan (**Pasal 6**).
4.  **Kekuatan Tanda Tangan:** Tanda Tangan Elektronik memiliki kekuatan hukum dan akibat hukum yang sah selama memenuhi persyaratan yang telah ditentukan (**Pasal 11 ayat 1**).
5.  **Kewajiban Para Pihak:** Para pihak yang melakukan Transaksi Elektronik wajib beriktikad baik dalam melakukan interaksi dan/atau pertukaran Informasi Elektronik selama transaksi berlangsung (**Pasal 17 ayat 2**). | Pasal 5 (alat bukti sah) dan Pasal 18 (kontrak elektronik mengikat para pihak) | 4 |
| 7 | Setiap Orang yang dengan sengaja dan tanpa hak mendistribusikan dan/atau mentransmisikan dan/atau membuat dapat diaksesnya Informasi Elektronik dan/atau Dokumen Elektronik yang memiliki muatan yang melanggar kesusilaan | Berdasarkan dokumen yang Anda berikan, perbuatan tersebut diatur dalam **Pasal 27 ayat (1)**, yang menyatakan bahwa setiap orang dilarang dengan sengaja dan tanpa hak mendistribusikan dan/atau mentransmisikan dan/atau membuat dapat diaksesnya Informasi Elektronik dan/atau Dokumen Elektronik yang memiliki muatan yang melanggar kesusilaan. | Pasal 27 | 5 |
| 8 | Jika seorang karyawan dengan sengaja dan tanpa hak menjebol sistem pengamanan komputer perusahaan untuk mencuri dokumen rahasia, bagaimana aturan hukum dan larangannya menurut undang-undang ini? | 
Berdasarkan dokumen Undang-Undang Republik Indonesia Nomor 11 Tahun 2008 yang Anda berikan, tindakan karyawan tersebut diatur dan dilarang melalui pasal-pasal berikut:

1.  **Pelanggaran Akses dan Penjebolan Sistem:**
    *   **Pasal 30 ayat (2):** Melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum mengakses komputer dan/atau sistem elektronik dengan tujuan untuk memperoleh Informasi Elektronik dan/atau Dokumen Elektronik.
    *   **Pasal 30 ayat (3):** Melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum mengakses komputer dan/atau sistem elektronik dengan cara apa pun dengan melanggar, menerobos, melampaui, atau **menjebol sistem pengamanan**.
    *   *Catatan:* Berdasarkan Penjelasan **Ayat (3)**, sistem pengamanan adalah sistem yang membatasi atau melarang akses berdasarkan kategorisasi pengguna dan tingkat kewenangan yang ditentukan.

2.  **Pemindahan Dokumen Milik Orang Lain:**
    *   **Pasal 32 ayat (1):** Melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum mengubah, menambah, mengurangi, melakukan transmisi, merusak, menghilangkan, **memindahkan**, atau menyembunyikan Informasi Elektronik dan/atau Dokumen Elektronik milik orang lain atau milik publik.

3.  **Pengungkapan Dokumen Rahasia:**
    *   **Pasal 32 ayat (3):** Mengatur bahwa perbuatan memindahkan atau mengubah dokumen sebagaimana dimaksud pada ayat (1) yang mengakibatkan terbukanya suatu Informasi Elektronik dan/atau Dokumen Elektronik yang **bersifat rahasia** menjadi dapat diakses oleh publik dengan keutuhan data yang tidak sebagaimana mestinya adalah tindakan yang dilarang.

4.  **Dampak Kerugian:**
    *   **Pasal 36:** Melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum melakukan perbuatan sebagaimana dimaksud dalam Pasal 27 sampai dengan Pasal 34 (termasuk akses ilegal dan pemindahan data) yang mengakibatkan **kerugian bagi orang lain**.

5.  **Ketentuan untuk Karyawan/Staf:**
    *   **Pasal 52 ayat (4):** Menjelaskan bahwa setiap perbuatan melawan hukum yang memenuhi unsur dalam Pasal 27 sampai dengan Pasal 37 yang dilakukan oleh korporasi, pengurus, dan/atau **staf** yang memiliki kapasitas untuk melakukan perbuatan tersebut dapat dihukum. | Pasal 30 tentang akses ilegal | 5 |
| 9 | Ada seseorang yang sakit hati, lalu sengaja membuat postingan di media sosial yang isinya menghina dan mencemarkan nama baik mantan atasannya agar dibaca oleh publik. Apakah perbuatan ini dilarang, dan masuk ke dalam pasal berapa? | Berdasarkan dokumen yang Anda berikan, perbuatan tersebut dilarang dan diatur dalam **Pasal 27 ayat (3)**. | Pasal 27 ayat 3 | 5 |
| 10 | Budi membeli laptop bekas, tetapi dia mengedit file PDF bukti transfer bank miliknya. Budi mengubah nominal angkanya dari Rp100.000 menjadi Rp10.000.000 menggunakan aplikasi edit foto, lalu mengirimkannya ke penjual seolah-olah itu adalah bukti transfer yang asli dan sah. Apakah memalsukan dokumen elektronik ini ada aturannya? | ... | Ya, tindakan memalsukan dokumen elektronik tersebut diatur dalam Undang-Undang Republik Indonesia Nomor 11 Tahun 2008 tentang Informasi dan Transaksi Elektronik, khususnya pada pasal-pasal berikut:

1.  **Pasal 35**: Pasal ini secara spesifik melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum melakukan manipulasi, penciptaan, perubahan, penghilangan, atau pengrusakan Informasi Elektronik dan/atau Dokumen Elektronik dengan tujuan agar informasi atau dokumen tersebut **dianggap seolah-olah data yang otentik**. Dalam kasus ini, Budi mengedit nominal angka pada bukti transfer agar dianggap sebagai bukti yang sah/otentik.
2.  **Pasal 32 ayat (1)**: Melarang setiap orang dengan sengaja dan tanpa hak atau melawan hukum dengan cara apa pun **mengubah**, menambah, atau mengurangi suatu Informasi Elektronik dan/atau Dokumen Elektronik milik orang lain atau milik publik.
3.  **Pasal 36**: Menyatakan bahwa perbuatan sebagaimana dimaksud dalam Pasal 27 sampai dengan Pasal 34 (termasuk tindakan manipulasi atau pengubahan dokumen) dilarang jika **mengakibatkan kerugian bagi orang lain**. Tindakan Budi yang mengubah nominal transfer tentu mengakibatkan kerugian bagi penjual laptop. | 5 |

**Rata-rata Skor:** 4,9  
**Analisis:** 	Ketergantungan terhadap kwalitas dokumen
Belum ada evaluasi otomatis

---

## 🏗️ Arsitektur Sistem


<img width="714" height="301" alt="arsitektur" src="https://github.com/user-attachments/assets/a55813b7-6b84-4cbd-ba94-5381d26c0cb4" />



---


## 📚 Referensi & Sumber

- Framework: LangChain docs
- LLM: Gemini
- Vector DB: ChromaDB
- Tutorial yang digunakan: (https://github.com/ThomasJanssen-tech/Retrieval-Augmented-Generation.git)

---

## 👨‍🏫 Informasi UTS

- **Mata Kuliah:** Data Engineering
- **Program Studi:** D4 Teknologi Rekayasa Perangkat Lunak
- **Deadline:** 23 April 2026
