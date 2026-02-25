# WebGIS


## 1. Pengenalan GIS & WebGIS

**GIS (Geographic Information System)** adalah sistem pengelolaan data berbasis peta yang digunakan untuk mengelola, menganalisis, dan menampilkan data dengan informasi geografis (koordinat) di permukaan bumi. 

**WebGIS** adalah pengembangan dari GIS yang bersifat *client-server* dan dapat diakses melalui web browser menggunakan internet. 
* **Keunggulan WebGIS** Multi-user, *real-time*, tidak perlu instalasi *software* khusus (seperti QGIS/ArcGIS desktop), dan mendukung integrasi sistem melalui API.
* **Implementasi** Perencanaan wilayah pemerintahan, pemetaan persebaran sekolah, mitigasi bencana, hingga monitoring aset perusahaan.

---

## 2. Jenis Data Spasial & Sistem Koordinat

Data dalam GIS tidak sekadar angka atau teks, melainkan data yang merepresentasikan lokasi di permukaan bumi.

### A. Jenis Data Spasial
1. **Vector Data** Menyimpan informasi lokasi dalam bentuk koordinat presisi tinggi.
   * **Point (Titik)** Lokasi sekolah, rumah sakit, ATM.
   * **Line (Garis)** Jaringan jalan, sungai, pipa.
   * **Polygon (Area)** Batas desa, wilayah kabupaten, area sawah.
2. **Raster Data** Berbentuk grid/piksel (citra satelit, foto udara, peta elevasi/DEM).

### B. Data Atribut & Sistem Koordinat
* **Data Atribut** Informasi tambahan yang menjelaskan objek spasial (misal nama sekolah, jumlah siswa).
* **Sistem Koordinat** Menentukan posisi pasti di bumi agar peta tidak bergeser (contoh **WGS84** menggunakan latitude/longitude, **UTM**).

---

## 3. Arsitektur & Komponen WebGIS (3-Tier)

WebGIS menggunakan arsitektur 3-tier yang memisahkan tanggung jawab sistem untuk keamanan dan kemudahan pemeliharaan.

1. **Client Layer (Frontend)** * Berada di sisi pengguna (browser). Tidak mengakses database secara langsung.
   * **Fungsi** Visualisasi peta, kontrol layer, navigasi (zoom/pan), dan UI/UX.
2. **Server Layer (Backend & GIS Server)** * Penghubung antara client dan database.
   * **Fungsi** Menerima request HTTP, memproses logika sistem, menjalankan query spasial, dan menyusun respons (JSON/GeoJSON).
3. **Spatial Database Layer** * Tempat penyimpanan data geometri dan atribut yang terisolasi dari akses publik.
   * **Fungsi** Menyimpan titik, garis, poligon, serta metadata spasial.

---

## 4. Teknologi & Standar OGC

WebGIS dibangun menggunakan kombinasi berbagai teknologi
* **Frontend** HTML, CSS, JavaScript, Leaflet, OpenLayers.
* **Backend** Node.js, Python (Django/Flask), PHP.
* **GIS Server** GeoServer, MapServer.
* **Database** PostgreSQL + PostGIS, MySQL Spatial, SpatiaLite.

**Standar OGC (Open Geospatial Consortium)**
* **WMS (Web Map Service)** Menampilkan peta dalam bentuk gambar/citra.
* **WFS (Web Feature Service)** Mengirim data spasial berformat vektor yang bisa diolah.
* **WCS (Web Coverage Service)** Layanan untuk data raster.

---

## 5. Fitur & API dalam WebGIS

WebGIS bekerja melalui komunikasi API (*Application Programming Interface*) dengan metode HTTP (GET, POST, PUT, DELETE) untuk mengambil data lokasi, menambah koordinat baru, atau mengupdate atribut.

**Fitur Analisis & Interaksi**
* **Navigasi** Zoom, Pan, Pencarian lokasi.
* **Layering** Mengatur visibilitas dan transparansi layer peta.
* **Analisis Spasial** *Buffer* (radius area), *Overlay* (menggabungkan layer), pengukuran jarak/luas.

---

## 6. Peran Penting QA dalam WebGIS

Karena kompleksitas komponennya, seorang Quality Assurance (QA) Tester sangat vital dalam pengembangan WebGIS. Potensi *bug* dapat terjadi pada UI, logika *backend*, atau data spasial yang bergeser.

**Fokus Pengujian QA pada WebGIS**
1. **Fungsionalitas & Akurasi Data** Memastikan fitur berjalan sesuai spesifikasi, koordinat presisi, dan tidak ada data yang hilang dari database spasial.
2. **Pengujian API** Memvalidasi format respons API (JSON/GeoJSON) dan status HTTP.
3. **Pengujian UI/UX** Memastikan tampilan konsisten di berbagai browser, peta tidak terpotong, dan kontrol layer responsif.
4. **Integrasi Sistem** Memastikan komunikasi antara Frontend, Backend, GeoServer, dan PostGIS berjalan tanpa *bottleneck*.
5. **Performa & Keamanan** Melakukan *load testing* untuk memastikan peta tidak lambat (lag) saat memuat layer yang berat, serta memastikan akses data spasial dilindungi oleh autentikasi (HTTPS & Role-based access).
