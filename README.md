
# Tahapan Penyelesaian Projek

1. Deteksi Warna pada Citra

`import cv2`: mengimpor modul OpenCV untuk pengolahan citra.

`import matplotlib.pyplot as plt`: mengimpor modul pyplot dari Matplotlib untuk menampilkan gambar.

`import numpy as np`: mengimpor modul NumPy yang digunakan untuk operasi numerik.

`img = cv2.imread("name.jpg")`: membaca gambar dari file "name.jpg" menggunakan OpenCV dan menyimpannya dalam variabel `img`.

`img.shape`: mengembalikan dimensi gambar sebagai tuple (baris, kolom, channel). Nilai channel adalah 3 untuk gambar berwarna (RGB).

`[baris, kolom] = img.shape[:2]`: mengekstrak dimensi baris dan kolom dari tuple dimensi gambar dan menyimpannya dalam variabel `baris` dan `kolom`.

`img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)`: Ini mengonversi gambar dari mode warna BGR (yang digunakan oleh OpenCV) ke mode warna RGB (yang digunakan oleh Matplotlib untuk menampilkan gambar dengan benar).

`plt.imshow(img)`: Ini menampilkan gambar menggunakan Matplotlib. Fungsi `imshow()` digunakan untuk menampilkan gambar dalam format RGB.

OPERASI PIXEL GABUNGAN (Meningkatkan Kecerahan dan Meregangkan Kontras)

`alpa = 1.25` dan `beta = 4`: Variabel `alpa` dan `beta` adalah parameter untuk mengontrol kontras dan kecerahan gambar. `alpa` mengontrol kontras sedangkan `beta` mengontrol kecerahan.

`citra_gabungan = np.zeros((baris, kolom, 3))`: Membuat array numpy dengan ukuran yang sama dengan gambar asli, tetapi diisi dengan nol. Ini akan digunakan untuk menyimpan gambar yang telah dimodifikasi.

Loop `for` digunakan untuk mengakses setiap piksel dalam gambar:
   - `gcx = (img[x,y] * alpa) + beta`: Operasi kontras dan kecerahan diterapkan pada setiap saluran warna (RGB) dari setiap piksel. Nilai piksel dikalikan dengan `alpa` untuk mengatur kontras dan ditambah dengan `beta` untuk mengatur kecerahan.
   - `citra_gabungan[x,y] = gcx`: Hasil dari operasi kontras dan kecerahan disimpan dalam array `citra_gabungan`.

`citra_gabungan = citra_gabungan.astype(np.uint8)`: Array `citra_gabungan` diubah menjadi tipe data unsigned integer 8-bit, karena nilai piksel dalam gambar harus berada dalam kisaran 0-255.

`fig, axs = plt.subplots(2,2, figsize = (15,5))`: Membuat bingkai gambar dengan empat subplot, di mana subplot pertama menampilkan gambar asli dan subplot kedua menampilkan histogramnya, begitu pula dengan subplot ketiga dan keempat untuk gambar yang telah dimodifikasi.

`axs[0,0].imshow(img)`: Menampilkan gambar asli dalam subplot pertama.

`axs[0,1].hist(img.ravel(),256,[0,256])`: Menampilkan histogram gambar asli dalam subplot kedua.

`axs[1,0].imshow(citra_gabungan)`: Menampilkan gambar yang telah dimodifikasi dalam subplot ketiga.

`axs[1,1].hist(citra_gabungan.ravel(),256,[0,256])`: Menampilkan histogram gambar yang telah dimodifikasi dalam subplot keempat.

`plt.show()`: Menampilkan bingkai gambar dengan keempat subplot-nya.

DETEKSI WARNA PADA CITRA 

`plt.subplot(2, 2, 1)`: Membuat subplot pertama dalam bingkai gambar dengan konfigurasi 2 baris dan 2 kolom, dan mengatur subplot saat ini menjadi yang pertama.

`plt.imshow(citra_gabungan)`: Menampilkan gambar yang telah dimodifikasi dalam subplot pertama.

`plt.title('Citra Kontras')`: Memberikan judul "Citra Kontras" untuk subplot pertama.

`plt.subplots_adjust(wspace = 0.4, hspace=0.4)`: Mengatur jarak antara subplot secara horizontal dan vertikal.

`plt.show()`: Menampilkan bingkai gambar dengan semua subplot-nya.

HISTOGRAM UNTUK SETIAP GAMBAR 

`fig, axs = plt.subplots(3, 2, figsize=(15,15))`: Membuat bingkai gambar dengan ukuran yang ditentukan dan konfigurasi 3 baris dan 2 kolom untuk subplot.

Mendefinisikan variabel `merah`, `hijau`, dan `biru` yang mewakili saluran warna merah, hijau, dan biru dari gambar yang telah dimodifikasi.

Menghitung histogram untuk setiap saluran warna menggunakan `cv2.calcHist()`.

Menampilkan gambar dan histogram saluran warna merah dalam subplot pertama (indeks [0,0] dan [0,1]).

Menampilkan gambar dan histogram saluran warna hijau dalam subplot kedua (indeks [1,0] dan [1,1]).

Menampilkan gambar dan histogram saluran warna biru dalam subplot ketiga (indeks [2,0] dan [2,1]).

`plt.tight_layout()`: Mengatur layout subplot agar rapih dan tidak tumpang tindih.

`plt.show()`: Menampilkan bingkai gambar dengan semua subplot-nya.

Hasil Analisis pada Citra

Analisis Citra Kontras:

citra tersebut menunjukkan grafik kontras untuk tiga kata: "REVA", "NURNADIA", dan "SYAPA". Grafik ini menunjukkan perbedaan intensitas warna (merah, hijau, dan biru) untuk ketiga kata tersebut pada nilai piksel yang berbeda.

Analisis Kontras Warna Merah

Nilai Kontras: 1000
Deskripsi: Kata "REVA" memiliki kontras warna merah yang lebih tinggi dibandingkan dengan kata "NURNADIA" dan "SYAPA". Hal ini menunjukkan bahwa kata "REVA" memiliki perbedaan intensitas warna merah yang lebih besar antara piksel terang dan gelap.

Analisis Kontras Warna Hijau

Nilai Kontras: 3000
Deskripsi: Kata "NURNADIA" memiliki kontras warna hijau yang paling tinggi dibandingkan dengan kata "REVA" dan "SYAPA". Hal ini menunjukkan bahwa kata "NURNADIA" memiliki perbedaan intensitas warna hijau yang paling besar antara piksel terang dan gelap.

Analisis Kontras Warna Biru

Nilai Kontras: 3000
Deskripsi: Sama seperti kontras warna hijau, kata "NURNADIA" juga memiliki kontras warna biru yang paling tinggi dibandingkan dengan kata "REVA" dan "SYAPA". Hal ini menunjukkan bahwa kata "NURNADIA" memiliki perbedaan intensitas warna biru yang paling besar antara piksel terang dan gelap.

Analisis histogram

Red histogram

Histogram merah ini memiliki satu puncak, yang menunjukkan bahwa gambar tersebut kemungkinan besar didominasi oleh satu warna merah atau tingkat intensitas merah tertentu. Puncak tersebut berada di sekitar nilai intensitas merah 150, yang berarti nilai ini adalah yang paling sering muncul untuk piksel berwarna merah dalam gambar. Histogram ini juga memiliki ekor panjang di sebelah kanan, yang menunjukkan adanya sedikit piksel dengan nilai intensitas merah yang sangat tinggi.

Green histogram

Histogram ini memiliki satu puncak, yang menunjukkan gambar tersebut kemungkinan besar didominasi oleh satu warna atau tingkat intensitas tertentu. Puncak tersebut berada di sekitar nilai intensitas piksel 250, yang berarti nilai ini adalah yang paling sering muncul dalam gambar. Histogram ini juga memiliki ekor panjang di sebelah kanan, yang menunjukkan adanya sedikit piksel dengan nilai intensitas yang sangat tinggi.

Blue histogram

Histogram biru ini memiliki satu puncak, yang menunjukkan bahwa gambar tersebut kemungkinan besar didominasi oleh satu warna biru atau tingkat intensitas biru tertentu. Puncak tersebut berada di sekitar nilai intensitas biru 200, yang berarti nilai ini adalah yang paling sering muncul dalam gambar. Histogram ini juga memiliki ekor panjang di sebelah kanan, yang menunjukkan adanya sedikit piksel dengan nilai intensitas biru yang sangat tinggi.

2. Nilai Ambang Batas pada Citra

`hsv_image = cv2.cvtColor(citra_gabungan, cv2.COLOR_RGB2HSV)`: Mengonversi gambar `citra_gabungan` dari ruang warna RGB menjadi HSV.

`lower_blue` dan `upper_blue`: Menentukan batas bawah dan atas untuk warna biru dalam ruang warna HSV.

`lower_green` dan `upper_green`: Menentukan batas bawah dan atas untuk warna hijau dalam ruang warna HSV.

`lower_red1`, `upper_red1`, `lower_red2`, dan `upper_red2`: Menentukan dua rentang untuk warna merah dalam ruang warna HSV, karena rentang warna merah melintasi batas 0 dan 180.

Membuat mask untuk warna biru, hijau, dan merah menggunakan `cv2.inRange()`.

`gray = cv2.cvtColor(citra_gabungan, cv2.COLOR_RGB2GRAY)`: Mengonversi gambar `citra_gabungan` menjadi citra skala abu-abu.

Membuat subplot untuk menampilkan hasil deteksi warna dalam gambar:

   - Subplot pertama menampilkan citra skala abu-abu tanpa thresholding.
   
   - Subplot kedua menampilkan hasil segmentasi untuk warna biru.
   
   - Subplot ketiga menampilkan hasil segmentasi untuk kombinasi warna merah dan biru.
   
   - Subplot keempat menampilkan hasil segmentasi untuk warna hijau.

`plt.tight_layout()`: Mengatur layout subplot agar rapih dan tidak tumpang tindih.

`plt.show()`: Menampilkan bingkai gambar dengan semua subplot-nya.

Nilai Ambang Batas yang Didapat

Nilai ambang batas yang dapat dipilih adalah 150.

Alasan Pemilihan Nilai Ambang Batas

Nilai ambang batas 150 dipilih karena alasan berikut:

Pemisahan Puncak: Nilai ini berada di antara dua puncak histogram, secara efektif memisahkan piksel yang lebih gelap (hitam) dari piksel yang lebih terang (putih).

Pembedaan Warna: Nilai ambang batas ini memastikan bahwa kategori hitam dan putih dapat dibedakan dengan jelas pada citra hasil segmentasi.

Karakteristik Citra: Mengingat karakteristik gambar, ambang batas 150 secara tepat membedakan antara teks dan latar belakang.


3. Teori yang mendukung mengenai Projek

Deteksi warna pada citra

Deteksi warna pada citra adalah proses pengidentifikasi dan segmentasi area tertentu dalam gambar berdasarkan warna atau kombinasi warna tertentu. Ini adalah salah satu teknik pemrosesan citra yang penting dan banyak digunakan dalam berbagai aplikasi, termasuk penglihatan komputer, kendali otomatis, pemrosesan gambar medis, dan lainnya. Berikut adalah beberapa konsep teoritis yang terkait dengan deteksi warna pada citra:

**Ruang Warna**: Deteksi warna sering kali dilakukan dalam ruang warna tertentu seperti RGB (Red, Green, Blue), HSV (Hue, Saturation, Value), atau LAB (Luminance, A, B). Setiap ruang warna memiliki kelebihan dan kekurangan tertentu, dan pemilihan ruang warna yang tepat tergantung pada aplikasi dan kebutuhan spesifik.

**Histogram Warna**: Histogram warna adalah representasi distribusi intensitas piksel warna dalam gambar. Dengan menganalisis histogram warna, kita dapat mengidentifikasi distribusi warna tertentu dalam citra, yang berguna untuk mendeteksi warna tertentu atau rentang warna dalam gambar.

**Segmentasi Warna**: Segmentasi warna adalah proses membagi gambar menjadi beberapa bagian atau region berdasarkan warna atau kombinasi warna tertentu. Metode segmentasi yang umum digunakan termasuk thresholding (pembatasan), clustering (pengelompokan), dan pendekatan berbasis model.

**Thresholding**: Thresholding adalah teknik segmentasi yang paling sederhana di mana nilai intensitas piksel dijadikan acuan untuk memisahkan area tertentu dalam gambar. Dalam deteksi warna, thresholding dapat digunakan untuk memisahkan piksel berdasarkan batas intensitas warna tertentu dalam ruang warna yang dipilih.

**Model Warna**: Pendekatan berbasis model melibatkan penggunaan model statistik atau probabilistik untuk menggambarkan distribusi warna dalam gambar. Model seperti Gaussian Mixture Models (GMM) atau Color Histogram Models sering digunakan untuk mengidentifikasi warna tertentu dalam citra.

**Filtering dan Pencocokan**: Metode deteksi warna juga dapat melibatkan penggunaan filter spasial atau filter spasial- frekuensi untuk menekankan atau menekan warna tertentu dalam gambar. Selain itu, teknik pencocokan pola atau pencocokan template dapat digunakan untuk mencari kecocokan pola warna tertentu dalam citra.

**Ekstraksi Fitur**: Setelah deteksi warna dilakukan, fitur-fitur kunci seperti luas area berwarna, koordinat spasial, atau distribusi spasial dapat diekstraksi dari area yang tersegmentasi untuk analisis lebih lanjut atau pengambilan keputusan.

Deteksi warna pada citra adalah bagian penting dari berbagai aplikasi pemrosesan citra dan visi komputer. Dengan memahami konsep teoritis di atas dan menerapkannya dengan benar, kita dapat mengidentifikasi dan memanipulasi objek berdasarkan warna dalam gambar dengan tepat.

Nilai Ambang Batas Citra

Nilai ambang batas (threshold) dalam pemrosesan citra adalah nilai yang digunakan untuk memisahkan piksel menjadi dua kelas berdasarkan intensitasnya. Proses ini dikenal sebagai thresholding, dan digunakan dalam berbagai aplikasi pemrosesan citra untuk segmentasi, deteksi objek, dan pengenalan pola. Berikut adalah beberapa teori terkait dengan nilai ambang batas dalam pemrosesan citra:

**Thresholding**: Thresholding adalah teknik dasar dalam pemrosesan citra yang digunakan untuk memisahkan piksel menjadi dua kelas, yaitu hitam atau putih, berdasarkan intensitasnya melebihi atau kurang dari nilai ambang yang ditentukan. Hal ini dapat digunakan untuk meningkatkan kontras, menghilangkan noise, dan mengekstraksi objek dari latar belakang dalam gambar.

**Metode Thresholding**: Ada berbagai metode thresholding yang tersedia, termasuk thresholding global, thresholding adaptif, dan thresholding berdasarkan histogram. Thresholding global menggunakan nilai ambang yang sama untuk seluruh citra, sementara thresholding adaptif menggunakan nilai ambang yang bervariasi berdasarkan wilayah citra. Thresholding berdasarkan histogram memilih nilai ambang berdasarkan distribusi histogram intensitas citra.

**Otsu's Method**: Otsu's Method adalah salah satu metode thresholding yang paling umum digunakan. Ini adalah pendekatan yang optimal secara statistik yang mencoba untuk memilih nilai ambang yang meminimalkan variasi intra-kelas dan memaksimalkan variasi antara kelas dalam histogram intensitas citra.

**Evaluasi Thresholding**: Evaluasi kualitas thresholding dapat dilakukan menggunakan metrik seperti akurasi, sensitivitas, spesifisitas, dan F1-score. Metrik-metrik ini membantu untuk mengevaluasi seberapa baik nilai ambang yang dipilih dapat memisahkan objek dari latar belakang dengan benar.

**Penggunaan dalam Segmentasi**: Nilai ambang batas sering digunakan dalam proses segmentasi citra untuk memisahkan objek dari latar belakang atau untuk mengidentifikasi area tertentu dalam citra berdasarkan intensitasnya.

**Pemilihan Nilai Ambang yang Tepat**: Pemilihan nilai ambang batas yang tepat sangat penting dalam keberhasilan proses thresholding. Ini dapat dilakukan secara manual berdasarkan pengetahuan tentang gambar atau menggunakan pendekatan otomatis seperti Otsu's Method.

**Preprocessing**: Terkadang, preprocessing seperti penerapan filter atau teknik pengurangan noise dapat meningkatkan efektivitas thresholding dengan menghasilkan citra dengan kontras yang lebih baik atau dengan menghilangkan derau yang mengganggu.

Nilai ambang batas memainkan peran penting dalam pemrosesan citra, dan pemilihan yang tepat dapat memiliki dampak signifikan terhadap hasil akhir dari analisis citra.










