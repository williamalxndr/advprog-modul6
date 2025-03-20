# REFLECTION 6

#### 1. Commit 1 reflection notes
Method handle_connection bertugas untuk membaca dan mencetak HTTP request yang masuk melalaui koneksi TCP. Pertama, method ini menerima parameter stream bertipe Tcp Stream, kemudian memberikan referensi stream dalam BufReader yang memungkinkan pembacaan data secara lebih efisien. Lalu, data dibaca baris per baris hingga menemukan baris kosong yang menandakan akhir header, lalu dikumpulkan dalam sebuah vektor. Dan akhirnya vektor tersebut diprint di layar.

#### 2. Commit 2 reflection notes
Method handle_connection yang baru membaca isi dari file hello.html menjadi string yang disimpan dalam variabel `contents`. Kemudian method akan me-write http response dari stream dengan status 200 (OK) dan mengembalikan string html yang sudah disimpan variabel `contents`.

Screenshot:
![Commit 2 screen capture](/assets/images/commit2.png)