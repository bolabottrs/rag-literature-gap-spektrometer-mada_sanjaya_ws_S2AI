# Tugas 4 Individu — Pipeline RAG Literature Gap (SPEKTRA)

Pipeline ini membantu membuat **draf** Literature Gap Matrix untuk topik RAG dan low-cost visible spectrometer. Template artikel mencakup studi RAG/spektroskopi, referensi pendukung dari daftar pustaka buku, dan pembanding lintas domain.

## Yang dilakukan pipeline

1. Membaca metadata dari CSV.
2. Membaca PDF lokal jika `pdf_path` diisi; jika tidak, menggunakan abstrak/catatan CSV.
3. Memecah teks per halaman menjadi chunk dengan overlap.
4. Membuat embedding lokal memakai `paraphrase-multilingual-mpnet-base-v2`.
5. Mengambil chunk relevan **hanya dari artikel yang sedang diproses**, agar bukti tidak tercampur antarartikel.
6. Meminta Groq mengekstrak metode, domain, komponen RAG, evaluasi, temuan, keterbatasan, relevansi ke SPEKTRA, dan bukti gap ke format terstruktur.
7. Menghasilkan CSV, Excel, JSON bukti retrieval, dan sintesis Markdown.

RAG mengolah literatur dan dokumen; pipeline ini tidak memproses atau mengukur spektrum. Perhitungan, kalibrasi, dan interpretasi analitik tetap perlu prosedur teruji.

## Instalasi

Python 3.10+ direkomendasikan.

```bash
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate.ps1
# macOS/Linux
source .venv/bin/activate
pip install -r requirements.txt
```

Embedding model diunduh saat pertama dijalankan. Setelah itu embedding dibuat lokal. Untuk generasi, pipeline memerlukan API Groq dan koneksi internet.

## Mengatur API key dengan aman

Jangan memasukkan API key ke source code atau GitHub. Atur sementara di terminal:

```powershell
# Windows PowerShell
$env:GROQ_API_KEY="API_KEY_ANDA"
```

```bash
# macOS/Linux
export GROQ_API_KEY="API_KEY_ANDA"
```

Gunakan model ID Groq yang aktif pada akun Anda. ID bawaan dapat berubah, jadi cek dashboard/dokumentasi provider sebelum menjalankan.

## Mengisi CSV dan PDF

Buka `articles_individual_template.csv`. Setiap baris sudah berisi referensi inti dan pendukung. Untuk memakai full text, isi `pdf_path` dengan lokasi PDF artikel yang Anda miliki secara sah, misalnya `papers/speLL.pdf`. Jika kosong, ekstraksi hanya memakai abstrak dan catatan yang tersedia; hasil harus dianggap ringkasan awal, bukan telaah full text. Jangan memasukkan PDF yang akses/lisensinya tidak mengizinkan.

## Menjalankan

```bash
python rag_gap_pipeline_individual.py --input articles_individual_template.csv --outdir output --model MODEL_GROQ_AKTIF
```

Opsi:

```bash
python rag_gap_pipeline_individual.py --help
```

`--skip-synthesis` menghasilkan matriks dan evidence JSON tanpa panggilan API sintesis lintas artikel.

## Keluaran

- `output/literature_gap_matrix.csv`
- `output/literature_gap_matrix.xlsx`
- `output/article_evidence.json` — potongan yang diambil dan hasil ekstraksi
- `output/analysis.md` — draf sintesis gap

## Verifikasi akademik

Hasil model adalah draf. Cocokkan DOI, metadata, kutipan/halaman, metode, metrik, temuan, dan keterbatasan dengan artikel lengkap. Bedakan artikel peer-reviewed dan preprint. Jangan menyimpulkan novelty absolut dari korpus awal; dokumentasikan pencarian dan seleksi sebelum menulis klaim paper. Rahasia, data eksperimen sensitif, dan API key tidak boleh dimasukkan ke repository publik.
