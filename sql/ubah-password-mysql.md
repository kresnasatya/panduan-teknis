# Mengubah password MySQL di XAMPP
Langkah - langkah:
  1. Pastikan server `Apache` dan `MySQL` sudah dinyalakan.
  2. Klik tombol `Shell` yang berada di sebelah kanan XAMPP.
  3. Masukan perintah `mysqladmin --user=root password "newpassword"`.
    Contoh:  `mysqladmin --user=root password "0000"`
    Atau jika sebelumnya sudah pernah memasang password dan ingin mengubahnya
    dengan yang baru maka perintahnya seperti berikut: `mysqladmin --user=root --password=oldpassword password = "newpassword"`.
    Contoh: `mysqladmin --user=root --password=0000 password = "meow"`.
  4. Setelah mengubah password di `Shell`, kamu harus mengubah password di file `config.inc.php`.
    Kamu harus melakukannya untuk menghindari error saat koneksi ke database.
    Silahkan buka `C:\xampp\phpMyAdmin` dan cari file tersebut. Carilah baris kode seperti di bawah ini:

    ```
    /* Authentication type and info */
    $cfg['Servers'][$i]['auth_type'] = 'config';
    $cfg['Servers'][$i]['user'] = 'root';
    $cfg['Servers'][$i]['password'] = '';
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    $cfg['Servers'][$i]['AllowNoPassword'] = false;
    $cfg['Lang'] = '';
    ```

    Berikan isi dalam `$cfg['Servers'][$i]['password'] = '';` menjadi seperti ini:
    ```
    /* Authentication type and info */
    $cfg['Servers'][$i]['auth_type'] = 'config';
    $cfg['Servers'][$i]['user'] = 'root';
    $cfg['Servers'][$i]['password'] = '0000';
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    $cfg['Servers'][$i]['AllowNoPassword'] = false;
    $cfg['Lang'] = '';
    ```
  5. Matikan koneksi `Apache` dan `MySQL`. Hidupkan kembali dan akses `localhost/phpMyAdmin` di browser kamu. Yeay~


## Referensi
[How to configure root password for phpMyAdmin MySQL in XAMPP](https://www.roodex.com/blog/change-password-phpmyadmin-mysql-xampp/)
