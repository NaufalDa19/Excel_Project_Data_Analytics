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
- 🧑‍💼 **Job title** (posisi)
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

- d
- d
- d
- d

