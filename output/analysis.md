# Sintesis Literature Gap

**Sintesis Literatur (Bahasa Indonesia) – Matriks Kesenjangan untuk Asisten RAG Berbasis Bukti pada Interpretasi & Dokumentasi Spektrum Tampak dari Spektrometer Murah**

| **Kelompok** | **Studi (penulis‑tahun, DOI)** | **Modality / Fokus** | **Komponen RAG yang Dilaporkan** | **Evaluasi / Bukti Empiris** | **Keterbatasan yang Dilaporkan** | **Relevansi terhadap SPEKTRA (visible, low‑cost)** |
|--------------|--------------------------------|----------------------|-----------------------------------|------------------------------|-----------------------------------|---------------------------------------------------|
| **RAG + Spektroskopi (inti)** | Fu et al., 2025, 10.1021/acs.jcim.5c01236 | Near‑infrared (NIR) spectral modelling; tidak memakai spektrum tampak | • *Code RAG* (pembuatan kode analisis) <br>• *Data RAG* (pengambilan dataset historis) | Tidak ada metrik, benchmark, atau studi pengguna yang dilaporkan dalam abstrak | Tidak ada laporan eksplisit; abstrak hanya menyajikan arsitektur | Menyebutkan perbedaan spektral (NIR vs. visible) → memberi contoh arsitektur RAG yang dapat di‑adaptasi, tetapi tidak ada bukti kinerja pada rentang 400‑700 nm |
| | Xie et al., 2026, 10.1016/j.aca.2025.344857 | Infrared (IR) spectroscopy, multi‑task (klasifikasi, regresi, deteksi anomali) | • Basis pengetahuan literatur terstruktur <br>• Retrieval preprocessing/fitur sebagai bagian RAG | Dinyatakan dievaluasi pada beberapa dataset IR, namun metrik atau hasil spesifik tidak disajikan | Tidak ada detail tentang algoritma retrieval atau batasan sistem | Fokus pada IR; arsitektur “retrieval‑driven preprocessing” dapat di‑transfer ke spektrum tampak, tetapi bukti empiris belum tersedia |
| | Xie et al., 2025, 10.2139/ssrn.5391577 | Dataset SDAAP (teks pengetahuan spektral) + RAG QA | • Retrieval berbasis entitas kueri <br>• LLM generatif <br>• Mekanisme jejak sumber | Tidak ada evaluasi kuantitatif (akurasi QA, waktu respons) | Tidak ada laporan keterbatasan | Dataset SDAAP berisi pengetahuan spektral yang dapat dipakai untuk spektrum tampak; namun belum diuji pada data instrumen nyata atau pada tugas dokumentasi otomatis |
| **Instrumen / Aplikasi (bukan RAG)** | Rayhan et al., 2025, 10.1016/j.saa.2024.125240 | Spektrometer smartphone (400‑700 nm), kalibrasi panjang gelombang & koreksi respons detektor | – (tidak ada komponen RAG) | Tidak ada evaluasi RAG; hanya deskripsi kalibrasi | Tidak ada diskusi integrasi dengan sistem AI | Menyediakan “ground‑truth” instrumentasi yang diperlukan untuk menguji asisten RAG pada spektrum tampak |
| | Laganovska et al., 2020, 10.1016/j.ohx.2020.e00108 | Spektrofotometer nirkabel open‑source, biaya rendah | – | – | – | Menjadi platform hardware yang dapat di‑hubungkan ke pipeline RAG (mis. streaming data) |
| | Doğan et al., 2024, 10.1016/j.talanta.2023.125021 | Sistem kolorimetri berbasis ekstrak kubis merah + ML pada smartphone | – | – | – | Menunjukkan alternatif non‑spektral untuk monitoring; berguna sebagai pembanding “sensor‑only” vs. spektral‑RAG |
| | Kesonkan et al., 2026, 10.1016/j.microc.2025.116266 | Assay boron dengan ekstrak kurkumin hijau + spektrometer portabel | – | – | – | Contoh aplikasi kimia analitik dengan instrumen portabel; tidak ada RAG namun memberi skenario penggunaan data spektral |
| **Cross‑domain RAG (pembanding)** | Heredia & Barreda, 2025, 10.1016/j.aei.2024.103007 | RAG untuk troubleshooting manufaktur keramik (tidak ada spektroskopi) | • Retrieval bibliografi khusus <br>• Pre‑ & post‑processing teks | Tidak ada metrik kuantitatif dalam abstrak | – | Menunjukkan cara menggabungkan pengetahuan domain‑spesifik dengan RAG; dapat diadaptasi untuk pengetahuan spektral |
| | Wan et al., 2025, 10.1016/j.aei.2025.103212 | Hybrid KG + vector RAG untuk Q&A manufaktur aditif | • Knowledge‑graph retrieval <br>• Dense‑vector retrieval <br>• LLM generator | 77.8 % exact‑match, 76.5 % context‑precision (pada teks) | – | Menunjukkan performa hybrid retrieval pada teks; belum diuji pada data multimodal (spektrogram) |
| | Mao et al., 2025, 10.7506/spkx1002-6630-20250408-059 | RAG untuk regulasi keamanan pangan (teks) | • KG keamanan pangan <br>• Retrieval terarah LLM <br>• Qwen‑7B‑Chat (LoRA) | BLEU‑4, ROUGE‑L, akurasi (tidak ada spektrum) | – | Menunjukkan metrik evaluasi teks; dapat menjadi referensi untuk menilai kualitas dokumentasi otomatis pada spektrum |

### Analisis Kesenjangan (Gap) – Provisional

1. **Rentang Spektral** – Semua studi RAG inti (Fu 2025; Xie 2026; Xie 2025) beroperasi pada **NIR atau IR**, bukan pada **spektrum tampak (400‑700 nm)** yang menjadi fokus SPEKTRA.  
2. **Evaluasi Empiris** – Tidak ada satu pun studi yang melaporkan **metrik kuantitatif** (mis. akurasi identifikasi puncak, kesalahan kalibrasi, kualitas teks dokumentasi) atau **studi pengguna** pada tugas interpretasi spektrum tampak.  
3. **Integrasi Instrumen Murah** – Artikel instrumen (Rayhan 2025; Laganovska 2020) memberikan **karakteristik hardware** tetapi tidak menghubungkannya dengan **pipeline RAG** (retrieval + LLM).  
4. **Dokumentasi Otomatis** – Tidak ada laporan tentang **pembuatan laporan laboratorium** (deskripsi sampel, prosedur, hasil, interpretasi) yang di‑generate oleh RAG berbasis bukti.  
5. **Jejak Sumber (Traceability)** – SDAAP (Xie 2025) menekankan *source traceability* tetapi belum diuji pada **data spektral nyata** atau pada **penulisan laporan**.  
6. **Cross‑modal Retrieval** – Studi hybrid (Wan 2025) menunjukkan potensi **retrieval multimodal** (KG + vektor) tetapi belum diaplikasikan pada **spektrogram** atau **metadata instrumen**.  

> **Catatan:** Kesenjangan‑kesenjangan ini bersifat **sementara** dan terbatas pada korpus yang telah ditinjau; tidak dapat dijadikan bukti bahwa tidak ada karya lain di luar set ini yang telah menutupnya.

### Pertanyaan Penelitian yang Diusulkan

> **Bagaimana merancang dan mengevaluasi sebuah asisten berbasis Retrieval‑Augmented Generation yang dapat (i) menginterpretasikan spektrum tampak yang dihasilkan oleh spektrometer seluler berbiaya rendah, (ii) menghasilkan dokumentasi laboratorium yang lengkap dan dapat ditelusuri ke sumber literatur, serta (iii) beroperasi dengan latensi yang dapat diterima pada perangkat mobile?**

### Kriteria Evaluasi yang Dapat Dikuantifikasi

| **Dimensi** | **Metrik** | **Deskripsi Pengukuran** |
|-------------|------------|--------------------------|
| **Akurasi Spektral** | *Mean Absolute Error* (MAE) pada panjang gelombang kalibrasi vs. standar NIST | Menggunakan sampel referensi (e.g., holmium oxide) |
| **Identifikasi Puncak** | *Precision, Recall, F1* untuk deteksi puncak utama (≥ 3 % intensitas) | Dibandingkan dengan anotasi manual |
| **Kualitas Dokumentasi** | *BLEU‑4 / ROUGE‑L* antara laporan otomatis dan laporan manual ahli | Menilai kesesuaian terminologi, urutan prosedur, dan interpretasi |
| **Jejak Sumber** | Persentase referensi yang dapat ditelusuri (linkable DOI) dalam laporan | Mengukur keberhasilan *source traceability* |
| **Latensi Sistem** | Waktu rata‑rata (detik) dari input spektrum → laporan selesai | Target ≤ 5 s pada perangkat Android 8+ |
| **Kepuasan Pengguna** | Skor SUS (System Usability Scale) dari 30 pengguna (mahasiswa kimia) | Nilai ≥ 68 dianggap “acceptable” |

### Batasan yang Diharapkan

1. **Keterbatasan Data Pelatihan** – Dataset SDAAP (Xie 2025) berisi teks pengetahuan spektral, namun belum mencakup contoh spektrum tampak dari instrumen murah; diperlukan **kurasi tambahan**.  
2. **Variabilitas Instrumen** – Spektrometer smartphone (Rayhan 2025) dapat memiliki **noise dan drift** yang berbeda antar unit; model RAG harus tahan terhadap variasi ini atau memerlukan **kalibrasi dinamis**.  
3. **Keterbatasan LLM** – Model bahasa besar yang dipakai (mis. GPT‑4‑turunan) dapat menghasilkan **hallucination** pada interpretasi kimia; mekanisme *retrieval‑grounding* harus diuji secara ketat.  
4. **Keterbatasan Evaluasi** – Pengukuran kualitas laporan (BLEU/ROUGE) bersifat **permukaan**; penilaian ahli kimia diperlukan untuk validasi semantik yang lebih dalam.  
5. **Keterbatasan Komputasi Mobile** – Penggabungan retrieval (vektor) dan generasi LLM pada perangkat seluler dapat menimbulkan **batas memori**; solusi hybrid (cloud‑edge) harus dipertimbangkan.  

---

**Kesimpulan**  
Literatur yang ada menunjukkan bahwa arsitektur RAG untuk spektroskopi telah mulai muncul (Fu 2025; Xie 2026; Xie 2025), namun **tidak ada bukti empiris** pada spektrum tampak yang dihasilkan oleh **instrumen murah** serta **tidak ada demonstrasi dokumentasi otomatis yang dapat ditelusuri**. Dengan memanfaatkan karakteristik hardware (Rayhan 2025; Laganovska 2020) dan meminjam teknik hybrid retrieval dari domain lain (Wan 2025; Heredia & Barreda 2025), penelitian yang diusulkan dapat mengisi kesenjangan ini secara terukur, sambil tetap mengakui bahwa kesenjangan tersebut bersifat **sementara** dan terbatas pada kumpulan literatur yang ditinjau.

## Pemeriksaan sebelum pengumpulan
- Cocokkan metadata, DOI, metode, metrik, dan kutipan dengan artikel lengkap.
- Bedakan hasil full text dengan hasil abstrak/catatan.
- Gap ini hanya berlaku pada korpus yang ditelaah; perlu pencarian sistematis sebelum klaim novelty.
- RAG membantu retrieval dan penjelasan; tidak menggantikan kalibrasi atau pengukuran spektrum.
