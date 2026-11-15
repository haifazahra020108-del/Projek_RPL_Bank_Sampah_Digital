# Bank Sampah Digital

> Platform web modern untuk digitalisasi pengelolaan bank sampah, pencatatan transaksi setoran sampah, tabungan nasabah, dan edukasi pemilahan sampah berbasis Artificial Intelligence (AI).

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
   - [Fitur Utama Aplikasi](#1-fitur-utama-aplikasi)
   - [Fitur Pengelolaan Bank Sampah](#2-fitur-pengelolaan-bank-sampah)
   - [Fitur Pengguna dan Peran (Role-Based Access)](#3-fitur-pengguna-dan-peran-role-based-access)
   - [Fitur Transaksi dan Pencatatan Sampah](#4-fitur-transaksi-dan-pencatatan-sampah)
   - [Fitur Artificial Intelligence (AI)](#5-fitur-artificial-intelligence-ai)
5. [Tautan Video Dokumentasi](#e-tautan-video-dokumentasi)
   - [Tautan Video Progres 1](#tautan-video-progres-1)
   - [Tautan Video Progres 2](#tautan-video-progres-2)
   - [Tautan Video Final Demo](#tautan-video-final-demo)
6. [Petunjuk Instalasi Aplikasi (Setup Instruction)](#f-petunjuk-instalasi-aplikasi-setup-instruction)
   - [Prasyarat Sistem](#1-prasyarat-sistem)
   - [Langkah Instalasi](#2-langkah-instalasi)
   - [Akun Pengguna Demo](#3-akun-pengguna-demo)
   - [Perintah Tersedia (Scripts)](#4-perintah-tersedia-scripts)
7. [Teknologi dan Arsitektur](#g-teknologi-dan-arsitektur)

---

## A. Identitas Pengembang

- **Nama**: Haifa Nur Zahra
- **NIM**: 41257107
- **Kelompok**: 6
- **Mata Kuliah**: Rekayasa Perangkat Lunak (RPL)

---

## B. Tema Topik Kelompok

**Sistem Informasi Berbasis Web untuk Pemberdayaan UMKM Cerdas**

---

## C. Deskripsi Aplikasi

### Latar Belakang
Pengelolaan sampah di tingkat komunitas, RT/RW, dan desa sering kali menghadapi kendala efisiensi operasional. Sebagian besar bank sampah konvensional masih menggunakan buku besar fisik untuk mencatat setoran nasabah, penimbangan sampah, dan buku tabungan. Metode manual ini rentan terhadap kesalahan hitung, risiko kehilangan data, lambatnya rekapitulasi laporan berkala, serta rendahnya transparansi saldo nasabah. Di sisi lain, masyarakat sering kali kekurangan literasi mengenai kategori sampah yang bernilai ekonomis dan cara pemilahan yang tepat.

### Permasalahan yang Diselesaikan
1. **Pencatatan Manual yang Tidak Efisien:** Menggantikan proses pencatatan setoran berbasis kertas yang rawan *human error* dan risiko kerusakan fisik.
2. **Kurangnya Transparansi Saldo:** Nasabah tidak dapat memantau akumulasi saldo dan riwayat penyetoran secara *realtime*.
3. **Rekapitulasi dan Validasi yang Lambat:** Pengelola memerlukan waktu lama untuk menghitung total tonase per kategori sampah serta arus kas penarikan saldo.
4. **Keterbatasan Edukasi Pemilahan:** Nasabah kesulitan membedakan jenis sampah daur ulang (organik, anorganik, B3, kertas, plastik, logam) dan nilai ekonomisnya.

### Tujuan Pengembangan
1. Membangun sistem informasi bank sampah berbasis web yang andal, aman, dan mudah digunakan oleh nasabah maupun pengurus.
2. Menyediakan mekanisme pencatatan transaksi penimbangan sampah yang otomatis mengonversi bobot sampah menjadi saldo tabungan secara akurat.
3. Menghadirkan *dashboard* analitik untuk memantau perputaran volume sampah, status transaksi, dan arus kas penarikan dana.
4. Mengintegrasikan asisten cerdas AI guna memberikan konsultasi instan mengenai pemilahan sampah, nilai ekonomis, dan panduan daur ulang.

### Target Pengguna
1. **Administrator (Superadmin):** Mengelola konfigurasi sistem, audit log aktivitas, manajemen seluruh pengguna, konfigurasi *provider* & model AI, dan pengaturan *master data*.
2. **Pengelola / Manager Bank Sampah:** Memvalidasi transaksi setoran sampah fisik, memperbarui *master* kategori dan harga sampah per kg, memproses permohonan penarikan saldo nasabah, serta mencetak laporan berkala.
3. **Nasabah / Anggota (Warga):** Melihat saldo tabungan, mengajukan dan memantau riwayat setoran sampah, mengajukan penarikan dana, serta memanfaatkan konsultasi AI untuk pemilahan sampah.

### Gambaran Cara Kerja
1. **Registrasi & Otentikasi:** Nasabah dan pengelola mendaftar/masuk ke dalam platform menggunakan kredensial terenkripsi (Argon2/bcrypt) dengan sesi aman (JWT/NextAuth).
2. **Katalog Sampah Terstandarisasi:** Pengelola menentukan kategori sampah (misal: Plastik PET, Kardus/Kertas, Logam/Kaleng, Minyak Jelantah) lengkap dengan harga beli per kilogram yang dinamis.
3. **Penyetoran Sampah:** Nasabah membawa sampah ke lokasi bank sampah. Pengelola menimbang sampah, mencatat berat pada sistem, dan memilih kategori yang sesuai.
4. **Kalkulasi & Akumulasi Saldo Otomatis:** Sistem secara otomatis menghitung nilai rupiah berdasarkan rumus `bobot (kg) × harga satuan (Rp/kg)` dan menambahkannya langsung ke saldo buku tabungan digital nasabah.
5. **Penarikan Saldo:** Nasabah dapat mengajukan permohonan penarikan saldo (*cash out*) yang akan diverifikasi dan diselesaikan oleh pengelola.
6. **Konsultasi Edukatif AI:** Nasabah dan pengelola dapat berkonsultasi secara interaktif melalui AI Chat Widget untuk mengenali jenis sampah dan panduan daur ulangnya.

---

## D. Fitur Aplikasi dan Fitur AI

### 1. Fitur Utama Aplikasi
- **Autentikasi & Autorisasi Aman:** Login, register, logout berbasis JWT session dengan proteksi route middleware.
- **Dashboard Multi-Role:** Tampilan antarmuka yang disesuaikan secara dinamis untuk Admin, Pengelola, dan Anggota/Nasabah.
- **Desain UI Responsif & Modern:** Antarmuka responsif bernuansa hijau zamrud (*emerald green*) menggunakan CSS Modules yang ringan dan cepat diakses melalui perangkat desktop maupun ponsel cerdas.
- **Audit Logging:** Pencatatan otomatis setiap aktivitas krusial sistem (transaksi, modifikasi pengguna, konfigurasi) untuk menjaga akuntabilitas data.

### 2. Fitur Pengelolaan Bank Sampah
- **Katalog Master Kategori Sampah:** Pengaturan kategori sampah (Plastik, Kertas, Logam, Kaca, Elektronik, dll.), satuan ukuran, dan harga per kilogram terkini.
- **Manajemen Inventaris & Total Tonase:** Pelacakan total akumulasi volume sampah daur ulang yang berhasil dikumpulkan dari warga.
- **Buku Tabungan Nasabah Digital:** Pencatatan mutasi saldo masuk (dari setoran) dan saldo keluar (dari penarikan dana) secara transparan.

### 3. Fitur Pengguna dan Peran (Role-Based Access)
Sistem menerapkan kontrol akses berbasis peran (*Role-Based Access Control* / RBAC) dengan 3 tingkatan hak akses:
- **Admin:**
  - Manajemen penuh pengguna (aktivasi, penonaktifan, penetapan peran).
  - Monitoring audit log aktivitas pengguna.
  - Konfigurasi sistem dan manajemen API Key kecerdasan buatan (AI).
- **Pengelola (Manager):**
  - Verifikasi dan persetujuan transaksi setoran sampah.
  - Pembaruan harga dan kategori sampah.
  - Pemrosesan dan pencairan dana penarikan saldo anggota.
  - Akses laporan operasional bank sampah.
- **Anggota (Member / Nasabah):**
  - Akses buku tabungan dan saldo pribadi.
  - Riwayat detail setoran sampah dan penarikan saldo.
  - Akses fitur konsultasi pintar AI.

### 4. Fitur Transaksi dan Pencatatan Sampah
- **Pencatatan Setoran Sampah:** Formulir pencatatan setoran sampah dengan validasi skema ketat menggunakan Zod (bobot, kategori, nasabah tertuju).
- **Status Transaksi:** Pelacakan status transaksi secara transparan (`PENDING`, `APPROVED`, `REJECTED`, `COMPLETED`).
- **Penarikan Saldo (Withdrawal):** Pengajuan penarikan saldo oleh nasabah dengan validasi kecukupan saldo tabungan dan verifikasi pengelola.
- **Riwayat & Cetak Rekapitulasi:** Riwayat riil transaksi dengan filter tanggal, pencarian, dan opsi cetak laporan.

### 5. Fitur Artificial Intelligence (AI)

Aplikasi mengintegrasikan asisten cerdas AI yang dirancang khusus untuk mendukung operasional bank sampah dan literasi lingkungan warga.

#### A. Dukungan Multi-Provider Fleksibel
Sistem backend AI dirancang secara modular dan mendukung berbagai penyedia model LLM (*Large Language Model*):
- **Groq API:** Inferensi super cepat menggunakan model open-source seperti `llama-3.3-70b-versatile` dan `openai/gpt-oss-120b`.
- **NVIDIA NIM:** Catalog inference GPU terakselerasi berbasis API OpenAI-compatible seperti `meta/llama-3.3-70b-instruct`.
- **Google Gemini:** Integrasi melalui endpoint OpenAI-compatible Google (`gemini-2.0-flash`, `gemini-1.5-pro`, dll.).

#### B. Context-Aware Prompting
Asisten AI tidak sekadar chatbot umum, melainkan menerima injeksi konteks server (*Server-side Contextual Prompting*) yang mencakup:
- Identitas dan peran pengguna yang sedang aktif (Admin, Pengelola, atau Anggota).
- Basis pengetahuan resmi bank sampah (kategori sampah yang diterima, cara pemilahan, kebijakan saldo, dan tips daur ulang).
- Jawaban yang dihasilkan terfokus, relevan, etis, dan menggunakan bahasa Indonesia yang ramah.

#### C. Keamanan API Key Tingkat Lanjut (AES-256-GCM)
- Kunci API penyedia LLM disimpan di dalam basis data dalam bentuk terenkripsi penuh menggunakan algoritma kriptografi simetris **AES-256-GCM** yang dilindungi oleh kunci master `AI_CONFIG_ENCRYPTION_KEY`.
- Antarmuka Admin hanya menampilkan kunci yang telah dimaskir (contoh: `gsk_••••••••••••••••3aB9`), mencegah kebocoran kredensial dari tangkapan layar maupun inspeksi DOM browser.

#### D. Deterministic Quick Response Engine
Sistem dilengkapi modul respon instan deterministik (`ai-quick-response.ts`) yang mampu mengenali pertanyaan umum (FAQ seputar jadwal, jenis sampah yang diterima, cara tarik saldo) secara instan tanpa mengonsumsi kuota token API eksternal.

#### E. Antarmuka Ganda (Dual UI Experience)
- **Halaman AI Terdedikasi (`/dashboard/ai`):** Antarmuka obrolan penuh dengan riwayat interaksi mendalam untuk sesi konsultasi intensif.
- **Floating Chat Widget (`FloatingChatWidget`):** Widget mengambang di pojok layar aplikasi yang dapat diakses dari halaman dashboard mana pun kapan saja.

---

## E. Tautan Video Dokumentasi

### Tautan Video Progres 1
- **Status:** Belum tersedia
- **Tautan:** `[MASUKKAN LINK VIDEO PROGRES 1]`

### Tautan Video Progres 2
- **Status:** Belum tersedia
- **Tautan:** `[MASUKKAN LINK VIDEO PROGRES 2]`

### Tautan Video Final Demo
- **Status:** Belum tersedia
- **Tautan:** `[MASUKKAN LINK VIDEO FINAL DEMO]`

> *Catatan: Tautan video di atas akan diperbarui setelah proses perekaman dan pengunggahan dokumentasi masing-masing progres selesai dilaksanakan.*

---

## F. Petunjuk Instalasi Aplikasi (Setup Instruction)

Ikuti panduan langkah demi langkah di bawah ini untuk menginstal dan menjalankan aplikasi Bank Sampah Digital pada lingkungan lokal pengembangan (*development*).

### 1. Prasyarat Sistem
Pastikan perangkat Anda telah terpasang:
- **Node.js:** Versi `20.x` (disarankan LTS v20.x, minimal v18.17+)
- **npm:** Versi `10.x` atau lebih baru (bawaan Node.js)
- **Git:** Versi terbaru untuk kloning repositori
- **Basis Data:** PostgreSQL (dapat menggunakan instance cloud seperti [Neon.tech](https://neon.tech) atau PostgreSQL lokal)

### 2. Langkah Instalasi

#### Langkah 1: Kloning Repositori
Buka terminal / command prompt, lalu kloning repositori proyek:
```bash
git clone https://github.com/haifazahra020108-del/bank-sampah-digital.git
```

#### Langkah 2: Masuk ke Direktori Proyek
```bash
cd bank-sampah-digital
```

#### Langkah 3: Instal Dependensi Proyek
Instal seluruh paket dependensi yang dibutuhkan:
```bash
npm install
```
*(Atau gunakan `npm ci` jika ingin menginstal persis sesuai `package-lock.json`)*

#### Langkah 4: Konfigurasi Environment Variable
Salin template environment `.env.example` menjadi `.env.local`:
```bash
cp .env.example .env.local
```
> Pada sistem operasi Windows (PowerShell), gunakan:
> ```powershell
> Copy-Item .env.example .env.local
> ```

Buka file `.env.local` menggunakan text editor Anda dan sesuaikan nilainya:
```env
# URL Publik Aplikasi
NEXT_PUBLIC_APP_URL="http://localhost:3000"
NEXT_PUBLIC_API_URL="http://localhost:3000/api"

# Koneksi Basis Data PostgreSQL (Contoh menggunakan Neon.tech)
DATABASE_URL="postgresql://user:password@ep-example-pooler.us-east-2.aws.neon.tech/neondb?sslmode=require"

# Keamanan Otentikasi (JWT Secret)
NEXTAUTH_SECRET="buat-kunci-rahasia-minimal-32-karakter-acak"
NEXTAUTH_URL="http://localhost:3000"

# Kunci Enkripsi Master AI (AES-256-GCM)
# Jika tidak diisi, sistem otomatis fallback ke NEXTAUTH_SECRET
# Buat dengan: node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
AI_CONFIG_ENCRYPTION_KEY=""

# (Opsional) Kunci API LLM sebagai fallback sebelum konfigurasi disimpan di database
GROQ_API_KEY=""

# (Opsional) Integrasi notifikasi Telegram Bot
TELEGRAM_BOT_TOKEN=""
TELEGRAM_BOT_USERNAME=""
TELEGRAM_WEBHOOK_SECRET=""
TELEGRAM_WEBHOOK_URL=""
```

#### Langkah 5: Sinkronisasi Skema Database & Generate Prisma Client
Jalankan sinkronisasi skema Prisma ke basis data dan lakukan generate client:
```bash
# Generate Prisma Client TypeScript
npx prisma generate

# Sinkronisasi struktur tabel ke database (db push)
npx prisma db push
```

#### Langkah 6: Mengisi Data Awal (Database Seeding)
Jalankan skrip *seeding* untuk mengisi data master kategori sampah serta akun demo awal:
```bash
npx prisma db seed
```

#### Langkah 7: Menjalankan Server Pengembangan (Development Server)
Jalankan aplikasi dalam mode pengembangan:
```bash
npm run dev
```

#### Langkah 8: Mengakses Aplikasi Melalui Browser
Buka peramban web Anda dan navigasikan ke alamat:
```
http://localhost:3000
```
Anda akan diarahkan ke halaman login Bank Sampah Digital.

---

### 3. Akun Pengguna Demo

Setelah menjalankan `npx prisma db seed`, Anda dapat menguji seluruh alur kerja menggunakan akun demo berikut:

| Peran (Role) | Email Login | Password Default | Akses Utama |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@banksampah.local` | `Admin123!` | Manajemen Pengguna, Audit Log, Konfigurasi AI |
| **Pengelola** | `pengelola@banksampah.local` | `Pengelola123!` | Verifikasi Setoran, Kategori Sampah, Pencairan Saldo |
| **Anggota / Nasabah** | `anggota@banksampah.local` | `Anggota123!` | Cek Saldo, Riwayat Setoran, Pengajuan Tarik, AI Chat |

---

### 4. Perintah Tersedia (Scripts)

Berikut adalah daftar perintah npm yang tersedia pada proyek:

| Perintah | Deskripsi |
| :--- | :--- |
| `npm run dev` | Menjalankan development server pada `localhost:3000` |
| `npm run build` | Menjalankan kompilasi produksi Next.js |
| `npm run start` | Menjalankan aplikasi hasil kompilasi produksi |
| `npm run lint` | Menjalankan audit kode dengan ESLint |
| `npm test` | Menjalankan seluruh test suite unit testing (Vitest) |
| `npm run test:watch` | Menjalankan Vitest dalam mode interaktif (watch mode) |
| `npm run test:coverage` | Menjalankan pengujian dengan kalkulasi cakupan kode (coverage) |

---

## G. Teknologi dan Arsitektur

- **Framework:** [Next.js](https://nextjs.org/) (App Router Architecture, React Server Components & Client Components)
- **Bahasa Pemrograman:** [TypeScript](https://www.typescriptlang.org/) (Strict mode, end-to-end type safety)
- **Styling:** CSS Modules murni (*Vanilla CSS Modules*) dengan palet warna modern bertema hijau zamrud (*emerald green*) yang responsif.
- **Database & ORM:** PostgreSQL ([Neon Serverless Postgres](https://neon.tech/)) dan [Prisma ORM](https://www.prisma.io/).
- **Validasi Data:** [Zod](https://zod.dev/) untuk validasi form dan input skema runtime.
- **Kriptografi & Keamanan:** `crypto` bawaan Node.js (AES-256-GCM), bcryptjs / argon2, jose (JWT).
- **Pengujian (Testing):** [Vitest](https://vitest.dev/) untuk unit testing logic, repository, dan API route handler.
- **CI/CD:** [GitHub Actions](https://github.com/features/actions) untuk automated linting, type-checking, unit testing, dan production build pada setiap pull request & push.

