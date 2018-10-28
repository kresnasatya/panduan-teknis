# Cara deploy web Laravel dengan Gitlab CI/CD
Bagi teman-teman yang memiliki VPS, mempunyai repository Github yang berisikan web Laravel serta kebingungan cara menyebarkan aplikasi Anda (deploy) secara terintegrasi dan otomatis maka Anda berada di tempat yang tepat. Pada bagian ini kita akan menggunakan Gitlab sebagai CI/CD deployment Laravel + Laravel Deployer.

# Catatan penting
Sebenarnya jika Anda sudah memiliki project di Gitlab maka Anda bisa langsung saja menggunakan Gitlab CI/CD nya. Namun, sebagai saya akan menggunakan Github sebagai contoh dan ada batasan yang perlu Anda ketahui. Saat ini kita bisa melakukan CI/CD via Gitlab di luar Gitlab (seperti Github atau Bitbucket) tetapi hanya berlaku sampai tanggal 22 Maret 2019. Jika lewat dari itu maka kita harus menggunakan layanan berbayar dari Gitlab.

![Langkah 1](images-guide/laravel-gitlab-deployment/langkah-1.jpg)

## Mulai
1. Koneksikan repository Github yang ingin menggunakan CI/CD Gitlab dengan login ke website Gitlab seperti gambar di bawah.

![Langkah 2](images-guide/laravel-gitlab-deployment/langkah-2.png)

![Langkah 3](images-guide/laravel-gitlab-deployment/langkah-3.png)

![Langkah 4](images-guide/laravel-gitlab-deployment/langkah-4.png)

![Langkah 5](images-guide/laravel-gitlab-deployment/langkah-5.png)

![Langkah 6](images-guide/laravel-gitlab-deployment/langkah-6.png)
