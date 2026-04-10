# Sentiment Analysis of Indonesian Financial News Using indoBERT and LSTM

## 📖 Deskripsi Proyek

Proyek ini menganalisis sentimen berita keuangan Indonesia menggunakan model **indoBERT** (BERT untuk bahasa Indonesia) dan **LSTM** (Long Short-Term Memory) untuk memMelihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi tren harga saham di Jakarta Composite Index (IHSG), khususnya pada saham-saham **Bluechip**.

Model ini menggabungkan two-stage architecture:
1. **indoBERT** untuk ekstraksi fitur sentimen dari berita
2. **LSTM** untuk Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi tren harga saham berdasarkan data historis dan sentimen

### Tujuan
- Mengakses dan memproses berita keuangan Indonesia secara otomatis
- Menganalisis sentimen berita yang relevan dengan saham pilihan
- MemMelihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi tren harga saham (naik/turun) dengan akurasi tinggi
- Mengidentifikasi korelasi antara sentimen berita dan pergerakan harga saham

---

## 🎯 Target Saham (Bluechip - LQ45)

Proyek ini fokus pada saham-saham papan atas dari berbagai sektor:

| Ticker | Nama Saham | Sektor |
|--------|-----------|--------|
| BBRI.JK | Bank Rakyat Indonesia | Keuangan |
| BMRI.JK | Bank Mandiri | Keuangan |
| BBCA.JK | Bank Central Asia | Keuangan |
| BBNI.JK | Bank Negara Indonesia | Keuangan |
| TLKM.JK | Telekomunikasi Indonesia | Infrastruktur |
| PGAS.JK | Perusahaan Gas Negara | Infrastruktur |
| ASII.JK | Astra International | Konsumer Non-Primer |
| ICBP.JK | Indofood CBP Sukses Makmur | Konsumer Primer |
| UNTR.JK | United Tractors | Industri |

---

## 📁 Struktur File

```
Sentiment analysis of Indonesian language financial news...
├── README.md                          # File dokumentasi (ini)
├── requirements.txt                   # Daftar dependensi Python
├── Data_Scrape_Berita_Terbaru.ipynb  # Notebook untuk web scraping berita
├── Skripsi_v2.ipynb                  # Notebook utama analisis dan model
└── berita_bersih_sastrawi.csv        # Dataset berita yang sudah diproses
```

### Penjelasan File

1. **Data_Scrape_Berita_Terbaru.ipynb**
   - Web scraping berita dari berbagai portal berita Indonesia
   - Menggunakan Selenium dan Newspaper3k untuk ekstraksi konten
   - Membersihkan dan menyimpan berita ke format CSV
   - **Output**: CSV berisi berita yang sudah dicrawl

2. **Skripsi_v2.ipynb**
   - Analisis eksploratori data dan korelasi saham
   - Preprocessing data teks menggunakan Sastrawi stemmer
   - Ekstraksi fitur sentimen dengan indoBERT
   - Modelling LSTM untuk Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi tren harga
   - Evaluasi model dengan berbagai metrik (Accuracy, Precision, Recall, F1-Score)
   - Visualisasi hasil Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi dan confusion matrix
   - **Input**: berita_bersih_sastrawi.csv
   - **Output**: Model predictions, visualisasi grafik dan metrics

3. **berita_bersih_sastrawi.csv**
   - Dataset berita yang sudah diproses
   - Kolom: [date, ticker, category, title, content, stemmed_text, sentiment, dll]
   - Siap untuk digunakan dalam model training

---

## 🚀 Cara Menggunakan

### Prerequisite
- Python 3.7+
- pip atau conda
- GPU (opsional, tapi sangat disarankan untuk training LSTM)

### 1. Setup Environment

```bash
# Clone repository (setelah di-push ke GitHub)
git clone https://github.com/[username]/[repo-name].git
cd [repo-name]

# Buat virtual environment
python -m venv venv

# Aktivasi virtual environment
# Untuk Windows:
venv\Scripts\activate
# Untuk macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Jalankan Web Scraping (Opsional)

Jika ingin mengupdate dataset berita:

```bash
# Buka Jupyter Notebook
jupyter notebook

# Jalankan: Data_Scrape_Berita_Terbaru.ipynb
# Cell by cell sesuai dengan instruksi di dalam notebook
```

### 3. Jalankan Model Analisis dan Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi

```bash
# Buka Jupyter Notebook
jupyter notebook

# Jalankan: Skripsi_v2.ipynb
# Cell by cell untuk melihat analisis dan hasil Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi
```

---

## 🔧 Teknologi dan Library Utama

### Data Processing
- **pandas** - Manipulasi data tabular
- **numpy** - Komputasi numerik
- **yfinance** - Download harga saham historis

### Text Processing & NLP
- **Sastrawi** - Stemming untuk bahasa Indonesia
- **NLTK** - Natural Language Toolkit
- **transformers** - Hugging Face untuk indoBERT

### Deep Learning
- **TensorFlow/Keras** - Framework untuk LSTM dan neural networks
- **sklearn** - Machine learning utilities (preprocessing, metrics)

### Web Scraping
- **Selenium** - Browser automation untuk scraping
- **newspaper3k** - Ekstraksi artikel dari web

### Visualization
- **matplotlib** - Plotting dasar
- **seaborn** - Statistical data visualization

---

## 📊 Output dan Hasil

Proyek menghasilkan beberapa output utama:

1. **Model Metrics**
   - Accuracy Score
   - Precision, Recall, F1-Score
   - Confusion Matrix

2. **Visualisasi**
   - Grafik pergerakan harga saham
   ** gambar grafik pergerakan harga saham 
   - Heatmap korelasi antar saham
   - Distribusi sentimen berita
   - Confusion matrix Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi
   - Trend Melihat apakah dengan mengintegrasikan Hybrid Model akan meningkatkan akurasi vs aktual

3. **Data**
   - CSV dengan sentiment labels
   - Predictions dengan confidence scores

---

## 🔍 Metodologi

### Tahap 1: Data Collection
- Download data harga saham dari yfinance (2021-2026)
- Web scraping berita finansial dari portal Indonesia

### Tahap 2: Data Preprocessing
- Normalisasi teks (lowercase, remove punctuation)
- Stemming menggunakan Sastrawi untuk bahasa Indonesia
- Tokenisasi dan padding sequence

### Tahap 3: Feature Extraction
- Menggunakan indoBERT untuk generate embeddings sentimen
- Klasifikasi sentimen: Positive, Neutral, Negative

### Tahap 4: Model Training
- LSTM architecture dengan input embeddings
- Dropout layers untuk regularisasi
- Early stopping untuk mencegah overfitting
- Train-test split: 80-20

### Tahap 5: Evaluation
- Confusion matrix
- Classification report (precision, recall, f1-score)
- Accuracy comparison across different stocks

---

## 📈 Hasil yang Diharapkan

Model diharapkan dapat:

- ✅ Mengidentifikasi periode bearish/bullish dari sentimen berita
- ✅ Memberikan insights tentang pengaruh sentimen terhadap pergerakan saham

---

## 📌 Catatan Penting

1. **Dataset Terbatas**: Dataset berita mungkin mencakup periode terbatas. Untuk hasil optimal, pastikan data tersedia untuk periode yang ingin dianalisis.

2. **Internet Connection**: Web scraping memerlukan koneksi internet yang stabil.

3. **Computational Resources**: LSTM training memerlukan waktu. GPU sangat membantu untuk accelerate training.

4. **Preprocessing Time**: Stemming dan tokenisasi untuk dataset besar memerlukan waktu. Progress bar disediakan untuk monitoring.

5. **Model Sensitivity**: Model LSTM sensitif terhadap hyperparameter. Tuning mungkin diperlukan untuk dataset baru.

---

## 🤝 Kontribusi

Untuk kontribusi atau perbaikan:
1. Fork repository
2. Buat branch feature (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

---

## 📝 License

Proyek ini tersedia untuk penggunaan akademis dan penelitian.

---

## 📞 Kontak dan Support

Untuk pertanyaan, silakan buat issue di repository GitHub ini.
firmanwijayakusuma22@gmail.com
firmanwijayakusuma22@gmail.com

---

## 🙏 Ucapan Terima Kasih

- Hugging Face untuk model indoBERT
- Yahoo Finance untuk data harga saham
- Community open source Python untuk semua library yang digunakan

---

**Last Updated:** April 2026  
**Version:** 2.0
