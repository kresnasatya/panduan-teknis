# CodeIgniter Config
Konfigurasi sederhana CodeIgniter 3.X

## Setting Dynamic Base URL
Secara umum, kita harus men-setting base URL secara manual misalnya `$config['base_url']= 'http://localhost/namaproject';`.<br>
Tetapi, kita bisa men-setting secara dinamis dengan mengubah `$config['base_url']` seperti pada sintaks di bawah ini: <br>

```
$config['base_url'] = ((isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] == "on") ? "https" : "http");
$config['base_url'] .= "://".$_SERVER['HTTP_HOST'];
$config['base_url'] .= str_replace(basename($_SERVER['SCRIPT_NAME']),"",$_SERVER['SCRIPT_NAME']);
```
Silahkan di **copy paste** ke dalam file `config.php` . Dengan Base URL yang dinamis, kita tidak perlu men-setting secara manual. :)

## Clean and Pretty URL
Ketika men-download framework CodeIgniter dan menjalankannya di browser biasanya formatnya seperti berikut:<br>
`http://namaproject/index.php/namacontroller/namamethod`.<br>
Untuk menghilangkan `index.php` kita ubah `$config['index_page'] = 'index.php';` menjadi `$config['index_page'] = '';`. dan membuat file .htaccess di root project utama kita dengan sintaks di bawah ini (Silahkan di **copy paste**):<br>

```
<IfModule mod_rewrite.c>
  Options -Indexes

  RewriteEngine On
  RewriteCond $1 !^(index\\.php|resources|robots\\.txt)
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^(.+)$ index.php?/$1 [L,QSA]
</IfModule>
```

## Terima Kasih
1. [Avenir](http://avenir.ro/codeigniter-tutorials/removing-the-index-php-from-the-url-and-allow-the-use-of-search-engine-friendly-urls/) <br>
2. [MbahCoding](http://mbahcoding.com/php/codeigniter/codeigniterdynamic-base-url.html) <br>
