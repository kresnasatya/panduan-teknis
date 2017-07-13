Saya menggunakan database yang ukurannya lebih dari 2 MB dan CI sebagai frameworknya. Namun, ketika menjalankan di localhost, muncul error di bawah ini: <br>

`Fatal error: Allowed memory size of 134217728 bytes exhausted (tried to allocate 47 bytes) in C:\xampp\htdocs\e-registrasi\system\database\drivers\mysqli\mysqli_result.php on line 183`

Saya melakukan googling dan menemukan solusi di stackoverflow [CodeIgniter Allowed memory exhausted](http://stackoverflow.com/questions/14701398/codeigniter-allowed-memory-exhausted).

Namun hal tersebut tidak membuat saya puas. Saya mencoba meningkatkan `memory_limit` di file **php.ini**, namun gagal. Berhari-hari akhirnya saya menemukan penyebabnya. Hal ini disebabkan karena saya mencoba menampilkan lebih dari 1000 rows tanpa system paging.

Dengan menggunakan system paging atau pagination, maka kita bisa menampilkan data 1000 rows tersebut dengan dibagi per page. Misalnya:

``1 page = 25 rows.
  40 page = 1000 rows``

Saya telah membuat contohnya di github. Berikut [linknya](https://github.com/satyakresna/e-registrasi)
