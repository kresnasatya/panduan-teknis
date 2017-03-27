Penamaan function/method Controller ketika membuat CRUD:
Dulu, ketika saya membuat sebuah controller untuk melakukan proses CRUD pada CodeIgniter, saya menggunakan opsi A.
Tetapi, sekarang saya mulai beralih kepada opsi B. Karena prosesnya terpisah-pisah seperti
1 fungsi mempunyai 1 tugas.

A.
1. create -> untuk menampilkan form tambah data dan sekaligus memproses penyimpanan data.
2. update -> untuk menampilkan form ubah data dan sekalgus memproses pengubahan data.
3. delete -> untuk melakukan penghapusan data

B.
1. create -> untuk menampilkan form tambah data
2. store -> untuk melakukan proses penyimpanan data
3. edit -> untuk menampilkan form ubah data
4. update -> untuk melakukan proses pengubahan data
5. delete -> untuk melakukan penghapusan data

Saya mendapat ide dari opsi B ketika latihan membuat aplikasi sederhana menggunakan Laravel
(Buku Seminggu belajar Laravel). Di dalam buku tersebut, penulis menjelaskan bahwa penerapan opsi B
ini merupakan salah satu hal yang baik ketika ingin menerapkan Restful atau sesuatu yang berkaitan
dengan API (mohon maaf saya lupa di halaman berapa).

Link terkait: https://sekolahkoding.com/forum/ask-share-penamaan-function-controller-ketika-membuat-crud
