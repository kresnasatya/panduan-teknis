# Membuat WordPress menjadi HTTPS
Dengan menggunakan fitur Let's Encrypt (gratis) dari Cpanel kita, kita dapat membuat website kita menjadi HTTPS. Saya mencoba membuat website pribadi saya (CMS WordPress) menjadi HTTPS

## Langkah-langkah
- Masuk ke WP Admin > Settings > General Settings:
    - Ubah WordPress Address (URL) anda dari `http://domainanda.com` menjadi `https://domainanda.com`
    - Ubah Side Address (URL) anda dari `http://domainanda.com` menjadi `https://domainanda.com`
- Setelah itu save changes dan cari file .htaccess kamu dan tambahkan script untuk redirect ke https di atas setting defaultnya WordPress.
```
# BEGIN HTTPS Redirection
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
# END HTTPS Redirection
 
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
```
- Save perubahan .htaccess tadi dan selamat website kamu sudah bisa menggunakan HTTPS. ;)

## Sumber
[Cara Membuat WordPress Menggunakan HTTPS (SSL) Redirect dari HTTP](https://situsali.com/other/cms/2015/11/07/cara-membuat-wordpress-menggunakan-https-ssl-redirect-dari-http/)