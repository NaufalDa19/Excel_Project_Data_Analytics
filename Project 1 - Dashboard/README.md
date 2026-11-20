# Excel Salary Dashboard
![](https://github.com/user-attachments/assets/27fb8dd3-491b-4e92-afb2-3f76ee74e93a)

## :one: Pendahuluan
Dashboard ini dibuat untuk membantu pencari kerja melihat kisaran gaji untuk posisi data job yang mereka incar, sehingga bisa menilai apakah tawaran gaji yang diterima layak.

Datanya berasal dari course Excel yang saya ikuti, berupa data lowongan tahun 2023 yang memuat informasi posisi (job title), gaji, negara, jenis pekerjaan, dan platform lowongan. Dari data ini saya membangun dashboard interaktif yang menampilkan median gaji, platform lowongan teratas, dan jumlah lowongan sesuai filter yang dipilih.

### :one: File Dashboard
Dashboard final saya ada di [Salary Dashboard](salary_dashboard.xlsx)

### :two: Skill Excel yang Digunakan
Skill Excel berikut dipakai untuk analisis:
- 📉 **Chart**
- 🧮 **Rumus dan Fungsi**
- ❎ **Data Validation**

### :three: Dataset Data Jobs
Dataset yang dipakai di proyek ini berisi informasi lowongan Data Science dari dunia nyata tahun 2023. Dataset ini tersedia lewat course Excel Luke Barousse ([lukebarousse.com/excel](https://www.lukebarousse.com/excel)), yang menjadi dasar untuk berlatih menganalisis data dengan Excel. Isinya mencakup informasi rinci tentang:
- 🧑‍💼 **Job Title** (posisi)
- 💰 **Gaji**
- 📍 **Lokasi**
- 🛠️ **Skill**

## :two: Pembuatan Dashboard
### 📉 Chart
#### 📊 Bar Chart Gaji Pekerjaan Data Science
![](https://github.com/user-attachments/assets/74cf2bd0-edf4-4770-bcc3-0865d668e13c)

- 🛠️ **Fitur Excel:** Menggunakan fitur bar chart (dengan format nilai gaji) dan tata letak yang dirapikan agar mudah dibaca.
- 🎨 **Pilihan Desain:** Bar chart horizontal untuk membandingkan median gaji antar posisi secara visual.
- 📉 **Pengorganisasian Data:** Job title diurutkan dari gaji tertinggi ke terendah agar lebih mudah dibaca.
- 💡 **Insight yang Didapat:** Dari chart ini, tren gaji bisa dilihat dengan cepat. Dalam data ini, posisi Senior dan Engineer bergaji lebih tinggi daripada posisi Analyst.

#### 🗺️ Median Gaji Berdasarkan Negara - Map Chart
![](https://github.com/user-attachments/assets/698bb4a9-fccd-4aea-92a8-30c9a62ba046)

- 🛠️ **Fitur Excel:** Menggunakan fitur map chart di excel untuk memvisualisasikan median gaji secara global
- 🎨 **Pilihan Desain:** Map chart dengan gradasi warna biru muda hingga biru tua untuk menampilkan perbedaan gaji antarnegara.
- 📉 **Pengorganisasian Data:** Pemetaan median gaji pada setiap negara dengan data yang tersedia.
- 👁️ **Penyempurnaan Visual:** Meningkatkan keterbacaan visual (readability) dan pemahaman langsung terhadap tren gaji secara geografis.
- 💡 **Insight yang Didapat:** Mengidentifikasi kesenjangan gaji serta menampilkan rentang gaji terendah hingga tertinggi antarnegara.

### 🧮 Rumus dan Fungsi
#### 💰 Median Gaji Berdasarkan Job Title

```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

- 🔍 **Filter Multikriteria:** Menyaring data berdasarkan *job title*, negara, dan tipe jadwal kerja, sekaligus mengabaikan baris yang nilai gajinya masih kosong.
- 📊 **Array Formula:** Menggabungkan fungsi `MEDIAN()` dengan logika `IF()` bersarang untuk memproses sekumpulan data (*array*) secara langsung.
- 🎯 **Insight Spesifik:** Menghasilkan gambaran gaji yang terarah sesuai kombinasi *job title*, wilayah, dan tipe jadwal tertentu.
- 🔢 **Tujuan Rumus:** Mengisi tabel di bawahnya dengan nilai median gaji yang disesuaikan menurut *job title*, negara, serta tipe yang dipilih.

🍽️ Tabel Pendukung

<img width="265" height="220" alt="1_Salary_Dashboard_Screenshot1" src="https://github.com/user-attachments/assets/dd45d5ce-a569-4a9d-9ddd-48cfa892ba01" />

📉 Implementasi Dashboard

<img src="https://github.com/user-attachments/assets/3a2d6030-7de3-4cd3-9caa-84b64806e619" width="400" height="500" alt="Salary Dashboard Title" />

#### ⏰ Jumlah Job Schedule Type

```
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

- 🔎 **Unique List Generation:** Rumus Excel di bawah ini memanfaatkan fungsi `FILTER()` untuk menyaring data dengan mengecualikan entri yang mengandung `"and"` atau tanda koma, serta mengabaikan nilai nol.
- 🔢 **Tujuan Rumus:** Rumus ini mengisi tabel di bawahnya untuk menghasilkan daftar *job schedule type* yang unik.

🍽️ Tabel Pendukung

<img width="195" height="119" alt="1_Salary_Dashboard_Screenshot2" src="https://github.com/user-attachments/assets/88f88b08-8499-4f12-9ed5-701ae4f94ede" />

📉 Implementasi Dashboard

<img src="https://github.com/user-attachments/assets/3ad84945-6818-41a0-bae2-f9e0bec7da26" width="400" height="500" alt="Salary Dashboard Title" />

### ❎ Validasi Data

#### 🔎 Daftar Terfilter

- 🔒 **Validasi Data yang Lebih Terarah:** Menerapkan daftar yang sudah difilter sebagai aturan *data validation* pada opsi `Job Title`, `Country`, dan `Type` di tab *Data* membantu:
  - 🎯 Membatasi input pengguna hanya pada tipe jadwal yang sudah tersedia dan tervalidasi
  - 🚫 Mencegah entri yang keliru atau tidak konsisten
  - 👥 Meningkatkan kenyamanan dan kepraktisan penggunaan *dashboard* secara keseluruhan

<img src="https://github.com/user-attachments/assets/ecf1c462-6133-4c6a-82c9-525e4cb0437d" width="425" height="400" alt="Salary Dashboard Data Validation" />

## Kesimpulan

Dashboard ini dibuat untuk menampilkan insight tren gaji di berbagai job title bidang data. Menggunakan dataset dari course Excel, dashboard ini membantu pengguna mengambil keputusan yang lebih tepat terkait jalur karier mereka sekaligus melihat bagaimana lokasi dan tipe pekerjaan memengaruhi besaran gaji.
