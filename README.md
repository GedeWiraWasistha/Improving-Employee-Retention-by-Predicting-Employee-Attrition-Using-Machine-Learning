# Retention Insights: Machine Learning Powered Employee Retention Analysis

## Latar Belakang
Sumber daya manusia (SDM) adalah aset utama yang perlu dikelola dengan baik oleh perusahaan agar tujuan bisnis dapat tercapai dengan efektif dan efisien. Pada kesempatan kali ini, kita akan menghadapi sebuah permasalahan tentang sumber daya manusia yang ada di perusahaan. Fokus kita adalah untuk mengetahui bagaimana cara menjaga karyawan agar tetap bertahan di perusahaan yang ada saat ini yang dapat mengakibatkan bengkaknya biaya untuk rekrutmen karyawan serta pelatihan untuk mereka yang baru masuk. Dengan mengetahui faktor utama yang menyebabkan karyawan tidak merasa, perusahaan dapat segera menanggulanginya dengan membuat program-program yang relevan dengan permasalahan karyawan.

## Dataset
Data yang digunakan dalam analisis tersedia dalam berkas "hotel_bookings_data.csv". Yang terdiri dari 287 baris, 25 kolom

## EDA & Data Preprocessing
- Handling Missing Values
  - Dalam pengelolaan data, saya telah mengambil langkah-langkah yang tepat untuk menangani nilai yang hilang. Kolom 'SkorKepuasanPegawai', 'JumlahKeikutsertaanProjek', 'JumlahKetidakhadiran' dan 'JumlahKeterlambatanSebulanTerakhir' diisi dengan nilai median karena adanya skewness.
  - Sementara itu, kolom 'AlasanResign' yang kategorikal diisi dengan mode karena nilai kosong dapat diidentifikasi sebagai status masih bekerja melalui 'TanggalResign'.  
  - Dan Kolom 'IkutProgramLOP' dihapus karena terlalu banyak missing value, guna untuk menjaga integritas dan relevansi data untuk analisis selanjutnya.
- Mengganti value yang tidak sesuai
  - Pada kolom 'Pernah Bekerja', terdapat satu baris yang memuat nilai 'yes', sedangkan baris lainnya mengandung angka '1'. Dalam konteks ini, saya telah melakukan perubahan untuk mengkonsolidasikan data dengan menggantikan nilai 'yes' dengan '1'.
- Membuang data yang memiliki satu nilai unique
  - Kolom 'Pernah Bekerja' hanya memiliki satu nilai unik. Oleh karena itu, dalam rangka menjaga kualitas permodelan yang akan kita lakukan ke depan, saya merekomendasikan untuk menghapus kolom ini.

## Annual Report on Employee Number Changes 
![1  Annual Report on Employee Number Changes](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/9820a91e-1597-42a6-bf49-0a58f7887a40)

Dari hasil visualisasi menggunakan Waterfall Chart, terlihat bahwa penurunan jumlah karyawan dimulai pada tahun 2016. Analisis total perubahan per tahun didasarkan pada selisih antara jumlah karyawan yang bertahan dan jumlah karyawan yang mengundurkan diri. Pada tahun 2018, terjadi aktivitas perekrutan dan pengunduran diri yang paling signifikan, yang dapat dilihat dari arah negatif garis Waterfall Chart. Hal ini mengindikasikan situasi yang menunjukkan perusahaan dalam kondisi kurang menguntungkan, karena jumlah karyawan yang mengundurkan diri lebih banyak daripada jumlah karyawan yang bergabung atau bertahan.

Hasil ini mencerminkan pentingnya perbaikan manajemen sumber daya manusia perusahaan. Perusahaan perlu melakukan peningkatan untuk memastikan retensi karyawan yang lebih baik dan menghindari biaya tambahan yang terkait dengan proses rekrutmen yang terus-menerus.

## Resign Reason Analysis for Employee Attrition Management Strategy

### Persentase karyawan aktif berdasarkan divisi pekerjaan
![2  Persentase karyawan aktif berdasarkan divisi pekerjaan](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/d4165569-71d3-4eaf-ae57-bc379550040e)

Grafik yang disajikan memperlihatkan distribusi persentase karyawan yang masih berada dalam berbagai divisi pekerjaan perusahaan. Dari data yang tersaji, menariknya, tujuh divisi memiliki tingkat retensi karyawan yang tinggi tanpa adanya kasus pengunduran diri. Namun, fokus khusus jatuh pada Divisi Data Analyst yang mencatat tingkat pengunduran diri sebesar 50%. Kondisi ini menegaskan urgensi untuk melakukan analisis mendalam terkait penyebab di balik tingginya tingkat perpindahan karyawan dari divisi ini.

### Alasan Pengunduran Diri Karyawan Berdasarkan JenjangKarir
![3  Alasan Pengunduran Diri Karyawan Berdasarkan JenjangKarir](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/7ce4cc2b-975d-4c7a-9c12-5b119fe63f3a)

Hasil pengamatan dan analisis grafik mengungkapkan beberapa pola yang signifikan dalam tingkat resignasi karyawan pada tiga tingkatan berbeda: Fresh Graduate, Middle Level, dan Senior. Pada tingkat Fresh Graduate, mayoritas karyawan mengundurkan diri disebabkan oleh ketidakmampuan melakukan pekerjaan dari jarak jauh (remote). Pada tingkat Middle Level, alasan utama resign adalah jam kerja yang terlalu padat. Sedangkan pada tingkat Senior, faktor utama adalah ketidakbahagiaan dalam pekerjaan.

Untuk mengatasi tantangan ini, saya merekomendasikan langkah-langkah strategis sebagai berikut:

1. Pada level Fresh Graduate disarankan untuk memberikan peluang kepada karyawan tingkat Fresh Graduate untuk mengadopsi model kerja jarak jauh (remote work) atau menerapkan pola kerja hybrid. Sebagai contoh, pola kerja hybrid ini dapat mencakup tiga hari kerja dari kantor dan dua hari kerja dari lingkungan rumah. Keputusan ini mendorong peningkatan fleksibilitas dalam lingkungan kerja, memungkinkan para Fresh Graduate untuk mengejar karir mereka sambil menjaga keseimbangan antara kehidupan kerja dan kehidupan pribadi. Dengan pendekatan ini, perusahaan memberikan peluang bagi karyawan muda ini untuk berkembang dan berkontribusi secara efisien sambil tetap memperhatikan kesejahteraan mereka.

2. Pada level Middle dalam kasus di mana alasan utama pengunduran diri berkaitan dengan beban kerja yang berlebihan, perusahaan memiliki kesempatan untuk mengambil tindakan proaktif. Salah satu langkah yang dapat dipertimbangkan adalah peningkatan jumlah karyawan di tim atau departemen terkait. Dengan demikian, perusahaan dapat mencapai distribusi beban kerja yang lebih merata, mengurangi tekanan yang ditanggung oleh individu, dan secara signifikan meningkatkan tingkat produktivitas. Langkah-langkah ini mencerminkan komitmen perusahaan terhadap kesejahteraan karyawan dan upaya untuk menciptakan lingkungan kerja yang seimbang dan produktif.

3. Pada level senior, perusahaan harus memberikan perhatian yang lebih serius terhadap fasilitas dan program kesejahteraan karyawan. Ini mencakup implementasi program kesehatan, kegiatan kebugaran, inisiatif pengembangan pribadi, serta kesadaran terhadap keseimbangan antara pekerjaan dan kehidupan pribadi. Langkah-langkah ini akan menciptakan lingkungan kerja yang seimbang dan nyaman, yang pada gilirannya dapat secara signifikan meningkatkan tingkat kepuasan dan retensi karyawan.

## Build and Modeling
### Data Preprocessing
- Handling Duplicated & Missing Value
  - Dalam analisis lebih lanjut, saya menemukan bahwa kolom 'TahunResign' mengandung 198 nilai yang hilang (missing value). Kehadiran missing value dalam kolom ini mengindikasikan bahwa karyawan tersebut belum mengajukan pengunduran diri. Untuk menangani situasi ini, saya memutuskan untuk mengisi missing value dalam kolom tersebut dengan nilai 0. Selain itu, saya menyimpulkan bahwa tidak ditemukan duplikasi nilai dalam dataframe.
- Handling Outliers
  - Sebelumnya, dalam tahap Analisis Data Eksplorasi (EDA), telah diidentifikasi adanya outlier pada beberapa kolom numerik. Untuk mengatasi permasalahan ini, saya menerapkan metode Z-score. Hasil dari penanganan outlier ini terlihat jelas dalam ilustrasi berikut, di mana jumlah baris dalam Dataframe mengalami penurunan sebanyak 14 baris.
- Feature Engineering
  - Saya membuat fitur baru yaitu ‘Resign’ dari kolom ‘TahunResign’. Dan ‘lama_bekerja’ dari kolom ‘TahunResignt’ - ‘TahunHiring.
- Feature Encoding
  - Demi memastikan keseragaman tipe data dan mempermudah proses pemodelan di masa mendatang, saya telah melaksanakan proses encoding fitur menggunakan metode label encoding. Gambar yang terlampir adalah ilustrasi sebagian dari kolom-kolom yang telah saya lakukan encoding.
- Feature Transformation
  - Dalam upaya untuk menormalkan skala semua fitur, telah diterapkan proses standarisasi dalam transformasi fitur. Sebagai hasilnya, terdapat cuplikan dataframe yang mencerminkan perubahan setelah proses transformasi, yang dapat dilihat pada gambar yang disajikan di sebelah kanan.

### Split Data
![4  Split Data](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/b89cb56d-9af4-4e2a-abf7-5e2738da58db)


Saya telah menetapkan kolom 'Resign' sebagai variabel target, sementara kolom lainnya saya gunakan sebagai atribut. 

Setelah menguraikan data, saya menjalankan proses resampling pada dataset pelatihan dengan menerapkan metode SMOTE. Hal ini dilakukan untuk mengatasi potensi bias dalam hasil output..

### Evaluation Model 
![5  Evaluation Model ](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/518c22c5-00f0-4673-82e1-730f974316be)

Setelah melakukan hyperparameter tuning, pilihan saya jatuh pada model DecisionTree sebagai model terbaik. Alasan saya memilih model DecisionTree adalah seimbangnya nilai Precision dan Recall yang dihasilkan oleh model tersebut. Dalam konteks ini, seimbangnya nilai Precision dan Recall menunjukkan bahwa model DecisionTree memiliki kemampuan yang baik dalam mengidentifikasi karyawan yang tetap (kelas 0) dan karyawan yang keluar (kelas 1) dengan tingkat kesalahan yang cukup rendah. Keputusan ini didasarkan pada pertimbangan bahwa seimbangnya Precision dan Recall dapat lebih meminimalkan risiko kesalahan yang dapat berdampak pada keputusan bisnis

## Presenting Machine Learning Products to the Business Users
### Confusion Matrix
![6  Confusion Matrix](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/8971d766-ff34-4d53-bac3-d85349d57b97)

Setelah menggunakan machine learning untuk memprediksi status karyawan (tetap atau keluar), diperoleh hasil berikut:
1. Precision untuk kelas 0 (0.95): Precision untuk kelas 0 sebesar 0.95 menunjukkan bahwa dari semua prediksi yang model buat sebagai kelas 0 (karyawan yang tetap), sekitar 95% dari prediksi tersebut adalah benar, atau dengan kata lain, sebagian besar karyawan yang model prediksi sebagai karyawan yang tetap benar-benar adalah karyawan yang tetap.
2. Precision untuk kelas 1 (0.88): Precision untuk kelas 1 sebesar 0.88 mengindikasikan bahwa dari semua prediksi yang model buat sebagai kelas 1 (karyawan yang keluar), sekitar 88% dari prediksi tersebut adalah benar, atau dengan kata lain, sebagian besar karyawan yang model prediksi sebagai karyawan yang keluar benar-benar adalah karyawan yang keluar.
3. Recall untuk kelas 0 (0.95): Recall mengukur sejauh mana model mampu mengidentifikasi dengan benar semua karyawan yang tetap. Dalam konteks ini, nilai recall yang tinggi (0.95) menunjukkan bahwa model hampir sempurna dalam mengenali karyawan tetap
4. Recall untuk kelas 1 (0.88): Recall untuk kelas 1 mengukur kemampuan model dalam mengidentifikasi karyawan yang keluar dengan benar. Dalam kasus ini, nilai recall yang tinggi (0.88) menunjukkan bahwa model juga cukup baik dalam mengenali karyawan yang keluar

Kesimpulannya adalah model yang sudah dilatih memiliki performa yang baik dalam mengidentifikasi karyawan tetap dan karyawan yang keluar dari dataset yang digunakan.

### Feature Importance
![7  Feature Importance](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/87d59ecc-c981-4bfb-80a3-7e94214a7c87)

"AlasanResign" merupakan feature importance yang memiliki kolerasi paling tinggi dengan Target, hal ini  menandakan bahwa laporan alasan yang diberikan oleh karyawan saat mereka mengundurkan diri memiliki dampak yang sangat berarti terhadap keputusan tersebut. Hal ini memberikan wawasan penting bagi perusahaan untuk memahami faktor-faktor yang berperan dalam pengambilan keputusan karyawan untuk meninggalkan pekerjaan. Analisis ini membantu perusahaan untuk lebih mendalam memahami tren dan faktor-faktor yang memengaruhi tingkat turnover serta mengidentifikasi upaya perbaikan yang diperlukan untuk memitigasi masalah tersebut.

![8  Distribusi Alasan Resign](https://github.com/GedeWiraWasistha/Improving-Employee-Retention-by-Predicting-Employee-Attrition-Using-Machine-Learning/assets/149849772/e7a40898-cb06-4319-8fda-e48eda195de9)

Dalam konteks ini, saya mengidentifikasi bahwa data yang memiliki nilai pada kolom "masih_bekerja" dan kolom "TanggalResign" kosong adalah data yang mewakili karyawan yang belum mengundurkan diri. Data ini menunjukkan bahwa karyawan-karyawan tersebut masih aktif bekerja dalam organisasi. Pemahaman ini didasarkan pada asumsi bahwa jika kolom "TanggalResign" kosong, maka tidak ada tanggal resign yang tercatat, yang menandakan bahwa karyawan tersebut masih bekerja.

Plot dengan nilai yang signifikan pada beberapa faktor yang menjadi alasan resign pegawai, seperti jam kerja, perubahan karier, ketidakjelasan jalur karier, dan keterbatasan dalam bekerja dari jarak jauh, mencerminkan dampak yang signifikan pada kepuasan dan retensi pegawai. Dalam kerangka yang lebih luas, plot dengan nilai tertinggi dapat dibagi menjadi dua sub-komponen, yaitu pengembangan karier dan fleksibilitas waktu serta tempat kerja.

Sebagai langkah-langkah untuk meningkatkan retensi karyawan, saya merekomendasikan perusahaan untuk:
1. Fleksibilitas Jam Kerja: Berikan opsi kerja yang lebih fleksibel, seperti bekerja dari rumah atau menerapkan kebijakan kerja fleksibel. Ini akan membantu menciptakan keseimbangan antara pekerjaan dan kehidupan pribadi yang lebih baik, serta meningkatkan kepuasan karyawan.
2. Pengembangan Karier: Sediakan jalur karier yang terdefinisi dengan jelas dan transparan sehingga karyawan memiliki visi yang jelas tentang bagaimana mereka dapat berkembang di perusahaan. Pastikan ada sistem promosi yang didasarkan pada kinerja dan adil, sehingga karyawan merasa diakui dan memiliki peluang untuk memajukan karier mereka.


