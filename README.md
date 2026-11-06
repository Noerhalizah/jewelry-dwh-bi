# 💎 Data Warehouse & Business Intelligence - Jewelry Project

Proyek ini merupakan implementasi *end-to-end* Data Warehouse & Business Intelligence untuk basis data penjualan perhiasan (Jewelry). Alur pemrosesan data mencakup ekstraksi data dari basis data operasional OLTP, pembuatan area *Staging*, perancangan *Star Schema* pada Data Warehouse, pembentukan *Datamart*, hingga ekspor dataset CSV.

---

## 🛠️ Teknologi & Tools
* **Database Management System:** PostgreSQL (via pgAdmin 4 & DBeaver)
* **ETL Tool:** Pentaho Data Integration (PDI / Spoon)
* **Arsitektur Data:** OLTP → Staging & Log → Data Warehouse (Star Schema) → Datamart (PostgreSQL & CSV)

---

## 📐 Arsitektur & Skema Data

### 1. Source Data (OLTP)
Terdiri dari 15 tabel operasional pada schema `public` database `Jewerly`.

### 2. Staging Area
Menggunakan database `staging_jewerly_kel10` yang terbagi atas dua skema:
* `staging`: Wadah penampungan sementara kerangka tabel dari OLTP.
* `log`: Tempat pencatatan audit eksekusi pemindahan data.

### 3. Data Warehouse (Star Schema)
Berpusat pada tabel fakta `fakta.fact_sales_detail_jewerly` dan dihubungkan dengan 5 tabel dimensi:
* `dimensi.dim_customers`
* `dimensi.dim_product`
* `dimensi.dim_stores`
* `dimensi.dim_brands`
* `dimensi.dim_date`

### 4. Datamart
Tabel `datamart.sales_jewerly` yang menyimpan data terintegrasi hasil penggabungan tabel fakta dan dimensi untuk kebutuhan pelaporan dan ekspor ke format `.csv`.

---

## 📂 Struktur Repositori
* `sql/`: Berisi skrip DDL untuk pembuatan basis data OLTP, Staging, DWH Star Schema, dan Datamart.
* `pdi_etl/`: Berisi file alur kerja Pentaho (.kjb dan .ktr).
* `data/`: File sampel ekspor hasil pengolahan Datamart (.csv).
* `docs/`: File laporan dokumentasi lengkap proyek.# jewelry-dwh-bi
Data Warehouse &amp; Business Intelligence implementation for Jewelry database using PostgreSQL and Pentaho Data Integration (PDI).
