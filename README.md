# REFLECTION 6

#### 1. Commit 1 reflection notes
Method handle_connection bertugas untuk membaca dan mencetak HTTP request yang masuk melalaui koneksi TCP. Pertama, method ini menerima parameter stream bertipe Tcp Stream, kemudian memberikan referensi stream dalam BufReader yang memungkinkan pembacaan data secara lebih efisien. Lalu, data dibaca baris per baris hingga menemukan baris kosong yang menandakan akhir header, lalu dikumpulkan dalam sebuah vektor. Dan akhirnya vektor tersebut diprint di layar.

#### 2. Commit 2 reflection notes
Method handle_connection yang baru membaca isi dari file hello.html menjadi string yang disimpan dalam variabel `contents`. Kemudian method akan me-write http response dari stream dengan status 200 (OK) dan mengembalikan string html yang sudah disimpan variabel `contents`.

Screenshot:
![Commit 2 screen capture](/assets/images/commit2.png)

#### 3. Commit 3 reflection notes
Pada method handle_connection sekarang, kini method mampu membaca path dari http request. Jika path yang direquest sesuai, maka akan menampilkan http response dengan status 200 (OK) berupa halaman hello.html, sedangkan path lainnya akan menampilkan http response dengan status 404 (Not Found) berupa halaman error (404.html). Kode ini perlu direfactor karena terdapat duplikasi kode pada blok if-else, dimana proses penulisan http response dilakukan dua kali yang membuat kode kurang efisien.

Screenshot: 
![Commit 3 screen capture](/assets/images/commit3.png)

#### 4. Commit 4 reflection notes
Sekarang, web server dapat membaca path /sleep. Ketika http requestnya menerima path /sleep, web server akan menunggu selama 10 detik menggunakan threap::sleep kemudian akan menampilkan halaman hello.html. Ketika saya menggunakan dua browser untuk membuka http://127.0.0.1:7878/sleep, yang terjadi adalah browser yang kedua menunggu halaman 1 untuk selesai proses sleep selama 10 detik sehingga total menjadi menunggu 20 detik, seandainya ada 100 user yang ingin mengakses http://127.0.0.1:7878/sleep secara bersamaan dan kemudian ada user ke-101 yang ingin mengakses http://127.0.0.1:7878/, hal ini berarti user ke-100 harus menunggu 1000 detik sampai halamannya muncul. Hal ini dikarenakan web server kita menggunakan single threaded server, artinya server memproses setiap request satu per satu. Jika request memerlukan waktu lama, request berikutnya harus menunggu sampai request pertama selesai. Hal ini dapat menjadi masalah ketika banyak pengguna yang mengakses server secara bersamaan.