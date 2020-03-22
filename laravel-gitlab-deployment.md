# Cara deploy web Laravel dengan Gitlab CI/CD
Bagi teman-teman yang memiliki VPS, mempunyai repository Github yang berisikan web Laravel serta kebingungan cara menyebarkan aplikasi Anda (deploy) secara terintegrasi dan otomatis maka Anda berada di tempat yang tepat. Pada bagian ini kita akan menggunakan Gitlab sebagai CI/CD deployment Laravel + Laravel Deployer.

# Catatan penting
Sebenarnya jika Anda sudah memiliki project di Gitlab maka Anda bisa langsung saja menggunakan Gitlab CI/CD nya. Namun, sebagai saya akan menggunakan Github sebagai contoh dan ada batasan yang perlu Anda ketahui. Saat ini kita bisa melakukan CI/CD via Gitlab di luar Gitlab (seperti Github atau Bitbucket) tetapi hanya berlaku sampai tanggal 22 Maret 2019. Jika lewat dari itu maka kita harus menggunakan layanan berbayar dari Gitlab.

![Langkah 1](images-guide/laravel-gitlab-deployment/langkah-1.jpg)

## Mulai tahap 1
1. Koneksikan repository Github yang ingin menggunakan CI/CD Gitlab dengan login ke website Gitlab seperti gambar di bawah.

![Langkah 2](images-guide/laravel-gitlab-deployment/langkah-2.png)

![Langkah 3](images-guide/laravel-gitlab-deployment/langkah-3.png)

![Langkah 4](images-guide/laravel-gitlab-deployment/langkah-4.png)

![Langkah 5](images-guide/laravel-gitlab-deployment/langkah-5.png)

![Langkah 6](images-guide/laravel-gitlab-deployment/langkah-6.png)

2. Membuat user bernama deployer dan memberikan akses baca tulis dan eksekusi ke user deployer. Anda bisa menggunakan user selain deployer.
```bash
# Lakukan ini di terminal VPS Anda
# Membuat user deployer
sudo adduser deployer
# Memberikan akses baca tulis dan eksekusi ke user deployer untuk directori /var/www
sudo setfacl -R -m u:deployer:rwx /var/www
```
Jika Anda tidak bisa membuat user hal ini dikarenakan Anda belum menginstall ACL, silahkan install terlebih dahulu di server Ubuntu Anda dengan perintah berikut:
```bash
sudo apt install acl
```

3. Membuat SSH key sebagai user deployer. Pastikan Anda berpindah user ke user deployer. Kemudian buatlah SSH key sesuai [artikel yang disediakan oleh Github](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).

4. Setelah berhasil membuat SSH key, selanjutnya lakukan duplikat konten public key SSH ke authorized keys.
```bash
# As the deployer user on server
#
# Copy the content of public key to authorized_keys
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```

5. Berikutnya duplikat isi private key dan kita akan taruh di project Gitlab kita.
```bash
# Copy the private key text block
cat ~/.ssh/id_rsa
# Blok isi dari private key tadi, copy dan tempel di Gitlab project kita seperti gambar di bawah.
```
![Langkah 7](images-guide/laravel-gitlab-deployment/langkah-7.png)

![Langkah 8](images-guide/laravel-gitlab-deployment/langkah-8.png)

6. Melakukan duplikat isi public key dan kita taruh di project Gitlab kita.
```bash
# As the deployer user on the server
#
# Copy the public key
cat ~/.ssh/id_rsa.pub
# Blok isi dari public key tadi, copy dan tempel di Gitlab project kita seperti gambar di bawah.
```
![Langkah 9](images-guide/laravel-gitlab-deployment/langkah-9.png)

## Mulai tahap 2
1. Langkah berikutnya memasang pustaka Laravel Deployer di project Laravel dengan perintah berikut.

```bash
composer require lorisleiva/laravel-deployer
```

2. Menjalankan perintah ```php artisan deploy:init``` dan Anda akan dihadapkan dengan beberapa pertanyaan serta setelah itu hasil pertanyaan tersebut akan di simpan dalam file ```config/deploy.php```.

3. Di dalam file deploy.php, kita buat konfigurasi seperti gist di bawah.

[Deploy with Laravel Deployer Setup](https://gist.github.com/satyakresna/f9b82fc7d599a34e61c37d43a47e28bf)

4. Di dalam file `deploy.php` tadi, kita memasukkan resep bernama `deploy_secrets.php`. Berikut konfigurasi gist nya.

[Deploy secrets setup for Laravel Deployer](https://gist.github.com/satyakresna/1acf9a1838b01c5f529c3b8ad1a24488)

## Mulai tahap 3
1. Membuat file ```.gitlab-ci.yml``` dan isinya Anda bisa lihat di [gist Github milik saya](https://gist.github.com/satyakresna/2091cc46a6dcef094d3f9ace4ae75d45).

2. Selanjutnya commit file ```.gitlab-ci.yml``` dan lakukan Git push dan hasilnya akan muncul **pipelines** seperti gambar di bawah.

![Langkah 9](images-guide/laravel-gitlab-deployment/langkah-9.png)

Catatan:
1. "$SSH_PRIVATE_KEY" diambil dari private key di CI/CD Gitlab kita tadi.
2. Perhatikan script bagian terakhir pada file ```.gitlab-ci.yml```.
```yml
production:
    stage: deploy
    script:
        - *init_ssh
        - *change_file_permissions
        - php artisan deploy yourdomain.com -vvv
    environment:
        name: production
        url: http://yourdomain.com
    when: manual # Perhatikan
    only:
        - master
```
Di sana fungsi manual adalah menyediakan fasilitas trigger manual untuk deployment, jika Anda menghilangkannya maka akan otomatis deploy. Untuk fasilitas trigger manual, Gitlab menyediakan tombol "play" pada gambar nomor 10. Jika Anda yakin dengan commit Anda buat dan lolos tes maka silahkan tekan tombol tersebut.

## Catatan

Ketika menggunakan teknik ini dan menggunakan server Nginx, tidak serta merta konten berubah. Hal ini dikarenakan OPcache tidak mampu mendeteksi perubahan file PHP secara akurat. Silakan buka tautan di bawah ini.

[Laravel (PHP 7.3) nginx conf](https://gist.github.com/satyakresna/9d59afb47a3ff64ab1d3bb3ba353f4cd)

## Sumber referensi
1. [Test and deploy Laravel applications with GitLab CI/CD and Envoy](https://docs.gitlab.com/ee/ci/examples/laravel_with_gitlab_and_envoy/#configure-the-production-server)
1. [Using GitLab's pipeline with Laravel](http://lorisleiva.com/using-gitlabs-pipeline-with-laravel/)
1. [Laravel Deployer Troubleshooting](https://github.com/lorisleiva/laravel-deployer/blob/master/docs/troubleshooting.md)

## Ucapan terima kasih dan mohon maaf
Terima kasih bagi Anda yang telah membaca tutorial ini dan jika berhasil mencobanya selamat! Mohon maaf bila tutorial ini saya buat buru-buru. Intinya saya membuat catatan kecil untuk diri saya jika saya lupa.
