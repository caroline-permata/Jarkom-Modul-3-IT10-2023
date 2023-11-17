# Jarkom-Modul-3-IT10-2023

**Praktikum Jaringan Komputer Modul 3 - IT10**

## Topologi 

<a href="https://ibb.co/zNTqmsv"><img src="https://i.ibb.co/DLH0142/Topologi.jpg" alt="Topologi" border="0"></a>

## Configuration 

## Soal 1 
>Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.
### Configuration Dynamic
Aura 
```
auto eth0
iface eth0 inet dhcp

# Static config for eth1
auto eth1
iface eth1 inet static
	address 192.238.1.1
	netmask 255.255.255.0

# Static config for eth2
auto eth2
iface eth2 inet static
	address 192.238.2.1
	netmask 255.255.255.0

# Static config for eth3
auto eth3
iface eth3 inet static
	address 192.238.3.1
	netmask 255.255.255.0

# Static config for eth4
auto eth4
iface eth4 inet static
	address 192.238.4.1
	netmask 255.255.255.0
```

Revolte
```
auto eth0
iface eth0 inet dhcp
```

Richter
```
auto eth0
iface eth0 inet dhcp
```

Sein
```
auto eth0
iface eth0 inet dhcp
```

Stark
```
auto eth0
iface eth0 inet dhcp
```

### Configuration Static

Himmel
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.1.2
	netmask 255.255.255.0
	gateway 192.238.1.1
```

Helter
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.1.3
	netmask 255.255.255.0
	gateway 192.238.1.1
```

Denken
```
#Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.2.2
	netmask 255.255.255.0
	gateway 192.238.2.1
```

Eisen
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.2.3
	netmask 255.255.255.0
	gateway 192.238.2.1
```

Lugner
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.3.2
	netmask 255.255.255.0
	gateway 192.238.3.1
```

Linie
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.3.3
	netmask 255.255.255.0
	gateway 192.238.3.1
```

Lawine
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.3.4
	netmask 255.255.255.0
	gateway 192.238.3.1
```

Fern
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.4.2
	netmask 255.255.255.0
	gateway 192.238.4.1
```

Flamme
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.4.3
	netmask 255.255.255.0
	gateway 192.238.4.1
```

Frieren
```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.238.4.4
	netmask 255.255.255.0
	gateway 192.238.4.1
```
### `Heiter.sh`

### Hasil 
(hasil ping)

## Soal 2 - 5 
> Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80 (2)

> Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168 (3)

> Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut (4)

> Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit (5)

Untuk melakmenjalankan nomor 2,3, dan 5, pada DHCP Server atau `Himmel` jalankan perintah 
```
echo 'subnet 192.238.1.0 netmask 255.255.255.0 {}

subnet 192.238.3.0 netmask 255.255.255.0 {
    // Nomor 2
    range 192.238.3.16 192.238.3.32;
    range 192.238.3.64 192.238.3.80;

    option routers 192.238.3.1;
    option broadcast-address 192.238.3.255;
    option domain-name-servers 192.238.1.3;

    // Nomor 5
    default-lease-time 180;
    max-lease-time 5760;
}

subnet 192.238.4.0 netmask 255.255.255.0 {
    // Nomor 3
    range 192.238.4.12 192.238.4.20;
    range 192.238.4.160 192.238.4.168;
    option routers 192.238.4.1;
    option broadcast-address 192.238.4.255;
    option domain-name-servers 192.238.1.3;
    default-lease-time 720;
    max-lease-time 5760;
}' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```
Sedangkan untuk nomor 4, pada `Heiter` jalankan perintah 
``` 
echo 'options {
directory "/var/cache/bind";
forwarders {
  192.168.122.1;
};
// dnssec-validation auto;
allow-query{any;};
listen-on-v6 { any; };
};'> /etc/bind/named.conf.options

```

## Soal 6
> Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3.


### Hasil


## Soal 7 
> Kepala suku dari Bredt Region memberikan resource server sebagai berikut: Lawine, 4GB, 2vCPU, dan 80 GB SSD. Linie, 2GB, 2vCPU, dan 50 GB SSD. Lugner 1GB, 1vCPU, dan 25 GB SSD. aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second.


### Hasil 

## Soal 8 
> Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut: Nama Algoritma Load Balancer, Report hasil testing pada Apache Benchmark, Grafik request per second untuk masing masing algoritma, Analisis 


### Hasil 


## Soal 9
> Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire.

### Hasil 


## Soal 10
> Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/

### Hasil 


## Soal 11
> Lalu buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman https://www.its.ac.id. hint: (proxy_pass)

### Hasil 


## Soal 12
> Selanjutnya LB ini hanya boleh diakses oleh client dengan IP [Prefix IP].3.69, [Prefix IP].3.70, [Prefix IP].4.167, dan [Prefix IP].4.168. hint: (fixed in dulu clinetnya)

### Hasil 


## Soal 13
> Semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern. 

Lakukan Setup pada `Database Server` atau `Denken`
```
mysql <<EOF
CREATE USER 'kelompokit10'@'%' IDENTIFIED BY 'passwordit10';
CREATE USER 'kelompokit10'@'localhost' IDENTIFIED BY 'passwordit10';
CREATE DATABASE dbkelompokit10;
GRANT ALL PRIVILEGES ON *.* TO 'kelompokit10'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'kelompokit10'@'localhost';
FLUSH PRIVILEGES;
quit
EOF

echo '[client-server]

# Import all .cnf files from configuration directory
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

[mysqld]
skip-networking=0
skip-bind-address' > /etc/mysql/my.cnf

service mysql restart
```

### Hasil 
Jalankan Perintah `mariadb --host=192.238.2.2 --port=3306 --user=kelompokit10 --password=passwordit10`, lalu `SHOW DATABASES;` pada worker.

<a href="https://ibb.co/3WnZ6KN"><img src="https://i.ibb.co/ctjnfqF/Nomer13.jpg" alt="Nomer13" border="0"></a>

## Soal 14
> Frieren, Flamme, dan Fern memiliki Riegel Channel sesuai dengan quest guide berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer

Pada Laravel worker,
```
# Update package list
apt-get update

# Install dependencies
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2

# Download and add GPG key for the PHP repository
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg

# Add PHP repository to sources.list.d
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'

# Update package list again
apt-get update

# Install PHP and related packages
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y

# Install Nginx
apt-get install nginx -y

# Download and install Composer
wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
mv composer.phar /usr/bin/composer

# Install Git
apt-get install git -y

# Clone the Laravel project and navigate to the project directory
cd /var/www
git clone https://github.com/martuafernando/laravel-praktikum-jarkom
cd laravel-praktikum-jarkom

# Update Composer dependencies
composer update

# Install Composer dependencies
composer install

# Copy the environment file
cp /var/www/laravel-praktikum-jarkom/.env.example /var/www/laravel-praktikum-jarkom/.env
```

Setelah melakukan hal diatas, lakukan konfigurasi untuk tiap tiap worker dengan menggunakan perintah 
```
echo '
APP_NAME=Laravel
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=192.238.2.2
DB_PORT=3306
DB_DATABASE=dbkelompokit10
DB_USERNAME=kelompokit10
DB_PASSWORD=passwordit10

BROADCAST_DRIVER=log
CACHE_DRIVER=file
FILESYSTEM_DISK=local
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

MEMCACHED_HOST=127.0.0.1

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=mt1

VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_HOST="${PUSHER_HOST}"
VITE_PUSHER_PORT="${PUSHER_PORT}"
VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"'> .env
php artisan migrate:fresh
php artisan db:seed --class=AiringsTableSeeder
php artisan key:generate
php artisan config:cache
php artisan migrate
php artisan storage:link
php artisan jwt:secret
php artisan config:clear
```


Lalu, lakukan konfigurasi nginx pada masing masing worker dengan menjalankan perintah 
```
echo 'server {

    listen 8001; # Fern
    listen 8002; # Flamme
    listen 8003; # Frieren

    root /var/www/laravel-praktikum-jarkom/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}' > /etc/nginx/sites-available/implementasi

ln -s /etc/nginx/sites-available/implementasi /etc/nginx/sites-enabled/
chown -R www-data.www-data /var/www/laravel-praktikum-jarkom/storage
service php8.0-fpm start

service nginx restart 
```
catatan: sesuaikan port untuk masing masing worker sesuai dengan ketentuan soal

### Hasil 
Jalankan perintah `lynx localhost:8001` pada worker 

<a href="https://ibb.co/BB3MYBS"><img src="https://i.ibb.co/Wf5JRfY/Nomer14.jpg" alt="Nomer14" border="0"></a>

## Soal 15
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second untuk `POST /auth/register` . Tambahkan response dan hasil testing pada grimoire.

Pada `client` masukan konfigurasi `.json` dengan memasukkan perintah 
```
echo '{
  "username": "kelompokit10",
  "password": "passwordit10"
}' > register.json 
```

### Hasil 
Jalankan perintah `ab -n 100 -c 10 -p register.json -T application/json http://192.238.4.2:8001/api/auth/register` pada `client`

<a href="https://ibb.co/Smnsf9v"><img src="https://i.ibb.co/09MDsdJ/Nomer15.jpg" alt="Nomer15" border="0"></a>

## Soal 16
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second untuk `POST /auth/login` . Tambahkan response dan hasil testing pada grimoire.

Pada `client` masukan konfigurasi `.json` dengan memasukkan perintah 
```
echo '{
  "username": "kelompokit10",
  "password": "passwordit10"
}' > login.json 
```

### Hasil 
Jalankan perintah `ab -n 100 -c 10 -p login.json -T application/json http://192.238.4.2:8001/api/auth/login` pada `client`

<a href="https://ibb.co/W6f9LRW"><img src="https://i.ibb.co/FKzvFdb/Nomer16.jpg" alt="Nomer16" border="0"></a>

## Soal 17 
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second untuk `GET /me` . Tambahkan response dan hasil testing pada grimoire.

Dapatkan token untuk mengakses endpoint, lalu set token secara global dengan perintah 
```
curl -X POST -H "Content-Type: application/json" -d @login.json http://192.238.4.2:8001/api/auth/login > login_output.txt
token=$(cat login_output.txt | jq -r '.token')
```

### Hasil 
Jalankan perintah `ab -n 100 -c 10 -H "Authorization: Bearer $token" http://192.238.4.2:8001/api/me` pada client 

<a href="https://ibb.co/CV8BXpv"><img src="https://i.ibb.co/WB5ndNF/Nomer17.jpg" alt="Nomer17" border="0"></a>

## Soal 18
> Untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern.

### Hasil 


## Soal 19
> Untuk meningkatkan performa dari Worker, coba implementasikan PHP-FPM pada Frieren, Flamme, dan Fern. Untuk testing kinerja naikkan: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Sebanyak tiga percobaan dan lakukan testing sebanyak 100 request dengan 10 request/second kemudian berikan hasil analisisnya pada Grimoire.


### Hasil 


## Soal 20
> Nampaknya hanya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa dari worker maka implementasikan Least-Conn pada Eisen. Untuk testing kinerja dari worker tersebut dilakukan sebanyak 100 request dengan 10 request/second. 



### Hasil 



