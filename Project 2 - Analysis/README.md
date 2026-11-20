# Analisis Proyek 2

## Pendahuluan

Analisis ini disusun untuk membantu melihat pola *skill* dan tingkat gaji di pasar kerja *data science*, sehingga bisa menjadi gambaran mengenai kebutuhan industri dan cara meraih kompensasi yang lebih kompetitif.

Datanya berasal dari *course* Excel yang saya ikuti, berupa data lowongan kerja tahun 2023 yang memuat informasi posisi (*job title*), gaji, lokasi, dan *skill*. Dari data ini saya melakukan pengolahan dan analisis di Excel menggunakan Power Query, PivotTable, DAX, dan grafik untuk melihat hubungan antara jumlah *skill*, wilayah, *skill* teratas, serta kisaran gaji sesuai topik yang dibahas.

### Pertanyaan yang Dianalisis

Untuk memetakan dinamika pasar kerja di bidang *data science*, analisis ini diarahkan pada empat pertanyaan utama:

1. **Apakah semakin banyak *skill* berkaitan dengan gaji yang lebih besar?**
2. **Bagaimana gambaran gaji untuk posisi data di berbagai wilayah?**
3. **Apa saja *skill* teratas yang paling banyak dimiliki praktisi data?**
4. **Berapa kisaran gaji untuk 10 *skill* teratas tersebut?**

### Skill Excel yang Digunakan

Beberapa kemampuan di Microsoft Excel dimanfaatkan sepanjang proses analisis ini:

- **📊 PivotTable**
- **📈 PivotChart**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Dataset Lowongan Data

*Dataset* pada proyek ini bersumber dari informasi lowongan kerja *data science* di dunia nyata pada tahun 2023 dan diperoleh melalui *course* Excel yang saya ikuti sebagai bahan latihan pengolahan data di Excel.

Isi datanya mencakup rincian mengenai:

- **👨‍💼 Job title**
- **💰 Gaji**
- **📍 Lokasi**
- **🛠️ Skill**

## 1️⃣ Apakah semakin banyak *skill* berkaitan dengan gaji yang lebih besar?

### 🔍 Skill: Power Query (ETL)

#### 📥 Extract

- Tahap awal dimulai dengan menarik data mentah dari `data_salary_all.xlsx` lewat Power Query untuk memecahnya menjadi dua *query*:
  - 🗃️ *Query* pertama memuat keseluruhan informasi lowongan pekerjaan data.
  - 🔧 *Query* kedua merinci daftar *skill* berdasarkan masing-masing ID lowongan.

#### 🔄 Transform

- Selanjutnya, setiap *query* dirapikan melalui penyesuaian tipe data kolom, penghapusan kolom yang tidak diperlukan, pembersihan teks dari kata tertentu, serta perapian spasi berlebih.
  - 📊 data_jobs_all
    
      ![2_Project_Analysis_Screenshot1.png](https://github.com/user-attachments/assets/d880793f-f198-4da9-ad1d-0b913d041a33)
    
  - 🛠️ data_job_skills

      ![2_Project_Analysis_Screenshot2.png](https://github.com/user-attachments/assets/3d82a6cc-8938-41df-a250-a46789bd211c)

#### 🔗 Load

- Pada tahap akhir, kedua *query* hasil pembersihan dimuat ke dalam *workbook* sebagai pijakan untuk analisis lanjutan.
  - 📊 data_jobs_all

      ![2_Project_Analysis_Screenshot3.png](https://github.com/user-attachments/assets/e97ee252-25a1-424b-a68e-ced084b5ea74)
    
  - 🛠️ data_job_skills

      ![2_Project_Analysis_Screenshot4.png](https://github.com/user-attachments/assets/bf77fb87-2b63-43c6-8ec2-7d1a616ef7c2)

### 📊 Analisis

#### 💡 Temuan Analisis

- 📈 Semakin banyak jumlah *skill* yang dicantumkan pada lowongan, nilai median gajinya cenderung ikut meningkat—terutama pada peran seperti Senior Data Engineer dan Data Scientist.
- 💼 Posisi dengan tuntutan *skill* yang lebih sedikit, seperti Business Analyst, umumnya menawarkan gaji yang lebih rendah, menandakan bahwa kombinasi *skill* yang lebih spesifik bernilai lebih tinggi di pasar.

![2_Project_Analysis_Chart1.png](https://github.com/user-attachments/assets/a2c7d064-17ef-4261-b46f-973d4fb64e33)

#### 🤔 Implikasinya

- Pola ini menegaskan pentingnya memperluas penguasaan *skill* yang relevan, khususnya bagi siapa pun yang menargetkan posisi dengan kompensasi lebih besar.

## 2️⃣ Bagaimana gambaran gaji untuk posisi data di berbagai wilayah?

### 🧮 Skill: PivotTable & DAX

#### 📈 PivotTable

- 🔢 PivotTable disusun menggunakan Data Model yang sudah dibangun melalui Power Pivot.
- 📊 Kolom `job_title_short` ditempatkan pada area *rows*, sedangkan `salary_year_avg` dimasukkan ke area *values*.
- 🧮 Setelah itu ditambahkan *measure* baru guna menghitung nilai median gaji khusus untuk lowongan di Amerika Serikat.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```

#### 🧮 DAX

- Perhitungan median gaji tahunan secara umum dilakukan dengan formula DAX berikut.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### 📊 Analisis

#### 💡 Temuan Analisis

- 💼 Peran seperti Senior Data Engineer dan Data Scientist mencatatkan median gaji yang tinggi baik di AS maupun di luar AS, menunjukkan permintaan global yang kuat terhadap keahlian data tingkat lanjut.
- 💰 Selisih gaji antara posisi di AS dan non-AS terlihat cukup mencolok pada pekerjaan berteknologi tinggi, yang kemungkinan dipengaruhi oleh pemusatan industri teknologi di AS.

    ![2_Project_Analysis_Chart2.png](https://github.com/user-attachments/assets/bbe8a361-57d4-42b1-b451-21ec7668eeca)

#### 🤔 Implikasinya

- Gambaran perbedaan gaji ini berguna untuk perencanaan karier maupun negosiasi kompensasi agar penawaran selaras dengan standar pasar dan kondisi geografis.

## 3️⃣ Apa saja *skill* teratas yang paling banyak dimiliki praktisi data?

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 Tabel `data_jobs_all` dan `data_jobs_skills` digabungkan ke dalam satu Data Model terpadu.
- 🧹 Karena pembersihan data sudah dilakukan sebelumnya di Power Query, relasi antar kedua tabel dapat terbentuk dengan rapi di Power Pivot.

#### 🔗 Data Model

- Keterkaitan antar kedua tabel dihubungkan melalui kolom `job_id`.

    ![2_Project_Analysis_Screenshot5.png](https://github.com/user-attachments/assets/949fb2fe-c2ef-4ca5-97d5-8dffa30b4deb)

#### 📃 Menu Power Pivot

- Menu Power Pivot dimanfaatkan untuk menyempurnakan Data Model sekaligus mempermudah pembuatan *measure*.

    ![2_Project_Analysis_Screenshot6.png](https://github.com/user-attachments/assets/abd1a601-fa7b-4d4c-b2dd-0eaee1ae3db6)

### 📊 Analisis

#### 💡 Temuan Analisis

- 💻 SQL dan Python tampil paling dominan di deretan *skill* utama bidang data, sejalan dengan peran keduanya sebagai fondasi pengolahan dan analisis data.
- ☁️ Teknologi berbasis *cloud* seperti AWS dan Azure juga muncul cukup menonjol, mencerminkan pergeseran industri ke arah layanan *cloud* dan *big data*.

    ![2_Project_Analysis_Chart3.png](https://github.com/user-attachments/assets/8d1220d4-165a-4139-b7a5-bf9be37b6605)

#### 🤔 Implikasinya

- Memahami *skill* yang paling banyak dibutuhkan membantu praktisi tetap kompetitif sekaligus memberi arah bagi program pelatihan untuk memprioritaskan teknologi yang paling berdampak.

## 4️⃣ Berapa kisaran gaji untuk 10 *skill* teratas tersebut?

### 📊 Skill: Visualisasi Lanjutan (PivotChart)

#### 📈 PivotChart

- Dibuat *combo* PivotChart dari PivotTable untuk memplot median gaji dan persentase peluang *skill* (*skill likelihood*).
  - 🪙 **Sumbu Utama (*Primary Axis*):** Median Salary (dalam format Clustered Column)
  - 👍 **Sumbu Kedua (*Secondary Axis*):** Skill Likelihood (dalam format Line with Markers)
- Tampilan grafik disesuaikan dengan menambahkan judul sumbu, menyembunyikan garis *skill likelihood*, serta mengubah bentuk *marker* menjadi *diamond*.

### 📊 Analisis

#### 💡 Temuan Analisis

- 💰 Median gaji yang lebih tinggi banyak berkaitan dengan *skill* seperti Python, Oracle, dan SQL, menandakan peran pentingnya di posisi teknologi bergaji besar.
- 📉 *Skill* seperti PowerPoint dan Word berada di posisi terbawah untuk median gaji maupun *likelihood*, yang mengindikasikan tingkat spesialisasi dan permintaan yang lebih rendah pada sektor bergaji tinggi.

    ![2_Project_Analysis_Chart4.png](https://github.com/user-attachments/assets/de1be6ac-6681-4d8e-b35a-3223ef948f00)

#### 🤔 Implikasinya

- Grafik ini mempertegas manfaat mengalokasikan waktu untuk mempelajari *skill* bernilai tinggi seperti Python dan SQL yang terbukti selaras dengan peran bergaji lebih besar, khususnya bagi yang ingin mengoptimalkan penghasilan di industri teknologi.

## Kesimpulan

## Kesimpulan

Melalui proyek latihan berbasis Excel ini, saya mengasah kemampuan pengolahan dan analisis data sekaligus membaca gambaran tren *skill* serta gaji di pasar kerja *data science*. Dengan memanfaatkan *dataset* dari *course* Excel yang mencakup *job title*, gaji, lokasi, dan *skill*, penggunaan fitur seperti Power Query, PivotTable, DAX, dan grafik membantu melihat bahwa penguasaan ragam *skill*—khususnya Python, SQL, serta teknologi *cloud*—cenderung berkaitan dengan tingkat kompensasi yang lebih tinggi.

Harapannya, dokumentasi ini menjadi catatan latihan yang rapi sekaligus membantu memberi gambaran mengenai *skill* yang relevan untuk dicermati pada peran di bidang data.
