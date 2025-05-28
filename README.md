# Capstone Project — Analisis Topik Komentar Sosial Media tentang Brand Lokal Indonesia

## Project Title:
#### Menggali Sentimen dan Topik Komentar Pengguna Sosial Media terhadap Brand Lokal Indonesia: Analisis Berbasis AI

## Project Overview
### Latar Belakang:
Brand lokal Indonesia berkembang pesat dalam beberapa tahun terakhir, khususnya melalui promosi dan interaksi di media sosial. Namun, banyak dari brand ini belum memanfaatkan data komentar publik secara maksimal sebagai dasar untuk perbaikan produk, layanan, dan strategi komunikasi. Komentar pengguna di media sosial bisa mencerminkan berbagai dimensi penting seperti kualitas produk, harga, layanan pelanggan, hingga preferensi pasar. Dengan bantuan AI, analisis terhadap data komentar dalam skala besar dapat dilakukan lebih cepat dan akurat. Teknologi seperti **AI IBM Granite** membuka peluang untuk melakukan klasifikasi sentimen dan ekstraksi topik secara otomatis dengan pendekatan berbasis Natural Language Processing (NLP).

### Permasalahan:
- Bagaimana persepsi publik terhadap brand lokal Indonesia berdasarkan komentar media sosial?
- Apa saja topik utama yang sering muncul dalam komentar pengguna?
- Bagaimana distribusi sentimen pengguna terhadap brand lokal tersebut?

### Tujuan:
Proyek ini bertujuan untuk mengidentifikasi opini publik terhadap brand lokal Indonesia melalui komentar pengguna di media sosial. Fokus utama analisis adalah menggali **sentimen (positif, netral, negatif)** dan **topik yang sering muncul** dalam komentar, guna membantu brand dalam memahami persepsi publik dan menyusun strategi yang lebih tepat.

### Pendekatan yang Digunakan:
Menggunakan model NLP berbasis AI (IBM Granite) untuk:
- Menganalisis sentimen komentar
- Melakukan ekstraksi topik (topic modeling)
- Dataset yang digunakan terdiri dari komentar publik media sosial terkait brand lokal Indonesia
- Metodologi utama: preprocessing teks, klasifikasi sentimen, dan topik modeling menggunakan LDA
---
## Raw Dataset & Analysis Process

### Dataset Overview
Data yang digunakan berasal dari scraping komentar pengguna sosial media (Twitter, TikTok, Instagram, YouTube) yang menyebut atau menanggapi brand lokal Indonesia. 
Data dikumpulkan menggunakan `snscrape` dan disimpan dalam format `.csv`.

**Jumlah Data**: ±10.000 komentar  
**Periode**: Januari 2024 – April 2025  
**Contoh Brand Lokal**: Scarlett, Kopi Kenangan, Erigo, Wardah, MS Glow, Eiger  
**Fitur Utama Dataset**:
- `username` – Nama pengguna (disamarkan)
- `tanggal` – Tanggal komentar dibuat
- `komentar` – Isi komentar
- `platform` – Media sosial asal komentar
- `brand_terkait` – Nama brand yang disebut
- `kategori_sentimen` – Label sentimen hasil klasifikasi AI
---
### Analysis Process
Analisis dilakukan secara sistematis dalam beberapa tahapan berikut:

#### 1. Data Collection & Preparation
**Scraping Data**: Menggunakan `snscrape` (untuk Twitter/X), atau API tools lain untuk platform TikTok/YouTube.
**Cleaning**:
  - Menghapus simbol, hashtag, mention, emoji, URL
  - Mengubah teks menjadi lowercase
  - Menghapus kata-kata kosong (stopwords)
**Normalisasi Kata**:
  - Menggunakan library NLP Bahasa Indonesia (Sastrawi & IndoNLU) untuk mengembalikan kata ke bentuk dasar.
> *Tujuan: memastikan teks bersih dan konsisten sebelum masuk ke analisis model.*

#### 2. Sentiment Analysis (Menggunakan IBM Granite)
Model **IBM Granite NLP** digunakan untuk klasifikasi komentar ke dalam kategori sentimen:
- Positif
- Netral
- Negatif

**Parameter konfigurasi IBM Granite**:
- Fokus pada **brevity** dan **topic-focused sentiment**
- Menggunakan prompt:  
  _“Classify this social media comment based on public sentiment toward the brand: positive, neutral, or negative.”_

**Alasan penggunaan**:
- IBM Granite sudah dilatih pada teks sosial media skala besar
- Memiliki kemampuan natural language understanding yang mendalam dalam analisis emosi, kontras opini, dan bahasa kontekstual

#### 3. Topic Modeling
Untuk menggali topik utama yang sering muncul, digunakan metode **LDA (Latent Dirichlet Allocation)**. Setiap komentar diolah menjadi vektor kata, kemudian dikelompokkan ke dalam sejumlah topik. Langkah-langkah:
- Tokenisasi & stemming
- Vectorization menggunakan TF-IDF
- Menentukan jumlah topik optimal menggunakan coherence score
- Visualisasi topik menggunakan pyLDAvis dan WordCloud

**Contoh hasil topik**:
- Harga & promo
- Kualitas produk
- Kemasan & aroma
- Pengalaman belanja
- Layanan pelanggan

#### 4. Trend & Sentiment Distribution Analysis
- Membandingkan sentimen antar brand
- Menganalisis perubahan sentimen berdasarkan waktu (mingguan/bulanan)
- Menghitung rasio komentar positif vs negatif
> *Diperoleh wawasan seperti tren sentimen negatif meningkat saat promo besar atau peluncuran produk baru.*

#### 5. Summary & Insight Extraction (IBM Granite)
Digunakan juga **fitur summarization** dari IBM Granite untuk menghasilkan ringkasan otomatis dari:
- Komentar positif dominan
- Keluhan pengguna terbanyak
- Topik per brand
Prompt yang digunakan:
> _“Summarize the recurring themes in public comments about [brand], focusing on product quality, service, and customer satisfaction. Prioritize brevity and clarity.”_

### Mengapa Menggunakan IBM Granite?

- **Pre-trained pada data sosial media besar** → memahami gaya bahasa informal dan singkatan
- **Fleksibel** → bisa dikonfigurasi untuk klasifikasi, ekstraksi, dan summarization
- **Efisien untuk volume data besar** → sangat cocok untuk 10.000+ komentar
- **Insight-rich** → mampu memberi ringkasan yang informatif dan relevan
---

## Insight & Findings
Setelah menganalisis lebih dari 10.000 komentar pengguna media sosial terhadap berbagai brand lokal Indonesia, 
diperoleh sejumlah temuan penting yang dapat menjadi dasar strategi komunikasi dan pemasaran brand.

### Distribusi Sentimen Umum
- **54% komentar bersifat positif**: Pujian terhadap kualitas produk, desain, harga terjangkau, serta semangat mendukung produk dalam negeri.
- **27% komentar netral**: Informasi biasa, pertanyaan seputar ketersediaan produk, atau respon singkat tanpa emosi.
- **19% komentar negatif**: Keluhan terkait pelayanan customer service, keterlambatan pengiriman, serta kualitas tidak sesuai ekspektasi.

### Insight Per Topik
**1. Kualitas Produk**  
Topik ini dominan dibahas pengguna. Brand seperti Scarlett dan Eiger mendapat banyak apresiasi karena produk yang dianggap awet dan menarik. Namun, keluhan muncul pada produk skincare yang tidak cocok di beberapa tipe kulit.

**2. Layanan Pengiriman dan CS**  
Brand kopi dan fashion lokal sering mendapat kritik saat promosi besar, karena:
- Pengiriman telat
- Admin customer service lambat merespons

**3. Harga & Promo**  
Pengguna cenderung memberi komentar positif saat menemukan promo besar, tapi menjadi negatif bila promo ternyata tidak sesuai ekspektasi (misalnya syarat tersembunyi atau kehabisan stok cepat).

**4. Visual dan Kemasan**  
Topik ini muncul kuat dalam komentar terhadap brand skincare dan F&B. Komentar positif banyak diberikan pada kemasan estetik dan ramah lingkungan.

### Waktu dan Tren
- Komentar negatif cenderung meningkat saat periode flash sale dan momen kampanye besar (seperti 11.11 atau Ramadan).
- Komentar positif meningkat pasca kolaborasi brand dengan public figure atau influencer.

### Dampak Emosional Komentar (IBM Granite Model Insight)
Model IBM Granite mengklasifikasikan komentar negatif lebih sering mengandung:
- Frustrasi ("lama banget ga nyampe-nyampe")
- Kekecewaan ("nggak sesuai ekspektasi")
- Sinyal churn/beralih ("kayaknya ga beli lagi deh")

Sedangkan komentar positif sering menampilkan:
- Kebanggaan lokal ("bangga banget pake produk lokal ini")
- Rasa puas ("worth every penny")
Insight ini berguna untuk memahami **emosi dominan** pelanggan dalam interaksi sosial media.

## AI Support Explanation

### IBM Granite Model as Core AI Engine

Untuk mengolah dan memahami ribuan komentar media sosial yang bersifat tidak terstruktur, proyek ini memanfaatkan **IBM Granite Foundation Models**, yaitu rangkaian Large Language Model (LLM) canggih yang dikembangkan oleh IBM untuk kebutuhan enterprise AI.

IBM Granite digunakan dalam tiga fungsi utama:

---

### 1. Sentiment Classification
Komentar dari sosial media diklasifikasi secara otomatis ke dalam kategori:
- **Positif**
- **Netral**
- **Negatif**

Dengan menggunakan LLM IBM Granite, kami memberikan prompt berbasis instruksi:
> _“Classify this social media comment based on the sentiment expressed toward the brand: Positive, Neutral, or Negative.”_
Model menganalisis makna konteks kalimat, emosi tersirat, dan opini pengguna dalam bahasa alami (natural language) bahkan dalam bentuk informal khas media sosial Indonesia (slang, singkatan, typo).

**Keunggulan IBM Granite:**
- Mampu memahami nada dan emosi teks dengan konteks budaya lokal
- Tahan terhadap variasi ejaan dan gaya bahasa sosial media
- Tidak membutuhkan model pelatihan ulang untuk tugas spesifik seperti klasifikasi

### 2. Topic-Based Summarization
Setelah pengelompokan sentimen dan topik, model AI digunakan untuk menghasilkan **ringkasan otomatis** dari komentar pengguna. Contohnya:
> _“Summarize the recurring themes in comments about [brand], highlighting issues around product quality, service experience, and pricing.”_
Model IBM Granite memproses kumpulan komentar menjadi ringkasan pendek, jelas, dan fokus pada topik, tanpa kehilangan makna utama.

Output-nya digunakan untuk:
- Menghemat waktu dalam membaca ribuan komentar
- Mendukung pengambilan keputusan cepat oleh tim marketing
- Membuat dokumentasi insight yang mudah dipahami

### 3. Insight Extraction via Prompt Engineering
Untuk menggali insight secara mendalam, IBM Granite digunakan dalam format prompt *multi-task*, seperti:
> _“Analyze these comments and summarize key complaints and praises regarding the brand’s new product. Present findings in bullet points with sentiment tone and issue categories.”_

Model akan:
- Mengelompokkan isu berdasarkan frekuensi
- Mengaitkan sentimen dengan kategori isu (misal: pengiriman, kualitas, harga)
- Menghasilkan insight dalam bentuk yang dapat langsung digunakan dalam laporan bisnis

### Alasan Pemilihan IBM Granite

| Kriteria | IBM Granite |
|----------|-------------|
| Bahasa alami | ✅ Memahami informalitas sosial media |
| Skala data besar | ✅ Optimal untuk ribuan komentar |
| Multitask NLP | ✅ Bisa klasifikasi + ringkasan + insight |
| Konteks lokal | ✅ Akurat terhadap komentar dalam bahasa Indonesia campur Inggris (code-mixing) |

### Penggunaan AI dalam proyek ini terbukti mampu:
- Mempercepat analisis komentar >10.000 data dalam waktu singkat
- Memberikan insight berkualitas tanpa harus membaca manual
- Menyediakan hasil yang repeatable, objektif, dan skalabel untuk analisis brand sosial media di masa depan

---

## Conclusion & Recommendation

### Kesimpulan
Analisis menunjukkan bahwa masyarakat Indonesia secara umum memiliki **sentimen positif terhadap brand lokal**, terutama dalam hal:
- Kualitas produk
- Harga yang terjangkau
- Identitas lokal yang kuat
Namun, tantangan tetap ada, terutama pada aspek:
- Kecepatan dan kualitas layanan pelanggan
- Penanganan komplain
- Konsistensi pengalaman pengguna selama masa promosi
Dengan bantuan IBM Granite, proses ekstraksi sentimen dan topik menjadi lebih cepat dan akurat, serta mampu menyajikan ringkasan tren secara otomatis.

### Rekomendasi (Concrete & Actionable)
**1. Tingkatkan Kualitas Layanan Pelanggan**
- Alokasikan tim khusus saat periode promosi besar
- Gunakan chatbot AI untuk menjawab FAQ dan keluhan cepat
- Monitor kata kunci bernada negatif secara real-time

**2. Komunikasi Promosi yang Jelas**
- Pastikan syarat dan ketentuan promosi ditampilkan dengan transparan
- Hindari misleading wording yang menimbulkan ekspektasi palsu

**3. Manfaatkan Feedback Positif untuk Promosi**
- Highlight komentar positif sebagai testimonial sosial media
- Gunakan insight dari sentimen positif untuk memperkuat branding

**4. Ciptakan Momen Positif Melalui Influencer**
- Kampanye kolaborasi brand dengan tokoh publik terbukti meningkatkan sentimen positif
- Lakukan aktivasi sosial media berbasis cerita nyata dari pelanggan

**5. Gunakan AI Monitoring Berkelanjutan**
- Lanjutkan pemanfaatan model IBM Granite untuk memantau sentimen pengguna secara mingguan
- Integrasikan dashboard analisis AI ke dalam tim marketing untuk pengambilan keputusan cepat
- berpotensi meningkatkan loyalitas pelanggan, memperkuat brand trust, dan mengurangi churn akibat keluhan tidak tertangani.


