---
title: 'Debian 10 Install LEMP WordPress & SSL Lets Encrypt'
layout: single
toc: true
---
# Latar Belakang
Tulisan ini adalah lanjutan dari tulisan sebelumnya, setelah selesai install LEMP stack akan kita lanjutkan dengan installasi dan konfigurasi CMS Wordpress dan SSL Let's Encrypt.

# Install Wordpress
Pindah ke folder /tmp dan download wordpress menggunakan wget.  
`sudo cd /tmp`  
`sudo wget https://wordpress.org/latest.tar.gz`

Extract dan pindahkan folder wordpress ke folder default untuk website.  
`sudo tar -zxvf latest.tar.gz`  
`sudo mv wordpress /var/www/html/wordpress`

Modify directory owner permission wordpress.  
`sudo chown -R www-data /var/www/html/wordpress`

Install curl, dan download kode API dari wordpress untuk optimasi wp-config. Simpan API key tersebut nanti akan digunakan pada saat edit file wp-config. Kode API ini bersifat unik dan berbeda pada setiap kali generate.  
`sudo apt install curl`  
`sudo curl -s https://api.wordpress.org/secret-key/1.1/salt/`  
```
define(‘AUTH_KEY’, ‘YVeHd u}_=T^)a]/@7RC_6&gt;gC/+6;^bpv@nq{TY0E_P g7+LaXT0 MGY&*B)/i6]v’);
define(‘SECURE_AUTH_KEY’, ‘]6v.q9E*x@S+Az_9|-&#91;hlpt,rx+lz@oa+%l.EI=:m6Ia~POdAq|E WSIi@^$93j(#’);
define(‘LOGGED_IN_KEY’, ‘1w4.q?72XOh&#91;-X^sa @|N]p!:I-]a?&lt;K9AO7VQ-kYjYzRLoY;Tzn $BRtFlo+4&gt;~n’);
define(‘NONCE_KEY’, ‘cUB$u1H9fu2T#YQ]M)-.*Y4UMK2Tl1zM/-3dI%IT%Mnu!7Cw/XJJ #4&#91;jR:WvtE3_’);
define(‘AUTH_SALT’, ‘3f.6E&]}m$B/&lt;2$&lt;7}r1tB YFAO-LcWsD–ZCFB!(mq7Quk%SoWF FSDFK%$)muW&gt;’);
define(‘SECURE_AUTH_SALT’, ‘AR(:#tD|x.J}hK8rY^H:Go&lt;qx8owyv1YGj=U6SMm,^JJKY}Actd- 7ynI(F%E=#-h’);
define(‘LOGGED_IN_SALT’, ‘x:,jXt*vpXHu)W~/oYF4Nxl@7Tg(3w-sj(E+;.rv-DI-dSB.O-!L Dyz-s*-&gt;45pR’);
define(‘NONCE_SALT’, ‘)+];+~jza]il/D;mc&gt;g(eUe+A0.lV2i4gQsjM281.J%1Cl 3d&lt;Y2 +ZnL#nfkda0#’);
```

Copy file wp-config untuk installasi wordpress.  
`sudo cp /var/www/html/wordpress/wp-config-sample.php /var/www/html/wordpress/wp-config.php`

Edit file wp-config, dan sesuaikan pengaturan untuk akses ke database yang sudah kita buat sebelumnya. Perhatikan text untuk nama database, username, dan password. Dan text untuk kode API yang sudah kita download sebelumnya.  
`sudo nano /var/www/html/wordpress/wp-config.php`  
```
<?php
/**
* The base configuration for WordPress
*
* The wp-config.php creation script uses this file during the
* installation. You don’t have to use the web site, you can
* copy this file to “wp-config.php” and fill in the values.
*
* This file contains the following configurations:
*
* * MySQL settings
* * Secret keys
* * Database table prefix
* * ABSPATH
*
* @link https://codex.wordpress.org/Editing_wp-config.php
*
* @package WordPress
*/

// ** MySQL settings – You can get this info from your web host ** //
/** The name of the database for WordPress */
define( ‘DB_NAME’, ‘wordpress’ );

/** MySQL database username */
define( ‘DB_USER’, ‘wpuser’ );

/** MySQL database password */
define( ‘DB_PASSWORD’, ‘p4ssw0rd’ );

/** MySQL hostname */
define( ‘DB_HOST’, ‘localhost’ );

/** Database Charset to use in creating database tables. */
define( ‘DB_CHARSET’, ‘utf8’ );

/** The Database Collate type. Don’t change this if in doubt. */
define( ‘DB_COLLATE’, ” );

/**#@+
* Authentication Unique Keys and Salts.
*
* Change these to different unique phrases!
* You can generate these using the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-key service}
* You can change these at any point in time to invalidate all existing cookies. This will force all users to have to log in again.
*
* @since 2.6.0
*/
define(‘AUTH_KEY’, ‘YVeHd u}_=T^)a]/@7RC_6>gC/+6;^bpv@nq{TY0E_P g7+LaXT0 MGY&*B)/i6]v’);
define(‘SECURE_AUTH_KEY’, ‘]6v.q9E*x@S+Az_9|-[hlpt,rx+lz@oa+%l.EI=:m6Ia~POdAq|E WSIi@^$93j(#’);
define(‘LOGGED_IN_KEY’, ‘1w4.q?72XOh[-X^sa @|N]p!:I-]a?<K9AO7VQ-kYjYzRLoY;Tzn $BRtFlo+4>~n’);
define(‘NONCE_KEY’, ‘cUB$u1H9fu2T#YQ]M)-.*Y4UMK2Tl1zM/-3dI%IT%Mnu!7Cw/XJJ #4[jR:WvtE3_’);
define(‘AUTH_SALT’, ‘3f.6E&]}m$B/<2$<7}r1tB YFAO-LcWsD–ZCFB!(mq7Quk%SoWF FSDFK%$)muW>’);
define(‘SECURE_AUTH_SALT’, ‘AR(:#tD|x.J}hK8rY^H:Go<qx8owyv1YGj=U6SMm,^JJKY}Actd- 7ynI(F%E=#-h’);
define(‘LOGGED_IN_SALT’, ‘x:,jXt*vpXHu)W~/oYF4Nxl@7Tg(3w-sj(E+;.rv-DI-dSB.O-!L Dyz-s*->45pR’);
define(‘NONCE_SALT’, ‘)+];+~jza]il/D;mc>g(eUe+A0.lV2i4gQsjM281.J%1Cl 3d<Y2 +ZnL#nfkda0#’);

/**#@-*/

/**
* WordPress Database Table prefix.
*
* You can have multiple installations in one database if you give each
* a unique prefix. Only numbers, letters, and underscores please!
*/
$table_prefix = ‘wp_’;

/**
* For developers: WordPress debugging mode.
*
* Change this to true to enable the display of notices during development.
* It is strongly recommended that plugin and theme developers use WP_DEBUG
* in their development environments.
*
* For information on other constants that can be used for debugging,
* visit the Codex.
*
* @link https://codex.wordpress.org/Debugging_in_WordPress
*/
define( ‘WP_DEBUG’, false );

/* That’s all, stop editing! Happy publishing. */

/** Absolute path to the WordPress directory. */
if ( ! defined( ‘ABSPATH’ ) ) {
define( ‘ABSPATH’, dirname( __FILE__ ) . ‘/’ );
}

/** Sets up WordPress vars and included files. */
require_once( ABSPATH . ‘wp-settings.php’ );
```

# Optimasi Nginx Untuk Wordpress
Buka file konfigurasi Nginx  
`sudo nano /etc/nginx/nginx.conf`  
```
...
keepalive_timeout 2;
...
```

Setup nginx virtual hosts, sesuikan nama websitenya. Dalam tulisan ini contoh nama websitenya example.com  
`sudo nano /etc/nginx/sites-available/wordpress`  
```
server {
listen 80;
listen [::]:80;
root /var/www/html/wordpress;
index index.php index.html index.htm;
server_name example.com www.example.com;
1
	
client_max_body_size 100M;

location / {
try_files $uri $uri/ =404;
}

location ~ [^/]\.php(/|$) {
include snippets/fastcgi-php.conf;
fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
include fastcgi_params;
}

}
```

Buat sysmlink dari etc/nginx/sites-available/wordpress ke /etc/nginx/sites-enabled  
`sudo ln -s /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/`

Test konfigurasi nginx, apabila tidak ada error seharusnya konfigurasi sudah running dengan benar.  
`sudo nginx -t`


# Jalankan Konfigurasi Wordpress
Akses wordpress dari browser dengan memanggil alamat ip address server anda.  
Lakukan installasi wordpress.

# Install SSL Let's Encrypt
# Install SSL
```
sudo apt update
sudo apt install python3-acme python3-certbot python3-mock python3-openssl python3-pkg-resources python3-pyparsing python3-zope.interface
sudo apt install python3-certbot-nginx
```

Edit konfigurasi nginx.  
`sudo nano /etc/nginx/sites-available/wordpress`  
```
...
server_name example.com www.example.com;
...
```

Test konfigurasi nginx dan restart nginx, kalau ngak ada error lanjut.  
```
sudo nginx -t
sudo systemctl restart nginx
```

# Obtain SSL
Jalankan perintah untuk mendapatkan SSL  
`sudo certbot --nginx -d example.com -d www.example.com`

# Test Renew SSL
Test certbot untuk renew SSL  
`sudo certbot renew --dry-run`

Done! kalau tidak ada error, SSL berhasil didapatkan dan akan otomatis di renew oleh certbot.

Salam,
