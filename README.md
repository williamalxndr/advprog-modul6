# REFLECTION 6

#### 1. Commit 1 reflection notes
Method handle_connection bertugas untuk membaca dan mencetak HTTP request yang masuk melalaui koneksi TCP. Pertama, method ini menerima parameter stream bertipe Tcp Stream, kemudian memberikan referensi stream dalam BufReader yang memungkinkan pembacaan data secara lebih efisien. Lalu, data dibaca baris per baris hingga menemukan baris kosong yang menandakan akhir header, lalu dikumpulkan dalam sebuah vektor. Dan akhirnya vektor tersebut diprint di layar.