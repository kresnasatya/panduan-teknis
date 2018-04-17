# Import File SQL besar
Di PHPMyadmin, kita tidak bisa mengimport .sql file lebih dari 2MB (2048kiB). Berikut adalah solusi jika kita ingin mengimport data lebih dari itu.

  1. Pertama matikan module ***Apache*** dan ***MySQL*** di XAMPP. <br/>
  2. Di module ***Apache*** klik menu ***config*** dan cari file ***php.ini***: <br/>
      a. Cari (CTRL + F) `post_max_size` dan `upload_max_filesize`. <br/> Jika kita ingin mengupload data sekitar 128MB maka ubah nilainya menjadi: <br/>
      `post_max_size=128M
       upload_max_filesize=128M` <br/>
  3. Di module ***MySQL*** klik menu ***config*** dan cari file ***my.ini***: <br/>
      a. Cari (CTRL + F) `max_allowed_packet`. Jika ukuran SQL kita sekitar 128MB atau lebih maka ubah nilainya menjadi: <br/>
      `max_allowed_packet=1024M` dengan tujuan agar mempercepat proses import data SQL. <br/>
  4. Hidupkan kembali ***Apache*** dan ***MySQL***. Kita sudah bisa mengupload SQL lebih dari 2MB.

***Ingat*** Ini hanya berlaku pada server local saja. Kalau server sungguhan (cPanel) saya belum tahu.

***UPDATE!!!*** Di server sungguhan (cPanel), PHPMyadmin dapat menerima import file SQL kita maksimal 50MB

Link terkait: [phpMyAdmin: Can't import huge database file, any suggestions?](http://stackoverflow.com/questions/5051253/phpmyadmin-cant-import-huge-database-file-any-suggestions)

# Import SQL file dengan command prompt.
Saya telah mencoba menggunakan command prompt (windows) untuk mengimport sql file yang berukurannya besar
(ukurannya lebih dari 500 MB sudah saya coba dan berhasil) tanpa hacking mysql.ini dan php.ini seperti yang saya jelaskan di atas. Berikut langkah-langkahnya:
  1. Aktifkan XAMPP dan hidupkan opsi untuk `mysql` saja.
  2. Buka cmd dan masukkan perintah `mysql -u root -p` dan tekan `enter`. Masukkan password, jika tidak ada
  maka kosongkan.
  3. Pilih database yang akan diimport datanya perintahnya `use nama_database_kamu;`.
  4. Kemudian ketik `source path_import_sql_kamu_berada`. Contoh `source C:\Users\xyz\Documents\BACKUP DB KANTOR\nama_database_yg_diimport`. Ingat jangan masukkan tanda `;` di akhir perintahnya karena akan error.
  5. Ketik enter dan tunggu sampai proses import ke dalam database selesai.
**NB** : Saya kira untuk sistem operasi `macOS` dan `distro linux` bisa menyesuaikan.
