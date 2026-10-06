# Flask Microservices

## Praktikum Arsitektur Monolith vs Microservices dengan Flask Python

---

## Deskripsi

Project ini merupakan implementasi praktikum Arsitektur Monolith dan Microservices menggunakan Flask Python.

Pada praktikum ini dibuat dua pendekatan arsitektur aplikasi, yaitu Monolith dan Microservices.

Monolith merupakan arsitektur yang menempatkan seluruh fungsi aplikasi dalam satu aplikasi. Sedangkan Microservices membagi aplikasi menjadi beberapa service yang dapat berjalan secara terpisah dan saling berkomunikasi menggunakan REST API.

---

## Tujuan Praktikum

1. Memahami konsep arsitektur Monolith.
2. Memahami konsep arsitektur Microservices.
3. Membuat aplikasi menggunakan Flask Python.
4. Membuat REST API menggunakan Flask.
5. Memahami komunikasi antar-service.
6. Menjalankan beberapa service pada port yang berbeda.
7. Memahami konsep Fault Isolation.
8. Membandingkan arsitektur Monolith dan Microservices.

---

## Teknologi yang Digunakan

| Teknologi | Keterangan |
|---|---|
| Python | Bahasa pemrograman |
| Flask | Framework untuk membuat aplikasi dan REST API |
| Requests | Library untuk komunikasi antar-service |
| REST API | Komunikasi menggunakan HTTP |
| Git | Version Control |
| GitHub | Repository project |

---

## Struktur Project

```text
monolith-vs-microservices-flask/
│
├── monolith_app.py
├── book_service.py
├── order_service.py
├── README.md
│
├── LAPORAN PRAKTIKUM ARSITEKTUR MONOLITH VS MICROSERVICES
│   DENGAN FLASK PYTHON.docx
│
└── Laporan_Monolith_Microservices_Elisabet Kunmop.pdf
```

---

# LANGKAH KERJA PRAKTIKUM

## BAGIAN 1 — PERSIAPAN

> ### LANGKAH 1 — Membuat Folder Project
>
> **Tujuan**
>
> Membuat folder sebagai tempat menyimpan seluruh file project Flask.
>
> **Perintah**
>
> ```bash
> mkdir monolith-vs-microservices-flask
> cd monolith-vs-microservices-flask
> ```
>
> **Keterangan**
>
> `mkdir` digunakan untuk membuat folder project, sedangkan `cd` digunakan untuk masuk ke dalam folder tersebut.
>
> **Dokumentasi:**  
> Screenshot tampilan terminal setelah folder project dibuat.

---

> ### LANGKAH 2 — Mengecek Versi Python
>
> **Perintah**
>
> ```bash
> python --version
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk memastikan Python telah terinstal pada komputer.
>
> **Hasil yang diharapkan**
>
> ```text
> Python 3.x.x
> ```
>
> **Dokumentasi:**  
> Screenshot hasil perintah `python --version`.

---

> ### LANGKAH 3 — Menginstal Flask dan Requests
>
> **Perintah**
>
> ```bash
> pip install Flask requests
> ```
>
> **Keterangan**
>
> Flask digunakan untuk membuat aplikasi dan REST API, sedangkan Requests digunakan untuk komunikasi HTTP antar-service.
>
> **Dokumentasi:**  
> Screenshot proses instalasi Flask dan Requests.

---

> ### LANGKAH 4 — Mengecek Instalasi Flask
>
> **Perintah**
>
> ```bash
> pip show Flask
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk memastikan Flask telah berhasil terinstal.
>
> **Dokumentasi:**  
> Screenshot informasi Flask yang ditampilkan pada terminal.

---

# BAGIAN 2 — MEMBUAT APLIKASI MONOLITH

> ### LANGKAH 5 — Membuat Aplikasi Monolith
>
> Buat file:
>
> ```text
> monolith_app.py
> ```
>
> Aplikasi Monolith menggabungkan beberapa fungsi dalam satu aplikasi, yaitu:
>
> - Book Management
> - Order Management
>
> **Struktur Monolith**
>
> ```text
> Client
>    │
>    ▼
> ┌─────────────────────────┐
> │      Monolith Flask     │
> │                         │
> │  ┌───────────────────┐  │
> │  │  Book Management  │  │
> │  └───────────────────┘  │
> │                         │
> │  ┌───────────────────┐  │
> │  │ Order Management  │  │
> │  └───────────────────┘  │
> │                         │
> └─────────────────────────┘
> ```
>
> **Dokumentasi:**  
> Screenshot isi file `monolith_app.py`.

---

> ### LANGKAH 6 — Menjalankan Aplikasi Monolith
>
> **Perintah**
>
> ```bash
> python monolith_app.py
> ```
>
> **Hasil**
>
> Aplikasi berjalan pada:
>
> ```text
> http://localhost:5000
> ```
>
> **Keterangan**
>
> Aplikasi Monolith dijalankan menggunakan satu aplikasi Flask pada port 5000.
>
> **Dokumentasi:**  
> Screenshot terminal saat Monolith berhasil dijalankan.

---

> ### LANGKAH 7 — Mengakses Data Buku
>
> **Perintah**
>
> ```bash
> curl.exe http://localhost:5000/books
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk mengambil daftar buku melalui endpoint `/books`.
>
> **Endpoint**
>
> ```text
> GET /books
> ```
>
> **Dokumentasi:**  
> Screenshot hasil daftar buku.

---

> ### LANGKAH 8 — Membuat Pesanan pada Monolith
>
> **Perintah**
>
> ```bash
> curl.exe -X POST http://localhost:5000/orders -H "Content-Type: application/json" -d "{\"book_id\":1,\"quantity\":1}"
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk mengirim data pesanan ke endpoint `/orders`.
>
> **Endpoint**
>
> ```text
> POST /orders
> ```
>
> **Dokumentasi:**  
> Screenshot hasil proses pembuatan order.

---

# BAGIAN 3 — MEMBUAT MICROSERVICES

> ### LANGKAH 9 — Membuat Book Service
>
> Buat file:
>
> ```text
> book_service.py
> ```
>
> Book Service bertugas untuk:
>
> - Menyediakan data buku.
> - Menampilkan daftar buku.
> - Menampilkan buku berdasarkan ID.
> - Menyediakan informasi stok buku.
>
> Book Service berjalan pada:
>
> ```text
> http://localhost:5001
> ```
>
> **Dokumentasi:**  
> Screenshot isi file `book_service.py`.

---

> ### LANGKAH 10 — Menjalankan Book Service
>
> **Perintah**
>
> ```bash
> python book_service.py
> ```
>
> **Hasil**
>
> Book Service berjalan pada port 5001.
>
> ```text
> http://localhost:5001
> ```
>
> **Dokumentasi:**  
> Screenshot terminal saat Book Service berjalan.

---

> ### LANGKAH 11 — Mengakses Semua Data Buku
>
> **Perintah**
>
> ```bash
> curl.exe http://localhost:5001/books
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk mengambil seluruh data buku dari Book Service.
>
> **Endpoint**
>
> ```text
> GET /books
> ```
>
> **Dokumentasi:**  
> Screenshot hasil data buku dari Book Service.

---

> ### LANGKAH 12 — Mengakses Buku Berdasarkan ID
>
> **Perintah**
>
> ```bash
> curl.exe http://localhost:5001/books/1
> ```
>
> **Keterangan**
>
> Perintah digunakan untuk mengambil data buku berdasarkan ID.
>
> **Endpoint**
>
> ```text
> GET /books/1
> ```
>
> **Dokumentasi:**  
> Screenshot data buku berdasarkan ID.

---

# BAGIAN 4 — ORDER SERVICE

> ### LANGKAH 13 — Membuat Order Service
>
> Buat file:
>
> ```text
> order_service.py
> ```
>
> Order Service bertugas menangani proses pemesanan dan berkomunikasi dengan Book Service.
>
> Order Service berjalan pada:
>
> ```text
> http://localhost:5002
> ```
>
> **Dokumentasi:**  
> Screenshot isi file `order_service.py`.

---

> ### LANGKAH 14 — Menjalankan Order Service
>
> **Perintah**
>
> ```bash
> python order_service.py
> ```
>
> **Hasil**
>
> Order Service berjalan pada port 5002.
>
> ```text
> http://localhost:5002
> ```
>
> **Dokumentasi:**  
> Screenshot terminal saat Order Service berjalan.

---

> ### LANGKAH 15 — Membuat Pesanan melalui Order Service
>
> **Perintah**
>
> ```bash
> curl.exe -X POST http://localhost:5002/orders -H "Content-Type: application/json" -d "{\"book_id\":1,\"quantity\":1}"
> ```
>
> **Keterangan**
>
> Order Service menerima permintaan pemesanan kemudian meminta informasi buku kepada Book Service.
>
> **Alur komunikasi**
>
> ```text
> Client
>    │
>    ▼
> Order Service
>    │
>    │ Request Data Buku
>    ▼
> Book Service
>    │
>    │ Response Data Buku
>    ▼
> Order Service
>    │
>    ▼
> Client
> ```
>
> **Dokumentasi:**  
> Screenshot hasil pembuatan order melalui Order Service.

---

# BAGIAN 5 — PENGUJIAN KOMUNIKASI MICROSERVICES

> ### LANGKAH 16 — Menguji Komunikasi Antar-Service
>
> Pastikan kedua service sedang berjalan:
>
> ```text
> Book Service  → Port 5001
> Order Service → Port 5002
> ```
>
> Jalankan:
>
> ```bash
> curl.exe http://localhost:5001/books
> ```
>
> Kemudian lakukan pemesanan:
>
> ```bash
> curl.exe -X POST http://localhost:5002/orders -H "Content-Type: application/json" -d "{\"book_id\":1,\"quantity\":1}"
> ```
>
> **Keterangan**
>
> Pengujian dilakukan untuk memastikan Order Service dapat mengambil informasi dari Book Service.
>
> **Dokumentasi:**  
> Screenshot hasil komunikasi antara Order Service dan Book Service.

---

# BAGIAN 6 — PENGUJIAN FAULT ISOLATION

> ### LANGKAH 17 — Menghentikan Book Service
>
> Hentikan proses Book Service menggunakan:
>
> ```text
> CTRL + C
> ```
>
> **Kondisi**
>
> ```text
> Book Service  → DOWN
> Order Service → MASIH BERJALAN
> ```
>
> **Dokumentasi:**  
> Screenshot Book Service setelah dihentikan.

---

> ### LANGKAH 18 — Menguji Order Service Saat Book Service Down
>
> Jalankan:
>
> ```bash
> curl.exe -X POST http://localhost:5002/orders -H "Content-Type: application/json" -d "{\"book_id\":1,\"quantity\":1}"
> ```
>
> **Hasil yang diharapkan**
>
> ```text
> Book Service sedang down!
> ```
>
> **Keterangan**
>
> Hasil tersebut menunjukkan bahwa Order Service masih berjalan walaupun Book Service mengalami gangguan.
>
> Kondisi ini merupakan contoh Fault Isolation pada arsitektur Microservices.
>
> **Dokumentasi:**  
> Screenshot pesan ketika Book Service tidak aktif.

---

# BAGIAN 7 — MENJALANKAN KEMBALI BOOK SERVICE

> ### LANGKAH 19 — Menjalankan Kembali Book Service
>
> Jalankan kembali:
>
> ```bash
> python book_service.py
> ```
>
> Book Service kembali aktif pada:
>
> ```text
> http://localhost:5001
> ```
>
> **Dokumentasi:**  
> Screenshot Book Service berhasil aktif kembali.

---

> ### LANGKAH 20 — Menguji Kembali Order Service
>
> Setelah Book Service aktif kembali, jalankan:
>
> ```bash
> curl.exe -X POST http://localhost:5002/orders -H "Content-Type: application/json" -d "{\"book_id\":1,\"quantity\":1}"
> ```
>
> **Keterangan**
>
> Setelah Book Service aktif kembali, Order Service dapat berkomunikasi kembali dengan Book Service sehingga proses pemesanan dapat dilakukan.
>
> **Dokumentasi:**  
> Screenshot order berhasil setelah Book Service aktif kembali.

---

# BAGIAN 8 — PERBANDINGAN ARSITEKTUR

> ### LANGKAH 21 — Membandingkan Monolith dan Microservices
>
> | Aspek | Monolith | Microservices |
> |---|---|---|
> | Struktur | Satu aplikasi | Beberapa service |
> | Deployment | Satu aplikasi | Setiap service dapat dijalankan terpisah |
> | Komunikasi | Internal aplikasi | REST API / HTTP |
> | Pengembangan | Terpusat | Terbagi berdasarkan service |
> | Fault Isolation | Lebih rendah | Lebih baik |
> | Skalabilitas | Aplikasi secara keseluruhan | Dapat dilakukan per service |
> | Kompleksitas | Lebih sederhana | Lebih kompleks |
> | Port | Satu port utama | Port berbeda |

---

# ANALISA

Berdasarkan praktikum yang telah dilakukan, arsitektur Monolith memiliki struktur yang lebih sederhana karena seluruh fungsi aplikasi berada dalam satu aplikasi Flask.

Pada arsitektur Microservices, aplikasi dibagi menjadi beberapa service yang memiliki tugas masing-masing. Pada project ini terdapat Book Service dan Order Service.

Book Service bertanggung jawab menyediakan data buku, sedangkan Order Service bertanggung jawab menangani proses pemesanan. Kedua service tersebut berkomunikasi menggunakan REST API melalui HTTP.

Pengujian juga menunjukkan adanya Fault Isolation. Ketika Book Service dihentikan, Order Service masih dapat berjalan, tetapi tidak dapat mengambil data buku sampai Book Service dijalankan kembali.

Dengan demikian, Microservices memberikan pemisahan fungsi yang lebih baik dan memungkinkan service dikembangkan serta dijalankan secara terpisah. Namun, Microservices juga memiliki tingkat kompleksitas yang lebih tinggi dibandingkan Monolith.

---

# KESIMPULAN

Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa:

1. Arsitektur Monolith menempatkan seluruh fungsi aplikasi dalam satu aplikasi.
2. Arsitektur Microservices membagi aplikasi menjadi beberapa service.
3. Flask dapat digunakan untuk membuat aplikasi dan REST API.
4. Library Requests dapat digunakan untuk komunikasi antar-service.
5. Book Service dan Order Service dapat berjalan pada port yang berbeda.
6. Microservices memungkinkan setiap service berjalan secara terpisah.
7. Fault Isolation memungkinkan gangguan pada satu service tidak langsung menghentikan service lainnya.
8. Monolith lebih sederhana, sedangkan Microservices lebih fleksibel tetapi memiliki kompleksitas yang lebih tinggi.

---

# DOKUMENTASI PRAKTIKUM

Dokumentasi praktikum meliputi:

1. Pembuatan folder project.
2. Pengecekan versi Python.
3. Instalasi Flask dan Requests.
4. Pembuatan aplikasi Monolith.
5. Menjalankan Monolith.
6. Pengujian API Monolith.
7. Pembuatan Book Service.
8. Menjalankan Book Service.
9. Pengujian Book Service.
10. Pembuatan Order Service.
11. Menjalankan Order Service.
12. Pengujian Order Service.
13. Pengujian komunikasi antar-service.
14. Pengujian Fault Isolation.
15. Menjalankan kembali Book Service.
16. Pengujian order setelah service aktif kembali.

---

# LAPORAN PRAKTIKUM

File laporan tersedia di repository:

```text
LAPORAN PRAKTIKUM ARSITEKTUR MONOLITH VS MICROSERVICES
DENGAN FLASK PYTHON.docx
```



---

# IDENTITAS

**Nama:** Elisabet Kunmop  
**Kelas:** TRKJ-2D  
**Program Studi:** Teknologi Rekayasa Komputer Jaringan  
**Jurusan:** Teknologi Informasi dan Komputer  
**Institusi:** Politeknik Negeri Lhokseumawe

---

# REFERENSI

1. Dokumentasi Flask.
2. Dokumentasi Python.
3. Dokumentasi Requests.
4. Modul Praktikum Paradigma Sistem untuk IT.
5. Dokumentasi REST API.