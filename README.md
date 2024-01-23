# Wildfire_Detection
Using YOLO Object Detection with SAHI Inference

## Background
  Kebakaran hutan dan lahan (karhutla) merupakan masalah lingkungan yang serius di Indonesia, terutama di daerah Sumatera. Karhutla memiliki dampak negatif yang sangat besar bagi lingkungan dan masyarakat, antara lain pencemaran udara, degradasi lahan, hilangnya keanekaragaman hayati, perubahan iklim, kerusakan infrastruktur, gangguan kesehatan, dan kehilangan mata pencaharian. Proyek deteksi kebakaran hutan dengan object detection merupakan salah satu upaya untuk mengatasi masalah karhutla di Indonesia. Teknologi object detection dapat digunakan untuk mendeteksi titik api dalam citra satelit atau video. Proyek ini penting untuk dibuat karena dapat membantu dalam mendeteksi kebakaran hutan secara dini, sehingga dapat mencegah meluasnya kebakaran hutan dan mengurangi dampak negatifnya bagi lingkungan dan masyarakat.

## Method
  Metode yang digunakan pada project ini untuk menyelesaikan permasalahan tentang kebakaran hutan, yaitu dengan menggunakan **Object Detection**. Mengutip dari halaman web *ultralytics*, "object detection adalah tugas yang melibatkan identifikasi lokasi dan kelas objek dalam aliran gambar atau video. Output dari pendeteksi objek adalah sekumpulan kotak pembatas yang mengapit objek dalam gambar, beserta label kelas dan skor keyakinan untuk setiap kotak". Sehingga object detection dapat menjadi salah satu solusi untuk mengamati object tertentu dalam hal ini adalah asap kebakaran yang merupakan tanda awal terjadinya kebakaran hutan.

  Object detection diatas, jika ditambahkan metode SAHI (Slicing Aided Hyper Inference) diharapkan akan menambah performa dari proses pendeteksian asap sehingga mendapatkan hasil yang lebih baik terutama pada object gambar asap yang memiliki resolusi tinggi. SAHI adalah library yang dirancang untuk mengoptimalkan algoritma object detection pada gambar berskala besar dan beresolusi tinggi. Fungsi inti SAHI terletak pada pemotongan gambar menjadi potongan-potongan yang dapat dikelola, menjalankan deteksi objek pada setiap potongan, dan kemudian menyatukan hasilnya kembali. SAHI kompatibel dengan berbagai model deteksi objek, termasuk seri YOLO, sehingga menawarkan fleksibilitas sambil memastikan penggunaan sumber daya komputasi yang dioptimalkan.

## Dataset
The dataset can be downloaded from `https://universe.roboflow.com/brad-dwyer/wildfire-smoke/dataset/1`. This dataset has already been annotate and i downloaded using YOLOv8 format. 

## Result
  Training yang menggunakan base model yolov8 versi nano menggunakan custom dataset menghasilkan deteksi yang cukup baik dengan nilai matriks maP50, F1-Score, Precision, dan Recall sebagai berikut:
|   maP50   | F1-Score  | Precision | Recall |
|-----------|-----------|-----------|--------|
|   85,68%  |  81,00%   |   73,1%   |  95%   |

  Dengan menggunakan object detection ditambahkan menggunakan yolov8 dengan metode inference SAHI, custom model memiliki performa lebih baik lagi. Dimana hasil dari deteksi menggunakan YOLO pada kasus [no Detection] menghasilkan [detection] jika menggunakan SAHI sebagai metode inference. Hasil ini dapat terlihat pada notebook. Sehingga dapat disimpulkan bahwa SAHI berfungsi sangat baik untuk kasus deteksi pada object yang berukuran sangat kecil dan berhasil dibuktikan untuk kasus deteksi asap kebakaran hutan lindung.
