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
