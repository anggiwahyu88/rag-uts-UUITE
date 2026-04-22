# 🤖 RAG Starter Pack — UTS Data Engineering

> **Retrieval-Augmented Generation** — Sistem Tanya-Jawab Cerdas Berbasis Dokumen

Starter pack ini adalah **kerangka awal** proyek RAG untuk UTS Data Engineering D3/D4.
**Sistem Rekomendasi Pasal UU ITE — Sistem Rekomendasi Pasal UU ITE Berdasarkan Input Kasus**
Proyek ini adalah implementasi sistem RAG untuk pemenuhan tugas UTS Data Engineering D4. Sistem ini dikembangkan untuk memproses input berupa deskripsi kasus dari pengguna, kemudian mencari dan merekomendasikan pasal-pasal dalam Undang-Undang Informasi dan Transaksi Elektronik (UU ITE) Tahun 2008 yang paling relevan dengan kasus tersebut.

---

## 👥 Identitas Kelompok

| Nama | NIM | Tugas Utama |
|------|-----|-------------|
| Anggi Wahyu Saputra  | 244311003 | Data Engineer         |
| Azza Auliyaul Fitri  | 244311006 | Project Manager         |
| Prima Afda Mukhlisin  | 244311024 | Data Analyst         |

**Topik Domain:** Hukum  
**Stack yang Dipilih:** LangChain  
**LLM yang Digunakan:** Gemini  
**Vector DB yang Digunakan:** ChromaDB

---

## 🗂️ Struktur Proyek

```
rag-uts-uuITE/
├── data/                    # Dokumen sumber Anda (PDF, TXT, dll.)
│   └── uu-ite.pdf           
├── src/
│   ├── indexing.py          
│   └── query.py             
├── ui/
│   └── app.py               
├── docs/
│   └── arsitektur.png       
├── evaluation/
│   └── hasil_evaluasi.xlsx  
├── notebooks/
│   └── 01_demo_rag.ipynb    # Notebook demo dari hands-on session
├── .env.example             
├── .gitignore
├── requirements.txt
└── README.md
```

---

---

## 🔧 Konfigurasi

Semua konfigurasi utama ada di `src/config.py` (atau langsung di setiap file):

| Parameter | Default | Keterangan |
|-----------|---------|------------|
| `CHUNK_SIZE` | 1000 | Ukuran setiap chunk teks (karakter) |
| `CHUNK_OVERLAP` | 200 | Overlap antar chunk |
| `TOP_K` | 1 | Jumlah dokumen relevan yang diambil |
| `MODEL_NAME` | Gemini | Nama model LLM yang digunakan |

---

## 📊 Hasil Evaluasi

*(Isi setelah pengujian selesai)*

| # | Pertanyaan | Jawaban Sistem | Jawaban Ideal | Skor (1-5) |
|---|-----------|----------------|---------------|-----------|
| 1 | Perusahaan A dan Perusahaan B melakukan transaksi bisnis bernilai besar. Mereka sepakat membuat kontrak perjanjian kerja sama, tetapi kontrak tersebut hanya dibuat dalam bentuk dokumen elektronik dan ditandatangani secara elektronik tanpa kertas fisik. Apakah transaksi dan kontrak elektronik tersebut sah dan mengikat secara hukum? | ... | ... | ... |
| 2 | Budi sering meneruskan (forward) pesan berantai di grup chat yang berisi berita bohong untuk memancing rasa permusuhan dan kebencian terhadap suku dan agama tertentu (SARA). Apa sanksi pidana untuk perbuatan Budi? | ... | ... | ... |
| 3 | Jika seorang karyawan dengan sengaja dan tanpa hak menjebol sistem pengamanan komputer perusahaan untuk mencuri dokumen rahasia, bagaimana aturan hukum dan larangannya menurut undang-undang ini? | ... | ... | ... |
| 4 | Ada seseorang yang sakit hati, lalu sengaja membuat postingan di media sosial yang isinya menghina dan mencemarkan nama baik mantan atasannya agar dibaca oleh publik. Apakah perbuatan ini dilarang, dan masuk ke dalam pasal berapa? | ... | ... | ... |
| 5 | Budi membeli laptop bekas, tetapi dia mengedit file PDF bukti transfer bank miliknya. Budi mengubah nominal angkanya dari Rp100.000 menjadi Rp10.000.000 menggunakan aplikasi edit foto, lalu mengirimkannya ke penjual seolah-olah itu adalah bukti transfer yang asli dan sah. Apakah memalsukan dokumen elektronik ini ada aturannya? | ... | ... | ... |
| 6 | apa isi pasal 23 | ... | ... | ... |
| 7 | apa isi pasal 17 | ... | ... | ... |
| 8 | apa isi pasal 52 | ... | ... | ... |
| 9 | apa isi pasal 43 | ... | ... | ... |
| 10 | apa isi pasal 4 | ... | ... | ... |

**Rata-rata Skor:** ...  
**Analisis:** ...

---

## 🏗️ Arsitektur Sistem

*(Masukkan gambar diagram arsitektur di sini)*

```
[Dokumen] → [Loader] → [Splitter] → [Embedding] → [Vector DB]
                                                         ↕
[User Query] → [Query Embed] → [Retriever] → [Prompt] → [LLM] → [Jawaban]
```

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
