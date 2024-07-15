# Paket-Prabayar-Manakah-yang-Lebih-Baik

**Pendahuluan <a id='intro'></a>**

Sebagai seorang analis di perusahaan operator telekomunikasi bernama Megaline, proyek ini bertujuan untuk menentukan paket prabayar yang menghasilkan pendapatan lebih tinggi berdasarkan analisis data dari 500 pelanggan. Data tersebut mencakup informasi pelanggan, asal, jenis paket, serta aktivitas panggilan dan pesan pada tahun 2018. Tujuan utama proyek ini adalah membantu perusahaan mengoptimalkan pendapatan dan anggaran iklan mereka dengan memahami perilaku pelanggan.

**Tujuan:**

* Dengan mencapai tujuan-tujuan ini, proyek ini diharapkan dapat membantu Megaline dalam meningkatkan pendapatan mereka dan mengambil keputusan yang lebih baik dalam pengelolaan paket prabayar mereka.
* Menganalisis perilaku pelanggan Megaline berdasarkan data yang ada, termasuk jenis paket yang mereka gunakan, jumlah panggilan, pesan, dan penggunaan data selama tahun 2018.
* Mengidentifikasi paket prabayar yang menghasilkan pendapatan lebih tinggi untuk perusahaan Megaline.
* Memberikan rekomendasi kepada departemen periklanan Megaline untuk mengalokasikan anggaran iklan dengan lebih efektif berdasarkan temuan analisis.
* Mengoptimalkan strategi pemasaran dan penawaran paket prabayar kepada pelanggan berdasarkan pemahaman lebih baik tentang preferensi dan perilaku pelanggan.

Proyek ini bertujuan untuk menganalisis perilaku klien dan menentukan paket prabayar mana yang mendatangkan lebih banyak pendapatan. Berikut rincian yang akan kita lewati:

**Deskripsi paket prabayar**

Catatan: Megaline membulatkan detik ke menit dan megabyte ke gigabyte. Untuk panggilan, setiap panggilan individual dibulatkan ke atas: bahkan jika suatu panggilan berlangsung hanya satu detik, panggilan tersebut akan dihitung sebagai satu menit. Untuk traffic web, setiap sesi web individual tidak dibulatkan ke atas. Akan tetapi, total untuk sebulan dibulatkan ke atas. Jika seorang pengguna menghabiskan 1025 megabyte bulan ini, dia pun akan dikenai biaya untuk 2 gigabyte.

**Paket Surf**

1. Biaya Bulanan: US 20 (US dollar)
2. Paket Bulanan: 
   - 500 menit durasi panggilan per bulan
   - 50 SMS
   - 15 GB data
3. Biaya Tambahan Setelah Melebihi Batas Paket:
   - 1 menit: 3 sen
   - 1 SMS: 3 sen
   - 1 GB data: $10


**Paket Ultimate**

1. Biaya Bulanan: US 70 (US dollar)
2. Paket Bulanan: 
   - 3000 menit durasi panggilan per bulan
   - 1000 SMS
   - 30 GB data
3. Biaya Tambahan Setelah Melebihi Batas Paket:
   - 1 menit: 1 sen
   - 1 SMS: 1 sen
   - 1 GB data: $7
   
**Tahapan yang Dilakukan**

**Langkah 1: Analisis Dataset**

- Melakukan analisis dataset pada beberapa file path berikut:
   - `/datasets/megaline_calls.csv`.
   - `/datasets/megaline_internet.csv`.
   - `/datasets/megaline_messages.csv`.
   - `/datasets/megaline_plans.csv`.
   - `/datasets/megaline_users.csv`.

**Langkah 2: Menyiapkan Data**

* Konversikan data menjadi tipe data yang dibutuhkan
* Temukan dan eliminasi kesalahan pada data, kemudian, jelaskan kesalahan yang ditemukan dan bagaimana mengeliminasinya.

**Catatan:** ada sejumlah panggilan yang memiliki durasi 0,0 menit. Ini mungkin adalah panggilan tak terjawab. Apakah data tersebut akan dieliminasi untuk nilai-nilai ini atau tidak. Perlu diingat, jangan lupa untuk mempertimbangkan seberapa besar ketidakhadiran nilai-nilai ini akan memengaruhi hasil analisis saya.

Untuk setiap pengguna, temukan:
* Jumlah panggilan yang dilakukan dan menit yang digunakan per bulan
* Jumlah SMS yang dikirim per bulan
* Volume data per bulan
* Hitung pendapatan bulanan dari setiap pengguna (caranya, kurangi batas paket gratis dari jumlah total panggilan, pesan teks, dan data; kalikan hasilnya dengan nilai paket panggilan; tambahkan biaya bulanan berdasarkan pada jenis paket panggilan)

**Langkah 3: Analisis Data**

Deskripsikan perilaku konsumen. Temukan menit, pesan, dan volume penggunaan data seluler yang dibutuhkan pengguna setiap paket per bulan. Hitung rata-rata, varians, dan standar deviasinya. Buat histogram. Deskripsikan distribusinya

**Langkah 4. Uji hipotesis**

* Rata-rata pendapatan dari pengguna paket telepon Ultimate dan Surf berbeda.
* Rata-rata pendapatan dari pengguna di wilayah NY-NJ berbeda dengan pendapatan pengguna dari wilayah lain.

Menentukan seberapa besar nilai "alpha" yang akan digunaka

Menjelaskan:
* Bagaimana kamu merumuskan hipotesis nol dan hipotesis alternatif.
* Kriteria apa yang kamu gunakan untuk menguji hipotesis dan alasanmu menggunakannya.

**Langkah 5. Tulis kesimpulannya secara menyeluruh**

**Deskripsi Data**

**Tabel `users` (data pengguna):**
- user_id — ID pengguna
- first_name — nama depan pengguna
- last_name — nama belakang pengguna
- age — usia pengguna (tahun)
- reg_date — tanggal mulai berlangganan (dd, mm, yy)
- churn_date — tanggal pengguna berhenti menggunakan layanan (jika nilainya hilang atau tidak ada, berarti paket layanan sedang digunakan saat data ini dibuat)
- city — kota tempat tinggal pengguna
- plan — nama paket telepon

**Tabel `calls` (data panggilan):**
- id — ID panggilan unik
- call_date — tanggal panggilan
- duration — durasi panggilan (dalam menit)
- user_id — ID pengguna yang melakukan panggilan

**Tabel `messages` (data SMS):**
- id — ID SMS unik
- message_date — tanggal SMS dikirim
- user_id — ID pengguna yang mengirim SMS

**Tabel `internet` (data sesi web):**
- id — ID sesi web unik
- mb_used — volume data yang dihabiskan selama sesi (dalam megabyte)
- session_date — tanggal sesi web
- user_id — ID pengguna

**Tabel `plans` (data paket telepon):**
- plan_name — nama paket telepon
- usd_monthly_fee — biaya bulanan dalam dolar AS
- minutes_included — alokasi menit panggilan bulanan
- messages_included — alokasi SMS bulanan
- mb_per_month_included — alokasi volume data bulanan (dalam megabyte)
- usd_per_minute — harga per menit jika sudah melebihi batas alokasi paket (misalnya, jika paket memiliki alokasi 100 menit maka penggunaan mulai dari menit ke-101 akan dikenakan biaya)
- usd_per_message — harga per SMS jika sudah melebihi batas alokasi paket
- usd_per_gb — harga per gigabyte tambahan data jika sudah melebihi batas alokasi paket (1 GB = 1024 megabyte)
