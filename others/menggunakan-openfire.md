# Openfire
Openfire is a powerful instant messaging (IM) and chat server that implements the XMPP protocol.

# Cara Install
Di windows cukup download aplikasi Openfire dan `run as administrator` untuk menjalankan proses instalasi.
Setelah selesai, klik kanan pada Openfire server dan `run as administrator`. Hal ini dikarenakan fitur UAC yang enabled, maka dari itulah harus `run as administrator`.

# Setup database
Karena kita akan pakai setup database external (MySQL) maka harus mengikuti tahap-tahap berikut:
  1. Pastikan kalau menggunakan MySQL 4.1.18 atau yang terbaru (5.x recommended).
  2. Buat database untuk Openfire tables. Misalnya: `CREATE DATABASE openfire`.
  3. Import schema database openfire yang berada di root aplikasi openfire `resource/database`.
      - Aktifkan MySQL Commandline > `USE openfire` > `source <copy path openfire_mysql yang berada di resource/database>`
  4. Jalankan XAMPP (run apache dan mysql) > Run openfire as administrator dan start openfire server.
