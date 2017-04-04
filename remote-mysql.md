# Remote MySQL
Cara agar database di server (internet) bisa di bawa ke komputer atau laptop kita tanpa harus buka Cpanel.

## Langkah-langkah
  - Buka Cpanel > Pilih opsi ``remote mysql`` di bagian **Databases**.
  - Saat berada di opsi tersebut, telah tersedia sebuah IP address atau host (default) yang akan kita pakai untuk
  melakukan remote MySQL. Namun, kita perlu membuat host lagi agar bisa diterima oleh server Cpanel.
  - Masukkan host IP address yang kita gunakan saat berinternet ke form `Add an Access Host`. Cara mengecek IP address buka web [whatismyip.com](http://whatismyip.com).
  - Saat masukkan host, gunakan tanda `%` sebagai wildcard. Contoh IP yang terbaca di **whatismyip** adalah `112.210.172.107`. Kemudian kita ubah menjadi `112.210.%.%`. Kemudian klik `Add host`
  - Tujuan menggunakan tanda `%` adalah supaya IP yang kita pakai untuk berinternet diterima oleh server Cpanel saat melakukan remote. Hal ini dikarenakan IP yang kita gunakan untuk berinternet berubah-ubah dalam waktu tertentu dan tergantung dari provider kita.
  - **Opsi pertama**: Buka SQLyog > klik new connection > pilih tab MySQL.
    - Masukkan **host atau IP address** yang di langkah kedua ke dalam kolom `MySQL Host Address`.
    - Masukkan **username** ke dalam kolom `username`.
    - Masukkan **password** ke dalam kolom `password`.
    - Biarkan port nya default
    - Klik **Test connection**. Jika berhasil maka klik **Connect**.
  - **Opsi kedua**: Buka XAMPP > Klik **config** pada  section **Apache** > pilih `config.inc.php`.
    - Pada baris terakhir sebelum tanda `?>` masukkan script berikut:
    ```
    /* Remote server */
    $i++;
    $cfg['Servers'][$i]['auth_type'] = 'config';
    $cfg['Servers'][$i]['user'] = 'yourusername';
    $cfg['Servers'][$i]['password'] = 'yourpass';
    $cfg['Servers'][$i]['host'] = 'your host or IP address di langkah kedua';
    $cfg['Servers'][$i]['connect_type'] = 'tcp';
    ```
    - Save file > hidupkan Apache > hidupkan MySQL > masuk ke `localhost/phpMyAdmin` > Cek combobox yang berada di pojok kiri atas > Pilih opsi server anda.
