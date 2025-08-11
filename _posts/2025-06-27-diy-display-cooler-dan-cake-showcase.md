# **Proyek: Memanfaatkan Freezer atau Kulkas Bekas Jadi Custom Cake Showcase 300L dengan Sistem Pendingin Paksa**

## **Panduan Teknis Rekayasa Ulang Freezer Bekas Menjadi Cake Showcase Profesional dengan Sistem Pendingin Paksa, Defrost Otomatis, dan Anti-Embun**

**Disusun oleh:** Yusuf Mochamad Iskandar  
**Lokasi & Tanggal:** Bandung, 24 Juni 2025

### **Daftar Isi**

1. **Ringkasan Eksekutif & Tujuan Proyek**  
2. **Prinsip-Prinsip Fundamental Sistem Refrigerasi Komersial**  
   * 2.1 Siklus Kompresi Uap: Sebuah Pemeriksaan Mendetail  
   * 2.2 Dinamika Aliran Udara dan Perpindahan Panas dalam *Showcase*  
   * 2.3 Evaluasi Teknologi Pendingin Alternatif: Studi Kasus Termoelektrik (Peltier)  
3. **Analisis Komponen Mekanis dan Pemilihan Material**  
   * 3.1 Jantung Sistem: Pemilihan Kompresor dan Refrigeran  
   * 3.2 Unit Penukar Kalor: Desain Evaporator dan Kondensor  
   * 3.3 Sirkulasi Udara: Spesifikasi dan Pemilihan Kipas  
   * 3.4 Desain Struktural dan Material Bodi  
4. **Sistem Elektrikal, Kontrol, dan Otomasi**  
   * 4.1 Dekonstruksi Diagram Pengkabelan (*Wiring Diagram*)  
   * 4.2 Otak Sistem: Analisis Kontroler Suhu Digital  
   * 4.3 Komponen Proteksi dan Pendukung  
5. **Sintesis, Kritik, dan Rekomendasi Strategis**  
   * 5.1 Analisis Kesenjangan (Gap Analysis)  
   * 5.2 Poin-Poin Kelemahan dan Area yang Perlu Dibenahi  
   * 5.3 Rekomendasi Komprehensif untuk Langkah Selanjutnya  
6. **Panduan Eksekusi Proyek: Fabrikasi dan Perakitan**  
   * 6.1 Persiapan: Alat, Material, dan Protokol Keselamatan  
   * 6.2 Tahap Pembongkaran dan Preparasi  
   * 6.3 Fabrikasi dan Perakitan Sistem Mekanis  
   * 6.4 Instalasi Kelistrikan dan Kontrol  
   * 6.5 Perakitan Akhir dan *Finishing*  
7. **Rencana Anggaran Biaya (RAB)**  
8. **Rekomendasi Teknis untuk Proyek Tingkat Lanjut**  
   * 8.1 Pertimbangan Refrigeran Modern (R290)  
   * 8.2 Optimisasi Efisiensi Energi  
   * 8.3 Peningkatan Keamanan dan Keandalan  
9. **Rekomendasi Operasional dan Pemeliharaan**  
10. **Referensi Proyek Serupa**  
    * 10.1 Dokumentasi Tulis & Diskusi Forum  
    * 10.2 Referensi Video (Bahasa Indonesia)  
    * 10.3 Referensi Video (Bahasa Inggris)  
11. **Halaman Penutup**  
12. **Lampiran: Referensi Tautan Produk**

### **1\. Ringkasan Eksekutif & Tujuan Proyek**

Laporan ini menyajikan panduan teknis komprehensif untuk proyek rekayasa ulang (*upcycling*) sebuah unit *freezer* bekas berkapasitas 300 liter menjadi **cake showcase** custom yang fungsional. Tujuan utama proyek ini adalah untuk menciptakan unit pajangan dengan sistem pendingin modern yang mampu menjaga kesegaran produk pada rentang suhu 2°C hingga 8°C.  
Desain yang diusulkan mengadopsi sistem pendingin konveksi paksa (*forced air*) dengan aliran udara dari bawah ke atas untuk menjamin distribusi suhu yang merata. Unit ini akan dilengkapi dengan fitur-fitur krusial untuk standar komersial, termasuk sistem *defrosting* (pencairan es) otomatis dan pemanas anti-embun (*anti-fog*) pada kaca depan. Laporan ini mencakup analisis kelayakan komponen, daftar material terperinci, desain teknis, hingga estimasi anggaran biaya yang realistis untuk pengerjaan mandiri.

### **2\. Prinsip-Prinsip Fundamental Sistem Refrigerasi Komersial**

#### **2.1 Siklus Kompresi Uap: Sebuah Pemeriksaan Mendetail**

Siklus refrigerasi kompresi uap merupakan teknologi fundamental yang menjadi dasar bagi hampir semua sistem pendingin modern. Siklus ini bekerja dengan mensirkulasikan refrigeran melalui empat komponen utama dalam sebuah loop tertutup untuk memindahkan panas dari dalam *showcase* ke lingkungan luar.

1. **Kompresor:** Menghisap refrigeran dalam wujud gas bertekanan rendah, lalu menaikkan tekanan dan temperaturnya.  
2. **Kondensor:** Melepaskan panas dari refrigeran gas panas bertekanan tinggi ke lingkungan, menyebabkannya berubah fasa menjadi cairan bertekanan tinggi.  
3. **Katup Ekspansi/Pipa Kapiler:** Menurunkan tekanan refrigeran cair secara drastis, yang secara dramatis mendinginkannya menjadi campuran cair-uap dingin.  
4. **Evaporator:** Menyerap panas dari dalam kabin *showcase* saat campuran refrigeran dingin menguap menjadi gas, sehingga mendinginkan udara di dalam kabin.

Untuk analisis kuantitatif, para insinyur menggunakan **diagram Tekanan-Entalpi (P-h)** untuk memvisualisasikan kondisi termodinamika refrigeran di setiap titik dalam siklus. Pemahaman diagram ini krusial untuk mengevaluasi efisiensi dan kinerja sistem.

#### **2.2 Dinamika Aliran Udara dan Perpindahan Panas dalam *Showcase***

* **Sistem Udara Paksa (*Forced Air*):** Mayoritas *showcase* komersial menggunakan sistem ini, di mana kipas secara aktif mensirkulasikan udara dingin untuk memastikan distribusi suhu yang merata dan pendinginan yang cepat.  
* **Konsep *Air Curtain* (Tirai Udara):** Pada unit terbuka, aliran udara dingin berkecepatan terkontrol menciptakan penghalang aerodinamis untuk memisahkan udara dingin di dalam dari udara hangat di luar, mencegah pengembunan dan menjaga efisiensi.  
* **Mekanisme Perpindahan Panas:** Beban pendinginan total pada *showcase* adalah jumlah dari semua panas yang masuk melalui **konduksi** (lewat dinding dan kaca), **konveksi** (pendinginan produk oleh aliran udara), dan **radiasi** (dari lampu dan lingkungan).

#### **2.3 Evaluasi Teknologi Pendingin Alternatif: Studi Kasus Termoelektrik (Peltier)**

Teknologi Peltier, yang bekerja berdasarkan efek termoelektrik, sering muncul dalam proyek DIY karena kesederhanaannya (tanpa kompresor atau refrigeran). Namun, teknologi ini memiliki keterbatasan signifikan:

* **Efisiensi Rendah:** Koefisien Kinerja (COP) modul Peltier jauh lebih rendah dibandingkan sistem kompresi uap, terutama pada perbedaan suhu yang besar.  
* **Kapasitas Pendinginan Terbatas:** Kapasitas pendinginan per modul sangat rendah, tidak praktis untuk mendinginkan volume *showcase* komersial.  
* **Manajemen Panas Kritis:** Kinerja sisi dingin sangat bergantung pada efektivitas pembuangan panas di sisi panasnya.

**Kesimpulan:** Untuk aplikasi *cake showcase* skala komersial, sistem kompresi uap tetap menjadi pilihan teknologi yang superior dan lebih praktis.

### **3\. Analisis Komponen Mekanis dan Pemilihan Material**

#### **3.1 Jantung Sistem: Pemilihan Kompresor dan Refrigeran**

* **Kapasitas Kompresor:** Diukur dalam PK atau BTU/jam. Pemilihan kapasitas yang tepat (tidak *oversized* atau *undersized*) sangat krusial untuk efisiensi dan keawetan. Untuk proyek ini, kompresor 1/3 PK dari *freezer* bekas dianggap memadai.  
* **Merek dan Keandalan:** Merek terkemuka seperti Embraco dan Danfoss/Secop adalah standar industri karena keandalannya.  
* **Jenis Refrigeran:**  
  * **R134a:** Standar umum, namun memiliki Potensi Pemanasan Global (GWP) yang tinggi.  
  * **R290 (Propana):** Lebih ramah lingkungan dan efisien, namun bersifat mudah terbakar dan memerlukan standar keamanan yang ketat.

#### **3.2 Unit Penukar Kalor: Desain Evaporator dan Kondensor**

* **Evaporator:** Untuk sistem udara paksa, wajib menggunakan tipe **finned tube** (pipa bersirip) untuk perpindahan panas yang efisien. Ukuran harus seimbang dengan kapasitas kompresor.  
* **Kondensor:** Wajib menggunakan tipe **finned tube dengan kipas**. Ukuran harus sesuai dengan kapasitas kompresor dan total beban panas.

#### **3.3 Sirkulasi Udara: Spesifikasi dan Pemilihan Kipas**

* **CFM (Cubic Feet per Minute):** Ini adalah metrik kinerja paling penting untuk kipas. Pemilihan kipas harus didasarkan pada CFM yang dibutuhkan oleh evaporator dan kondensor, bukan hanya ukuran fisiknya.

#### **3.4 Desain Struktural dan Material Bodi**

* **Rangka:** **Hollow Galvanis** adalah pilihan ekonomis, namun **Hollow Stainless Steel** menawarkan ketahanan korosi yang jauh lebih baik untuk lingkungan lembab.  
* **Kaca:** **Kaca tempered** adalah keharusan untuk keamanan. Penggunaan kaca lapis ganda (*double pane*) dengan lapisan **Low-E** sangat direkomendasikan untuk efisiensi termal.  
* **Insulasi:** Dinding kabinet harus diisi dengan insulasi berkualitas baik seperti busa poliuretan. Pipa refrigeran juga harus diisolasi.

### **4\. Sistem Elektrikal, Kontrol, dan Otomasi**

#### **4.1 Dekonstruksi Diagram Pengkabelan (*Wiring Diagram*)**

* **Ladder Diagram:** Standar industri untuk merepresentasikan sirkuit kontrol, memisahkan sirkuit daya tinggi dan tegangan rendah.  
* **Logika Kontrol Dasar:** Termostat mengontrol kompresor dan kipas kondensor. Kipas evaporator bisa berjalan terus-menerus atau dikontrol bersama kompresor. Lampu memiliki sirkuit terpisah.

#### **4.2 Otak Sistem: Analisis Kontroler Suhu Digital**

* **Peran Kontroler:** Kontroler digital (misal: Dixell) adalah pusat komando yang mengelola suhu, siklus *defrost*, dan fungsi proteksi.  
* **Parameter Kritis:**  
  * **Set Point (St):** Suhu target.  
  * **Differential/Hysteresis (Hy):** Rentang suhu untuk mencegah *short-cycling*.  
  * **Anti-Short Cycle Delay (AC):** Waktu tunda minimum sebelum kompresor restart.  
  * **Parameter Defrost (Interval & Durasi):** Mengelola siklus pencairan es otomatis.

#### **4.3 Komponen Proteksi dan Pendukung**

* **Overload Protector & PTC Relay:** Komponen vital yang terpasang pada kompresor untuk melindunginya dari arus berlebih dan membantu proses *start-up*.  
* **Sistem Pencahayaan:** LED strip 12V/24V *waterproof* adalah pilihan paling efisien.  
* **Pemilihan Kabel:** Gunakan kabel dengan ukuran penampang yang sesuai (misal: NYM 3x1.5 mm² untuk daya utama, NYMHY 2x0.75 mm² untuk kontrol) untuk keamanan.

### **5\. Sintesis, Kritik, dan Rekomendasi Strategis**

#### **5.1 Analisis Kesenjangan (Gap Analysis)**

* **Perhitungan Beban Pendinginan:** Ini adalah kekurangan paling fundamental. Tanpa mengetahui beban panas total, pemilihan komponen menjadi spekulatif.  
* **Standar Keamanan:** Kurangnya perhatian pada standar kelistrikan, material *food-grade*, dan keamanan penanganan refrigeran.  
* **Ergonomi dan Perawatan:** Desain harus mempertimbangkan kemudahan penggunaan dan perawatan jangka panjang.

#### **5.2 Poin-Poin Kelemahan dan Area yang Perlu Dibenahi**

* **Fokus pada Komponen, Bukan Sistem:** Pendekatan rekayasa yang benar adalah "top-down", dimulai dari perhitungan kebutuhan sistem.  
* **Kurangnya Definisi Proyek yang Jelas:** Dimensi, suhu target, dan kondisi lingkungan harus ditetapkan di awal.

#### **5.3 Rekomendasi Komprehensif untuk Langkah Selanjutnya**

1. **Fase 1: Definisi dan Spesifikasi Desain:** Tentukan parameter operasi inti dan lakukan perhitungan beban pendinginan.  
2. **Fase 2: Pemilihan dan Pengadaan Komponen Berbasis Data:** Pilih komponen (kompresor, evaporator, kondensor, kipas) secara berurutan berdasarkan hasil perhitungan.  
3. **Fase 3: Perakitan, Pengujian, dan Validasi:** Prioritaskan keamanan kelistrikan. **Gunakan jasa teknisi profesional untuk proses yang melibatkan penanganan refrigeran (las, vakum, pengisian).**  
4. **Fase 4: Panduan Perawatan Jangka Panjang:** Rancang unit dengan mempertimbangkan kemudahan akses untuk perawatan.

### **6\. Daftar Peralatan Proyek**

| Kategori | Nama Alat | Fungsi Utama |
| :---- | :---- | :---- |
| **Fabrikasi & Perakitan** | Mesin Las Listrik/MIG | Menyambung rangka hollow galvanis. |
|  | Gerinda Potong & Gerinda Tangan | Memotong dan merapikan material logam. |
|  | Bor Listrik & Mata Bor Besi | Membuat lubang untuk baut dan sekrup. |
|  | Meteran, Penggaris Siku, Waterpass | Pengukuran dan memastikan kerataan struktur. |
| **Kelistrikan** | Multimeter Digital | Mengukur tegangan, arus, dan kontinuitas. |
|  | Tang Kupas Kabel (*Wire Stripper*) & Tang Potong | Mempersiapkan kabel untuk penyambungan. |
|  | Solder & Timah | Menyambung komponen elektronik kecil. |
|  | Obeng Set (Plus & Minus) | Mengencangkan terminal dan sekrup. |
| **Refrigerasi (Khusus)** | **Pompa Vakum** | Menghilangkan udara dan kelembapan dari sistem. |
|  | **Manifold Gauge Set (untuk R134a)** | Mengukur tekanan dan proses vakum/pengisian. |
|  | **Pemotong Pipa Tembaga (*Tube Cutter*)** | Memotong pipa tembaga dengan rapi. |
|  | **Alat Flaring & Swaging** | Mengembangkan ujung pipa untuk sambungan. |
|  | **Brazing Torch (Las Tembaga)** | Menyambung pipa tembaga dengan las perak. |
| **Keselamatan & Umum** | Kacamata Pelindung & Sarung Tangan | Melindungi mata dan tangan dari percikan api dan benda tajam. |
|  | Masker Pernapasan | Melindungi dari debu saat menggerinda. |
|  | Alat Pemadam Api Ringan (APAR) | Antisipasi bahaya kebakaran. |

### **7\. Rencana Anggaran Biaya (RAB)**

RAB ini disesuaikan untuk pengerjaan mandiri (DIY), dengan biaya jasa profesional dihilangkan.

| No. | Uraian Pekerjaan / Nama Part | Spesifikasi | Jumlah | Satuan | Harga Satuan (Rp) | Jumlah Harga (Rp) |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| **A** | **Sistem Refrigerasi & Kontrol** |  |  |  |  |  |
| 1 | Kompresor | Dari freezer bekas 300L | 1 | unit | 0 | 0 |
| 2 | Kondensor Set (termasuk kipas) | Untuk 1/3 HP | 1 | set | 829.000 | 829.000 |
| 3 | Evaporator | Tipe *finned tube* | 1 | unit | 954.000 | 954.000 |
| 4 | Kontroler Suhu Digital | Dixell XR60CX / setara | 1 | unit | 895.000 | 895.000 |
| 5 | Pipa, Filter, Alat Ekspansi | Pipa tembaga, filter drier, kapiler/TXV | 1 | set | 300.000 | 300.000 |
| 6 | Pemanas Defrost & Anti-Embun | Elemen pemanas | 1 | set | 250.000 | 250.000 |
|  | *Subtotal A* |  |  |  |  | **3.228.000** |
| **B** | **Sistem Sirkulasi Udara** |  |  |  |  |  |
| 1 | Kipas Evaporator | Aksial, \~15 cm, 220V | 2 | unit | 150.000 | 300.000 |
| 2 | Kipas Kondensor | Aksial, \~25 cm, 220V | 1 | unit | 200.000 | 200.000 |
|  | *Subtotal B* |  |  |  |  | **500.000** |
| **C** | **Struktur & Material** |  |  |  |  |  |
| 1 | Panel Bodi (Ruang Mesin) | Dari freezer bekas | 1 | unit | 0 | 0 |
| 2 | Rangka Hollow Galvanis | 40x40mm, tebal 1.2mm | 2 | batang | 180.000 | 360.000 |
| 3 | Kaca Tempered 8mm | Custom cut & polish (\~3.1 m²) | 3.1 | m² | 400.000 | 1.240.000 |
| 4 | Material Lain-lain | Sealant, baut, rel, kaki, isolasi, dll. | 1 | set | 350.000 | 350.000 |
| 5 | Lampu LED & Adaptor | Strip LED waterproof & adaptor | 1 | set | 250.000 | 250.000 |
|  | *Subtotal C* |  |  |  |  | **2.200.000** |
|  | **TOTAL ESTIMASI BIAYA MATERIAL (A+B+C)** |  |  |  |  | **Rp 5.928.000** |

**Catatan:** Anggaran di atas adalah estimasi material. Sangat disarankan untuk menyiapkan dana tak terduga sebesar 10-15%.

### **8\. Rekomendasi Teknis untuk Proyek Tingkat Lanjut**

Untuk mencapai hasil yang sempurna secara ilmiah dan praktis, pertimbangkan topik-topik berikut:

* **Pertimbangan Refrigeran Modern (R290):** Standar industri global bergerak menuju refrigeran dengan Potensi Pemanasan Global (GWP) yang rendah. Pertimbangkan untuk merancang sistem menggunakan **R290 (propana)** sebagai alternatif R134a. R290 memiliki efisiensi termodinamika yang sangat baik, namun bersifat mudah terbakar (*flammable*), sehingga memerlukan komponen kelistrikan yang tahan percikan (*spark-proof*) dan prosedur penanganan yang sangat hati-hati sesuai standar keselamatan.  
* **Optimisasi Efisiensi Energi:**  
  * **Motor Kipas ECM:** Ganti motor kipas standar (*shaded-pole*) dengan motor **ECM (*Electronically Commutated Motor*)**. Motor ECM secara signifikan lebih efisien, lebih senyap, dan memiliki umur pakai lebih panjang.  
  * **Kontrol *Defrost on-Demand*:** Manfaatkan sepenuhnya kemampuan kontroler digital untuk mengatur siklus *defrost* berdasarkan kebutuhan aktual (misalnya, dengan sensor tambahan), bukan hanya berdasarkan timer tetap. Ini dapat menghemat energi secara signifikan.  
* **Peningkatan Keamanan dan Keandalan:**  
  * **Kelistrikan:** Pastikan semua pengkabelan sesuai dengan standar keamanan, menggunakan ukuran kabel yang benar untuk setiap beban. Gunakan komponen proteksi seperti *overload protector* dan pastikan sistem terhubung ke tanah (*grounding*) dengan benar.  
  * **Mekanikal:** Pastikan semua sambungan pipa refrigeran telah diuji kebocorannya dengan benar (misalnya, dengan tes tekanan nitrogen dan detektor kebocoran elektronik). Amankan kompresor pada dudukan peredam getaran (*rubber mounting*) untuk mengurangi kebisingan dan getaran mekanis.

### **9\. Rekomendasi Operasional dan Pemeliharaan**

* **Praktik Terbaik:**  
  * **Penempatan:** Letakkan unit di permukaan rata dengan jarak minimal 20 cm dari dinding untuk ventilasi kondensor.  
  * **Pengisian Produk:** Jangan menghalangi kisi-kisi masuk dan keluar udara di bagian bawah kabinet untuk menjaga sirkulasi.  
  * **Penggunaan Pintu:** Minimalkan frekuensi dan durasi pintu dibuka untuk menjaga suhu tetap stabil.  
* **Jadwal Pemeliharaan:**  
  * **Bulanan:** Bersihkan koil kondensor dari debu dan kotoran menggunakan sikat lembut atau penyedot debu.  
  * **Triwulanan:** Periksa dan bersihkan bilah kipas. Cek kondisi paking (gasket) pintu.  
  * **Tahunan:** Lakukan inspeksi menyeluruh pada semua komponen.

### **10\. Referensi Proyek Serupa**

Bagian ini menyediakan beberapa referensi proyek DIY yang relevan untuk memberikan inspirasi dan wawasan teknis tambahan.

#### **10.1 Dokumentasi Tulis & Diskusi Forum**

* **Diskusi Teknis di Forum Refrigerasi:** Sebuah diskusi di forum online membahas tantangan dalam membuat *display case* custom dengan menempatkan unit pendingin di bawah. Diskusi ini sangat relevan karena menyoroti pentingnya pemilihan komponen yang seimbang, kesulitan memodifikasi sistem refrigerasi, dan kebutuhan akan alat khusus serta lisensi untuk menangani refrigeran.  
* **Panduan Membangun *Walk-in Cooler* DIY:** Beberapa panduan online merinci proses pembangunan ruang pendingin custom menggunakan unit AC standar yang dikendalikan oleh perangkat "Cool-Bot". Meskipun teknologinya sedikit berbeda, prinsip konstruksi, insulasi, dan penyegelan kabinet sangat aplikatif untuk proyek ini.

#### **10.2 Referensi Video (Bahasa Indonesia)**

* **Modifikasi Mesin AC menjadi Freezer:** Video ini mendemonstrasikan proses rekayasa ulang unit outdoor AC menjadi sistem pendingin untuk *cold room* atau *brine tank*. Konsepnya sangat relevan dengan proyek ini, yaitu memanfaatkan komponen pendingin yang ada (dalam hal ini, unit outdoor AC Sharp 1PK) untuk tujuan refrigerasi yang berbeda.  
* **Membuat Kulkas Mini dengan Peltier:** Meskipun menggunakan teknologi pendingin yang berbeda (termoelektrik/Peltier), video ini memberikan gambaran umum tentang proses perakitan sebuah unit pendingin DIY dari awal, termasuk pembuatan boks dan instalasi komponen.

#### **10.3 Referensi Video (Bahasa Inggris)**

* ***DIY Mobile Walk-in Cooler*****:** Video ini adalah panduan praktis yang menunjukkan proses pembangunan sebuah pendingin *walk-in* portabel. Pembahasan mencakup konstruksi, insulasi, dan penggunaan sistem pendingin alternatif (CoolBot dengan unit AC), serta evaluasi mengenai apa yang berhasil dan apa yang akan dilakukan secara berbeda.  
* ***Building a Walk-in Cooler with an AC unit*****:** Video ini membahas pertimbangan penting dalam membangun ruang pendingin DIY, termasuk persiapan kelistrikan (outlet 240V), pemilihan unit AC yang sesuai, dan perbandingan dengan membeli unit komersial jadi.

### **11\. Halaman Penutup**

Laporan teknis ini disusun sebagai panduan komprehensif untuk perencanaan dan pelaksanaan proyek pembuatan **cake showcase** custom. Diharapkan dokumen ini dapat menjadi referensi yang akurat dan bermanfaat dalam setiap tahap pengerjaan, mulai dari desain konseptual hingga operasional unit. Keberhasilan proyek ini bergantung pada kepatuhan terhadap spesifikasi teknis dan praktik terbaik yang diuraikan dalam laporan ini.

### **12\. Lampiran: Referensi Tautan Produk**

**Penting:** Tautan berikut adalah contoh referensi berdasarkan informasi yang tersedia dan berfungsi untuk memberikan gambaran produk. Ketersediaan stok, harga, dan reputasi penjual dapat berubah. Selalu lakukan verifikasi mandiri sebelum melakukan pembelian.

| Nama Part | Spesifikasi yang Direkomendasikan | Contoh Tautan Produk (Shopee/Tokopedia) |
| :---- | :---- | :---- |
| **Kondensor Set** | Untuk kompresor 1/3 HP, dengan kipas | [https://www.tokopedia.com/sumberberkatac/condensor-1-3-pk-sudah-include-fan-kondensor-chiller-freezer-1-3-pk-condensor-fn-alltemp](https://www.tokopedia.com/sumberberkatac/condensor-1-3-pk-sudah-include-fan-kondensor-chiller-freezer-1-3-pk-condensor-fn-alltemp) |
| **Evaporator** | Tipe *finned tube*, untuk *chiller* 250-350L | [https://shopee.co.id/Evaporator-chiller-showcase-i.239559897.16856615650](https://shopee.co.id/Evaporator-chiller-showcase-i.239559897.16856615650) |
| **Kontroler Suhu Digital** | Dixell XR60CX atau setara | [https://www.tokopedia.com/terbaiktronics/dixell-xr60cx-5n0c0-230-vac-thermostat-digital-controller-emerson](https://www.tokopedia.com/terbaiktronics/dixell-xr60cx-5n0c0-230-vac-thermostat-digital-controller-emerson) |
| **Sensor Suhu (NTC)** | Kompatibel dengan kontroler Dixell, 10K Ohm | (https://shopee.co.id/Sensor-Suhu-Thermostat-Raksa-Temperature-Controller-Elitech-Eliwell-Dixell-Hitam-Kabel-10-K-Ohm-i.141005581.25312509349) |
| **Pemanas Defrost** | Elemen pemanas kaca, universal | [https://www.tokopedia.com/anekaacmobil/heater-kaca-kulkas-showcase-2-pintu-10-inch-universal-semua-merk](https://www.tokopedia.com/anekaacmobil/heater-kaca-kulkas-showcase-2-pintu-10-inch-universal-semua-merk) |
| **Pemanas Kaca Anti-Embun** | Tipe pemanas mobil 12V (memerlukan adaptor terpisah) | [https://www.tokopedia.com/grosir-jam-tangan/pemanas-kaca-mobil-anti-embun-anti-foging](https://www.tokopedia.com/grosir-jam-tangan/pemanas-kaca-mobil-anti-embun-anti-foging) |
| **Kipas Evaporator** | Aksial, \~15 cm, 220V | [https://www.tokopedia.com/jagoan-pendingin/kipas-fan-ac-220v-220-volt-15-cm-15cm](https://www.tokopedia.com/jagoan-pendingin/kipas-fan-ac-220v-220-volt-15-cm-15cm) |
| **Kipas Kondensor** | Aksial, \~25 cm (10 inci), 220V | [https://www.tokopedia.com/sentralpartsac/exhaust-fan-panasonic-fv-25tgu5-10-panasonic-25-tgu-25tgu](https://www.tokopedia.com/sentralpartsac/exhaust-fan-panasonic-fv-25tgu5-10-panasonic-25-tgu-25tgu) |
| **Rangka Hollow Galvanis** | 40x40mm, tebal 1.2mm | [https://www.tokopedia.com/sinar-baja-sakti/besi-hollow-galvanis-1-2mm-20x40-40x40-40x60-40x80-50x100-6-meter-40-x-40](https://www.tokopedia.com/sinar-baja-sakti/besi-hollow-galvanis-1-2mm-20x40-40x40-40x60-40x80-50x100-6-meter-40-x-40) |
| **Kaca Tempered 8mm** | Custom per m² | [https://www.tokopedia.com/elitetoys/kaca-tempered-clear-8mm](https://www.tokopedia.com/elitetoys/kaca-tempered-clear-8mm) |
| **Lampu LED Strip** | 12V, Warm White, Waterproof | [https://www.tokopedia.com/sumber-rejekiled/lampu-led-strip-5050-ip44-12v-outdoor-ledstrip-ip-44-warm-white-12-v](https://www.tokopedia.com/sumber-rejekiled/lampu-led-strip-5050-ip44-12v-outdoor-ledstrip-ip-44-warm-white-12-v) |
| **Adaptor LED** | 12V, 5A (60W) | [https://www.tokopedia.com/solusirumahku/power-supply-adaptor-switching-trafo-led-strip-12v-5a-12-volt-5-ampere](https://www.tokopedia.com/solusirumahku/power-supply-adaptor-switching-trafo-led-strip-12v-5a-12-volt-5-ampere) |
| **Overload Protector & Relay PTC** | Untuk kompresor 1/3 HP | [https://www.tokopedia.com/snqelektronik/overload-kulkas-frezer-showcase-1-3-pk-230-watt-sampai-250-watt](https://www.tokopedia.com/snqelektronik/overload-kulkas-frezer-showcase-1-3-pk-230-watt-sampai-250-watt) |
| **Pipa Kapiler** | Ukuran 0.70 mm | [https://www.tokopedia.com/megateknikac/pipa-kapiler-tembaga-0-70](https://www.tokopedia.com/megateknikac/pipa-kapiler-tembaga-0-70) |

#### **Karya yang dikutip**

1\. 48inch Long Refrigerated Cake Showcase with Embraco / Danfoss ..., https://ahsocool.en.made-in-china.com/product/SNcxUysvMgkW/China-48inch-Long-Refrigerated-Cake-Showcase-with-Embraco-Danfoss-Compressor.html 2\. huggingface.co, https://huggingface.co/adriansyahdr/adrbert-base-p1/commit/201367aca7ccdd367ea414ae364ff9a9f084e815.diff?file=vocab.txt 3\. Tidak berjudul \- Hugging Face, https://huggingface.co/tepanee/indoxlnet/commit/dd1664fcd2cc533f0d19911d5620bbdd65e74956.diff?file=sp10m.base.uncased.indoNLU.vocab 4\. Refrigeration U: The Basic Refrigeration Cycle \- Master-Bilt Commercial Refrigeration Products, https://master-bilt.com/general-information/news/refrigeration-u-the-basic-refrigeration-cycle/ 5\. Mengenal Komponen Kulkas & Cara Kerjanya Menghasilkan Dingin | AQUA Elektronik, https://aquaelektronik.com/article/detail/392/Mengenal+Komponen+Kulkas 6\. The Refrigeration Cycle \- In easy to understand descriptions & diagrams\! \- Torr Engineering, https://www.torr-engineering.com/the-refrigeration-cycle/ 7\. The 4 Main Refrigeration Cycle Components | The Super Blog, https://www.superradiatorcoils.com/blog/4-main-refrigeration-cycle-components 8\. Guide on Displaying Your Bakery Items \- ESCOLO, https://www.easymancool.com/resources/guide-on-displaying-your-bakery-items.html 9\. Cake Display | ALF FROST, https://www.alffrost.com/cake-display/ 10\. USER MANUAL \- Trufrost, https://trufrost.com/assets/Display-Showcases-User-Manual.pdf 11\. PROGRAM STUDI TEKNIK MESIN FAKULTAS TEKNIK UNIVERSITAS ISLAM RIAU PEKANBARU 2020, https://repository.uir.ac.id/16870/1/133310324.pdf 12\. Jual Mesin Pendingin Showcase Kue / Showcase Cold FOMAC SHC-TTF80F \- Shopee, https://shopee.co.id/Mesin-Pendingin-Showcase-Kue-Showcase-Cold-FOMAC-SHC-TTF80F-i.111090144.9421009169 13\. Mesin Pendingin Showcase Kue / Showcase Cold FOMAC SHC-TTF100F \- Tokopedia, https://www.tokopedia.com/markasmesin/mesin-pendingin-showcase-kue-showcase-cold-fomac-shc-ttf100f 14\. Bagaimana Cara Kerja Showcase Cooler? \- Jaya Agung Mesin, https://jayaagungmesin.com/cara-kerja-showcase-cooler/ 15\. COUNTER TOP CAKE SHOWCASE SHC-CFTW120L | Fomac, https://www.fomac.co.id/produk/counter-top-cake-showcase-SHC-CFTW120L 16\. SPECIFICATIONS FOR WALK-IN COOLERS & FREEZERS, https://www.americanwalkincoolers.com/wp-content/uploads/2019/10/AWIC-Product-Information.pdf 17\. Thin Profile ETL Reach-In Cooler Evaporator 2 Fans Blower 1300 BTU 220CFM 115V, https://www.ebay.com/itm/185845623944 18\. Controls \- Refrigeration Basics, https://www.refrigerationbasics.com/RBIII/controls1.htm 19\. Komponen Utama Pada Kulkas Dan Fungsinya | PDF \- Scribd, https://id.scribd.com/document/789139288/Komponen-Utama-pada-Kulkas-dan-Fungsinya 20\. cedars.cpuc.ca.gov, https://cedars.cpuc.ca.gov/deer-resources/deemed-measure-packages/measure-package-archive/file/2046/download/ 21\. I need advice on a custom made display refrigerator. Info inside. \- Reddit, https://www.reddit.com/r/refrigeration/comments/1z6dx1/i\_need\_advice\_on\_a\_custom\_made\_display/ 22\. How to Build a DIY Walk in Cooler With Floor, https://blog.mrwinterinc.net/how-to-build-a-diy-walk-in-cooler-with-a-floor 23\. Building a Walk-in Cooler | Tom's Gardens \- WordPress.com, https://tomsgardens.wordpress.com/my-homemade-walk-in-cooler/ 24\. Jual Led Strip Warm White Terbaik \- Harga Murah Juni 2025 & Cicil 0% | Tokopedia, https://www.tokopedia.com/find/led-strip-warm-white?utm\_source=google\&utm\_medium=organic\&utm\_campaign=find 25\. modifikasi mesin ac menjadi mesin freezer coldroom brine tank / air garam \- YouTube, https://www.youtube.com/watch?v=q4L2QGGeHpo