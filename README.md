# Bank Sampah Digital

> Platform web untuk digitalisasi pengelolaan bank sampah, pencatatan transaksi setoran sampah, tabungan anggota, serta edukasi pemilahan sampah berbasis Artificial Intelligence (AI).

---

## Daftar Isi

1. [Identitas Pengembang](#a-identitas-pengembang)
2. [Tema Topik Kelompok](#b-tema-topik-kelompok)
3. [Deskripsi Aplikasi](#c-deskripsi-aplikasi)
   - [Latar Belakang](#latar-belakang)
   - [Permasalahan yang Diselesaikan](#permasalahan-yang-diselesaikan)
   - [Tujuan Pengembangan](#tujuan-pengembangan)
   - [Target Pengguna](#target-pengguna)
   - [Gambaran Cara Kerja](#gambaran-cara-kerja)
4. [Fitur Aplikasi dan Fitur AI](#d-fitur-aplikasi-dan-fitur-ai)
5. [Tautan Video Dokumentasi](#e-tautan-video-dokumentasi)
6. [Petunjuk Instalasi Aplikasi](#f-petunjuk-instalasi-aplikasi-setup-instruction)
7. [Teknologi dan Arsitektur](#g-teknologi-dan-arsitektur)

---

## A. Identitas Pengembang

- **Nama**: Haifa Nur Zahra
- **NIM**: 41257107
- **Kelompok**: 6
- **Mata Kuliah**: Rekayasa Perangkat Lunak (RPL)

---

## B. Tema Topik Kelompok

**TEMA :Sistem Informasi Berbasis Web untuk Pemberdayaan UMKM Cerdas.**

---

## C. Deskripsi Aplikasi

### Latar Belakang

Pengelolaan sampah di tingkat komunitas, RT/RW, dan desa sering menghadapi kendala efisiensi operasional. Sebagian bank sampah masih menggunakan pencatatan manual untuk transaksi setoran, penimbangan sampah, dan tabungan anggota. Metode tersebut rentan terhadap kesalahan perhitungan, risiko kehilangan data, lambatnya rekapitulasi laporan, serta rendahnya transparansi saldo anggota. Di sisi lain, masyarakat membutuhkan informasi mengenai kategori sampah yang bernilai ekonomis dan cara pemilahan yang tepat.

### Permasalahan yang Diselesaikan

1. **Pencatatan Manual yang Tidak Efisien:** Mengurangi ketergantungan pada pencatatan setoran berbasis kertas yang rawan kesalahan manusia dan kerusakan fisik.
2. **Kurangnya Transparansi Saldo:** Anggota membutuhkan akses untuk memantau saldo dan riwayat transaksi setoran maupun penarikan.
3. **Rekapitulasi yang Membutuhkan Waktu:** Pengelola membutuhkan cara yang lebih terstruktur untuk melihat total berat dan nilai transaksi setoran berdasarkan periode dan kategori.
4. **Keterbatasan Edukasi Pemilahan:** Anggota membutuhkan informasi untuk mengenali jenis sampah, pemilahan, dan potensi daur ulangnya.

### Tujuan Pengembangan

1. Membangun sistem informasi bank sampah berbasis web yang mudah digunakan oleh anggota dan pengurus.
2. Menyediakan pencatatan transaksi setoran yang menghitung nilai setoran berdasarkan berat dan harga kategori sampah.
3. Menyediakan dashboard dan laporan untuk membantu pemantauan transaksi serta saldo anggota.
4. Mengintegrasikan asisten AI untuk membantu konsultasi mengenai pemilahan sampah dan edukasi daur ulang.

### Target Pengguna

1. **Administrator (Admin):** Mengelola akun pengguna, status anggota, kategori dan harga sampah, konfigurasi AI, serta fungsi administratif yang tersedia pada sistem.
2. **Pengelola (Manager):** Mencatat transaksi setoran sampah dan memproses pengajuan penarikan saldo anggota.
3. **Anggota (Member/Nasabah):** Melihat saldo dan riwayat transaksi, mengajukan penarikan saldo, serta menggunakan fitur konsultasi AI.

Akun anggota dibuat oleh Admin melalui sistem. Pembuatan akun anggota bukan proses registrasi mandiri dari halaman publik.

### Gambaran Cara Kerja

1. **Pembuatan Akun dan Autentikasi:** Admin membuat akun anggota. Pengguna masuk menggunakan email dan kata sandi. Kata sandi disimpan menggunakan hashing `bcryptjs`, sedangkan sesi aplikasi menggunakan JWT yang dikelola dengan `jose`.
2. **Pengelolaan Kategori Sampah:** Admin mengelola kategori sampah, satuan, harga per kilogram, dan status aktif kategori.
3. **Pencatatan Setoran Sampah:** Admin atau Pengelola menimbang sampah, memilih anggota dan kategori, kemudian memasukkan berat setoran.
4. **Perhitungan Nilai Setoran:** Sistem mengambil harga kategori dari database dan menghitung nilai transaksi dengan rumus:

   `Nilai Setoran = Berat Sampah × Harga per Satuan`

   Transaksi setoran yang berhasil dicatat langsung berstatus `COMPLETED` dan nilainya masuk dalam perhitungan saldo anggota.
5. **Pengajuan Penarikan Saldo:** Anggota mengajukan nominal penarikan. Sistem memeriksa saldo tersedia dan menyimpan pengajuan dengan status `PENDING`.
6. **Pemrosesan Penarikan:** Admin atau Pengelola dapat menyetujui pengajuan menjadi `COMPLETED` atau menolaknya menjadi `REJECTED`.
7. **Konsultasi AI:** Pengguna dapat memanfaatkan fitur AI melalui halaman AI dan widget percakapan yang tersedia pada aplikasi.

---

## D. Fitur Aplikasi dan Fitur AI

### 1. Fitur Utama Aplikasi

- **Autentikasi dan Otorisasi:** Login dan logout menggunakan sesi JWT, dengan pemeriksaan hak akses berdasarkan peran pengguna.
- **Dashboard Multi-Role:** Tampilan dashboard disesuaikan dengan peran Admin, Pengelola, dan Anggota.
- **Antarmuka Responsif:** Antarmuka menggunakan CSS Modules dan dirancang untuk digunakan melalui perangkat desktop maupun ponsel.
- **Notifikasi Internal:** Sistem menyediakan notifikasi di dalam aplikasi untuk peristiwa seperti transaksi setoran, pengajuan penarikan, dan perubahan status.
- **Pencatatan Aktivitas:** Dokumentasi proyek mencakup fitur audit log untuk membantu pemantauan aktivitas administratif.

### 2. Fitur Pengelolaan Bank Sampah

- **Katalog Kategori Sampah:** Admin dapat mengelola nama kategori, satuan, harga per kilogram, serta status aktif atau nonaktif kategori.
- **Rekapitulasi Berat Sampah:** Sistem mengagregasikan berat transaksi setoran untuk menampilkan ringkasan berdasarkan kategori. Fitur ini merupakan rekapitulasi transaksi, bukan pengelolaan stok fisik persediaan sampah.
- **Buku Tabungan Digital:** Sistem menghitung saldo anggota berdasarkan total nilai setoran selesai dan transaksi penarikan.

Rumus saldo tersedia:

`Saldo Tersedia = Total Setoran COMPLETED - Total Penarikan COMPLETED - Total Penarikan PENDING`

Dengan demikian, pengajuan penarikan yang masih menunggu persetujuan sudah mengurangi saldo yang dapat digunakan. Jika pengajuan ditolak, nominal tersebut tidak lagi mengurangi saldo tersedia.

### 3. Fitur Pengguna dan Peran (Role-Based Access)

Sistem menerapkan kontrol akses berbasis peran (*Role-Based Access Control* / RBAC) dengan tiga peran:

- **Admin**
  - Membuat dan mengelola akun anggota.
  - Mengaktifkan atau menonaktifkan akun anggota.
  - Mengelola kategori sampah, harga, satuan, dan status kategori.
  - Mengelola konfigurasi provider AI dan API key.
  - Mengakses halaman laporan transaksi dan fungsi administratif.

- **Pengelola (Manager)**
  - Mencatat transaksi setoran sampah anggota.
  - Memproses pengajuan penarikan saldo dengan menyetujui atau menolaknya.
  - Melihat daftar pengajuan penarikan yang perlu diproses.
  - Mengakses fungsi operasional sesuai hak akses yang diberikan sistem.

- **Anggota (Member/Nasabah)**
  - Melihat saldo dan riwayat transaksi pribadi.
  - Melihat riwayat pengajuan penarikan.
  - Mengajukan penarikan saldo.
  - Mengakses fitur konsultasi AI.

**Catatan hak akses:** Pengelolaan kategori dan harga dilakukan oleh Admin. Pencatatan setoran dapat dilakukan oleh Admin maupun Pengelola. Pengajuan penarikan dilakukan oleh Anggota, sedangkan pemrosesannya dilakukan oleh Admin atau Pengelola.

### 4. Fitur Transaksi dan Pencatatan Sampah

- **Pencatatan Setoran Sampah:** Admin atau Pengelola mencatat anggota, kategori sampah, dan berat setoran. Input divalidasi, termasuk pemeriksaan berat positif dan batas berat yang ditentukan sistem.
- **Perhitungan Nilai Transaksi:** Nilai setoran dihitung di sisi server menggunakan harga kategori yang tersimpan di database. Harga per satuan juga disimpan sebagai snapshot pada transaksi.
- **Status Transaksi Setoran:** Status transaksi setoran yang digunakan adalah:
  - `COMPLETED`: transaksi setoran berhasil dicatat.
  - `CANCELLED`: transaksi setoran dibatalkan.
- **Pengajuan Penarikan Saldo:** Anggota hanya dapat mengajukan nominal positif dan tidak melebihi saldo tersedia.
- **Status Penarikan:** Status pengajuan penarikan adalah:
  - `PENDING`: menunggu pemrosesan Admin atau Pengelola.
  - `COMPLETED`: pengajuan disetujui dan diproses.
  - `REJECTED`: pengajuan ditolak.
- **Riwayat Transaksi:** Anggota dapat melihat riwayat transaksi dan penarikan sesuai hak akses.
- **Laporan Transaksi:** Halaman laporan Admin menyediakan filter tanggal, kategori, anggota, dan status transaksi setoran. Ringkasan laporan mencakup jumlah transaksi, total nilai, total berat, serta rekap berdasarkan kategori.
- **Ekspor dan Cetak:** Ekspor CSV mengambil data transaksi pada halaman yang sedang ditampilkan. Tombol cetak menggunakan fungsi cetak browser (`window.print()`), sehingga pengguna dapat memilih printer atau menyimpan hasil cetak sebagai PDF melalui browser. Laporan ini berfokus pada transaksi setoran dan bukan laporan penarikan.

### 5. Fitur Artificial Intelligence (AI)

Aplikasi menyediakan asisten AI untuk membantu konsultasi dan edukasi terkait pengelolaan serta pemilahan sampah.

#### A. Dukungan Multi-Provider

Sistem menyediakan konfigurasi untuk tiga provider AI:

- **Groq API:** Menggunakan endpoint API Groq yang kompatibel dengan format OpenAI. Model utama bawaan adalah `openai/gpt-oss-120b`, dengan `openai/gpt-oss-20b` sebagai model cadangan bawaan.
- **NVIDIA NIM:** Menggunakan endpoint NVIDIA NIM. Model utama bawaan adalah `openai/gpt-oss-20b`.
- **Google Gemini:** Menggunakan endpoint OpenAI-compatible Google. Model utama bawaan yang tercantum pada konfigurasi proyek adalah `gemini-3.8-flash`.

Daftar model dapat diambil dari endpoint provider. Jika daftar model langsung tidak dapat dimuat, sistem dapat menggunakan daftar model kurasi yang tersedia pada konfigurasi.

#### B. Context-Aware Prompting

Layanan AI memiliki modul untuk mengelola konteks dan pengetahuan yang berkaitan dengan aplikasi bank sampah. Konteks yang digunakan dapat mencakup informasi pengguna dan pengetahuan domain yang disiapkan oleh aplikasi, sehingga jawaban lebih relevan dengan kebutuhan konsultasi bank sampah.

#### C. Keamanan API Key

- API key provider AI dapat disimpan dalam database dalam bentuk terenkripsi menggunakan **AES-256-GCM**.
- Kunci `AI_CONFIG_ENCRYPTION_KEY` digunakan sebagai kunci enkripsi khusus. Jika tidak tersedia, implementasi menyediakan fallback ke `NEXTAUTH_SECRET`.
- Untuk pemisahan fungsi keamanan yang lebih baik, disarankan mengisi `AI_CONFIG_ENCRYPTION_KEY` dengan nilai acak yang kuat dan berbeda dari `NEXTAUTH_SECRET`.
- Antarmuka pengelolaan AI menampilkan API key dalam bentuk tersamarkan, bukan menampilkan nilai rahasia secara penuh.

#### D. Deterministic Quick Response

Proyek menyediakan modul `ai-quick-response.ts` untuk menangani respons cepat terhadap pertanyaan tertentu. Respons yang dapat dijawab oleh modul ini dapat diberikan tanpa selalu melakukan permintaan ke provider AI eksternal.

#### E. Antarmuka AI

- **Halaman AI:** Aplikasi menyediakan halaman konsultasi AI khusus pada area dashboard.
- **Floating Chat Widget:** Aplikasi menyediakan komponen widget percakapan AI yang dapat diakses dari antarmuka dashboard.

---

## E. Tautan Video Dokumentasi

### Tautan Video Progres 1
`https://youtu.be/8QkLyc3r-ZI`

### Tautan Video Progres 2
`https://youtu.be/bj5NDtzvids`

### Tautan Video Final Demo
`https://youtu.be/tkY6jcPfOb0`

---

## F. Petunjuk Instalasi Aplikasi (Setup Instruction)

Panduan berikut digunakan untuk menjalankan aplikasi Bank Sampah Digital pada lingkungan lokal pengembangan (*development*).

### 1. Prasyarat Sistem

Pastikan perangkat telah memiliki:

- **Node.js:** Versi 20.9 atau lebih baru. Workflow CI proyek menggunakan Node.js 20.x.
- **npm:** Versi yang kompatibel dengan Node.js dan `package-lock.json`.
- **Git:** Untuk mengkloning repositori.
- **Database PostgreSQL:** Dapat menggunakan PostgreSQL lokal atau layanan cloud seperti [Neon.tech](https://neon.tech/).

### 2. Langkah Instalasi

#### Langkah 1: Kloning Repositori

```bash
git clone https://github.com/haifazahra020108-del/bank-sampah-digital.git
```

#### Langkah 2: Masuk ke Direktori Proyek

```bash
cd bank-sampah-digital
```

#### Langkah 3: Instal Dependensi

```bash
npm install
```

Untuk instalasi yang mengikuti versi dependensi pada `package-lock.json`, dapat menggunakan:

```bash
npm ci
```

#### Langkah 4: Konfigurasi Environment Variable

Salin file `.env.example` menjadi `.env.local`.

Pada Windows PowerShell:

```powershell
Copy-Item .env.example .env.local
```

Pada Linux/macOS:

```bash
cp .env.example .env.local
```

Buka `.env.local`, lalu isi variabel yang diperlukan. Contoh konfigurasi:

```env
# URL aplikasi
NEXT_PUBLIC_APP_URL="http://localhost:3000"

# Koneksi database PostgreSQL
# DATABASE_URL menggunakan koneksi pooled (jika menggunakan Neon)
DATABASE_URL="postgresql://USER:PASSWORD@HOST/DB_NAME?sslmode=require"

# Koneksi langsung/unpooled untuk operasi Prisma tertentu
DATABASE_URL_UNPOOLED="postgresql://USER:PASSWORD@HOST/DB_NAME?sslmode=require"

# Secret untuk penandatanganan JWT session
NEXTAUTH_SECRET="GANTI_DENGAN_SECRET_ACAK_YANG_KUAT"

# Kunci enkripsi konfigurasi AI (disarankan berbeda dari NEXTAUTH_SECRET)
AI_CONFIG_ENCRYPTION_KEY="GANTI_DENGAN_KUNCI_ACAK_YANG_KUAT"

# Opsional: API key Groq sebagai konfigurasi fallback
GROQ_API_KEY=""

# Opsional: integrasi Telegram yang masih tersedia pada implementasi saat ini
TELEGRAM_BOT_TOKEN=""
TELEGRAM_BOT_USERNAME=""
TELEGRAM_WEBHOOK_SECRET=""
```

**Keterangan konfigurasi:**

- `DATABASE_URL` diperlukan untuk koneksi database PostgreSQL aplikasi.
- `DATABASE_URL_UNPOOLED` digunakan sebagai koneksi langsung (*direct connection*) oleh konfigurasi Prisma.
- `NEXTAUTH_SECRET` digunakan sebagai secret untuk JWT session aplikasi. Nama variabel ini dipertahankan pada konfigurasi proyek, tetapi autentikasi tidak menggunakan paket NextAuth.
- `AI_CONFIG_ENCRYPTION_KEY` digunakan untuk enkripsi konfigurasi API key AI. Jika tidak diisi, kode menyediakan fallback ke `NEXTAUTH_SECRET`; penggunaan kunci terpisah lebih disarankan.
- `GROQ_API_KEY` bersifat opsional sebagai fallback konfigurasi provider Groq.
- Variabel Telegram digunakan oleh integrasi Telegram yang masih terdapat dalam kode proyek saat ini.

Gunakan nilai rahasia milik lingkungan pengembangan sendiri. Jangan mengunggah `.env.local`, password database, secret JWT, atau API key ke repositori publik.

#### Langkah 5: Generate Prisma Client dan Sinkronisasi Database

Generate Prisma Client untuk skema utama:

```bash
npx prisma generate
```

Sinkronkan struktur skema PostgreSQL ke database:

```bash
npx prisma db push
```

> Proyek juga memiliki skema Prisma SQLite untuk kebutuhan skrip migrasi. Database utama aplikasi menggunakan PostgreSQL.

#### Langkah 6: Mengisi Data Awal (Database Seeding)

Jalankan perintah:

```bash
npx prisma db seed
```

Skrip seed membuat tiga akun demo awal menggunakan `upsert`. Skrip ini **tidak mengisi kategori sampah**. Jika akun dengan email yang sama sudah ada, data akun yang sudah ada tidak otomatis ditimpa karena bagian `update` pada seed dikosongkan.

#### Langkah 7: Menjalankan Server Pengembangan

```bash
npm run dev
```

#### Langkah 8: Mengakses Aplikasi

Buka browser dan kunjungi:

```text
http://localhost:3000
```

Aplikasi akan menampilkan halaman masuk Bank Sampah Digital.

### 3. Akun Pengguna Demo

Setelah menjalankan `npx prisma db seed`, akun demo awal yang disediakan oleh skrip seed adalah:

| Peran | Email Login | Password Awal |
|---|---|---|
| Admin | `admin@banksampah.local` | `Admin123!` |
| Pengelola | `pengelola@banksampah.local` | `Pengelola123!` |
| Anggota/Nasabah | `anggota@banksampah.local` | `Anggota123!` |

**Catatan keamanan:**

- Akun tersebut ditujukan untuk pengujian lokal.
- Ganti password demo sebelum menggunakan aplikasi pada lingkungan selain pengembangan.
- Karena seed menggunakan `upsert` dengan `update` kosong, menjalankan seed kembali tidak otomatis mengatur ulang password akun yang sudah ada.

### 4. Perintah Tersedia (Scripts)

Berikut perintah npm yang tersedia pada `package.json`:

| Perintah | Deskripsi |
|---|---|
| `npm run dev` | Menjalankan development server Next.js. |
| `npm run build` | Generate Prisma Client untuk skema PostgreSQL dan SQLite, kemudian membangun aplikasi Next.js untuk produksi. |
| `npm run start` | Menjalankan aplikasi hasil build produksi. |
| `npm run lint` | Menjalankan pemeriksaan kode menggunakan ESLint. |
| `npm test` | Menjalankan unit test menggunakan Vitest. |
| `npm run test:coverage` | Menjalankan unit test sekaligus menghasilkan laporan coverage. |
| `npm run ai:regression` | Menjalankan skrip regresi AI melalui `scripts/ai-regression.ts`. |

---

## G. Teknologi dan Arsitektur

- **Framework:** [Next.js](https://nextjs.org/) dengan App Router.
- **Library UI:** [React](https://react.dev/).
- **Bahasa Pemrograman:** [TypeScript](https://www.typescriptlang.org/).
- **Styling:** CSS Modules.
- **Database Utama:** PostgreSQL, termasuk dukungan layanan [Neon Serverless Postgres](https://neon.tech/).
- **ORM:** [Prisma ORM](https://www.prisma.io/).
- **Validasi Data:** [Zod](https://zod.dev/).
- **Autentikasi dan Sesi:** `jose` untuk JWT serta `bcryptjs` untuk hashing password.
- **Kriptografi:** Modul `crypto` bawaan Node.js dengan AES-256-GCM untuk enkripsi konfigurasi AI.
- **Integrasi AI:** Groq API, NVIDIA NIM, dan Google Gemini.
- **Pengujian:** [Vitest](https://vitest.dev/).
- **CI:** [GitHub Actions](https://github.com/features/actions).

### CI Pipeline

Proyek menyediakan workflow GitHub Actions pada `.github/workflows/ci.yml`. Workflow dijalankan ketika terdapat `push` atau `pull request` menuju branch `main`.

Tahapan CI meliputi:

1. Checkout repository.
2. Setup Node.js 20.x.
3. Instal dependensi menggunakan `npm ci`.
4. Generate Prisma Client untuk skema PostgreSQL dan SQLite.
5. Pemeriksaan kode menggunakan ESLint.
6. Pemeriksaan tipe menggunakan TypeScript (`npx tsc --noEmit`).
7. Menjalankan unit test menggunakan `npm test`.
8. Menjalankan production build menggunakan `npm run build`.

Workflow menggunakan environment variable dummy untuk kebutuhan CI dan tidak dimaksudkan untuk mengakses database produksi.

---

**Catatan pemeliharaan dokumentasi:** Deskripsi fitur pada README ini disesuaikan dengan struktur dan implementasi kode yang diperiksa. Perbarui dokumentasi apabila terdapat perubahan pada hak akses, alur transaksi, integrasi notifikasi, konfigurasi AI, atau perintah proyek.