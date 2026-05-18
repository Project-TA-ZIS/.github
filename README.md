# Project TA — Monitoring Dasawisma & ZIS

<p align="center">
  <img src="team-pict.jpg" alt="Team Project" width="700" />
</p>

Sistem informasi untuk kebutuhan monitoring dan pengelolaan:

- **Dasawisma** (anggota/koordinator, pemasukan, penyaluran, total kas)
- **ZIS (Zakat/Infaq/Shodaqoh)** (amil, muzakki, mustahik, pemasukan, penyaluran, total)

Repo ini terdiri dari 2 aplikasi:

- **Backend**: `Backend_TA`1302220052 (Node.js + Express + Sequelize + MySQL/MariaDB)
- **Frontend**: `Frontend-TA` (React + Vite + Tailwind)

---

## Tim

| Nama | NIM | Peran |
|---|---:|---|
| Muhammad Rafif Aryasatya Purnomo | 1302220003 | Backend |
| Reihan Ramadhana | 1302220048 | System Analys |
| Naufal Ammar Zaidan | 1302220052 | Front End |

---

## Prasyarat

- Node.js (disarankan LTS)
- MySQL / MariaDB

---

## Menjalankan Backend (Local)

Masuk ke folder backend:

```bash
cd Backend_TA
```

Install dependency:

```bash
npm install
```

Buat file `.env` (jangan dipush) di root folder `Backend_TA`:

```env
PORT=3000

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=db_monitoring_dasawisma_zis
DB_PORT=3306

NODE_ENV=development
JWT_SECRET=replace-with-strong-secret
```

Buat database kosong:

```sql
CREATE DATABASE db_monitoring_dasawisma_zis;
```

Jalankan migration & seeder:

```bash
npx sequelize-cli db:migrate
npx sequelize-cli db:seed:all
```

Jalankan server:

```bash
npm start
```

### Swagger (API Docs)

- Swagger UI: `http://localhost:<PORT>/api-docs`

### Auth (JWT)

Header yang dipakai:

```text
Authorization: Bearer <token>
Content-Type: application/json
```

Catatan: akun seed default tersedia, detail password tidak ditulis di README (cek file seeder bila diperlukan untuk testing lokal).

---

## Menjalankan Frontend (Local)

Masuk ke folder frontend:

```bash
cd Frontend-TA
```

Install dependency:

```bash
npm install
```

Jalankan dev server:

```bash
npm run dev
```

Akses aplikasi:

- `http://localhost:5173`

### Konfigurasi URL Backend

Saat ini URL backend untuk login masih **hard-coded** di:

- `Frontend-TA/src/pages/auth/Login.jsx` (konstanta `API_URL`)

Untuk menjalankan lokal, ubah nilainya menjadi:

- `http://localhost:3000` (atau sesuai `PORT` backend)

---

## Struktur Folder

```text
Project_TA/
  Backend_TA/       # API + database migration/seeder + Swagger
  Frontend-TA/      # React (Vite)
  profile/          # aset profil (termasuk gambar tim)
```

## Referensi Cepat

- Panduan migration/seeder backend: `Backend_TA/src/database/step-database.md`
- Dokumentasi Swagger backend: `Backend_TA/src/documentation/**`
