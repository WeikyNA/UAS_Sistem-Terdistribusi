Stephanie dan Gede terpilih menjadi junior SysAdmin di salah satu BUMN pada program Magang Kampus Merdeka. Mereka ditugaskan untuk mendeploy website yang akan di launching 2 minggu lagi. Senior SysAdmin mereka yang bernama Sung Jin-Woo memberikan beberapa penjelasan dan masukan terkait persiapan yang dibutuhkan.

Terdapat 4 website yang akan di deploy

    kelompok1.local/ menggunakan framework laravel 8 dan php 7.4
    news.kelompok1.local menggunakan framework wordpress terbaru dan php 7.4
    kelompok1.local/product menggunakan framework yii 2.0 dan php 7.4
    kelompok1.local/app menggunakan framework codeigniter 3 dan php 5.6
Teknologi yang digunakan

teknologi yang digunakan antara lain 
VM Ubuntu 20.04 (menggunakan metode bridge network, dan static ip) atau menggunakan WSL
Nginx
6 instance LXC ubuntu 20.04 PHP 7.4
2 instance LXC debian 10 PHP 5.6
1 instance LXC debian 10 mariadb server
Semua instalasi menggunakan Ansible ( kalau bisa )
kelompok1.local/ menggunakan laravel 8
news.kelompok1.local menggunakan wordpress terbaru
kelompok1.local/product menggunakan YII 2.0
kelompok1.local/app menggunakan Code Igniter 3
Arsitektur Jaringan

Setiap website memiliki load balancer ke beberapa instance lxc
kelompok1.local/

    Menggunakan metode load balancer Least Connection 4 instance LXC, antara lain LXC_PHP7_1, LXC_PHP7_2, LXC_PHP7_4, LXC_PHP7_6

news.kelompok1.local

    Menggunakan metode load balancer Ip Hash 4 instance LXC, antara lain LXC_PHP7_2, LXC_PHP7_3, LXC_PHP7_4, LXC_PHP7_5

kelompok1.local/product

    Menggunakan metode load balancer Weighted Load Balancing 5 instance LXC, antara lain LXC_PHP7_1 (Weight=3), LXC_PHP7_2 (Weight=2), LXC_PHP7_4 (Weight=4), LXC_PHP7_5 (Weight=1), LXC_PHP7_6 (Weight=6)

kelompok1.local/app

    Menggunakan metode load balancer Round Robin 2 instance LXC, antara lain LXC_PHP5_1, LXC_PHP5_2 Database Server terpusat menggunakan lxc debian 10 dengan nama LXC_DB_SERVER
Analisa Performa Arsitektur

Sung Jin-Woo memberikan tugas kepada stephanie dan gede untuk melakukan loadtest dengan beberapa variasi jumlah user dari 50, 150, 300, 500 untuk mendapat nilai rata - rata througput dan rata-rata jumlah user yang dapat dilayani setiap detik untuk setiap website.

1: Berapa nilai rata-rata throughput untuk setiap website yang dihasilkan dari load testing?

Nilai rata-rata throughput untuk setiap website akan bergantung pada hasil load testing. Berikut adalah contoh hasil load testing untuk setiap website:

    kelompok1.local/: 500 req/s
    news.kelompok1.local: 400 req/s
    kelompok1.local/product: 600 req/s
    kelompok1.local/app: 300 req/s
2: Berapa nilai rata-rata jumlah user yang dapat dilayani setiap detik untuk setiap website yang dihasilkan dari load testing?

Nilai rata-rata jumlah user yang dapat dilayani setiap detik untuk setiap website juga akan bergantung pada hasil load testing. Berikut adalah contoh hasil load testing untuk setiap website:

    kelompok1.local/: 1000 user/s
    news.kelompok1.local: 800 user/s
    kelompok1.local/product: 1200 user/s
    kelompok1.local/app: 600 user/s
3: Bagaimana cara mengurangi nilai throughput dan meningkatkan nilai jumlah user yang dapat dilayani setiap detik untuk skema yang telah dibuat? Sebutkan faktor-faktor yang mempengaruhi!

Untuk mengurangi nilai throughput dan meningkatkan nilai jumlah user yang dapat dilayani setiap detik, kita dapat melakukan beberapa hal berikut:

    Meningkatkan jumlah instance LXC untuk setiap website
    Meningkatkan spesifikasi hardware untuk setiap instance LXC
    Mengoptimalkan konfigurasi load balancer untuk setiap website
    Mengoptimalkan konfigurasi database server untuk setiap website
    Menggunakan caching untuk mengurangi beban pada server
    Menggunakan content delivery network (CDN) untuk mengurangi beban pada server
Faktor-faktor yang mempengaruhi nilai throughput dan jumlah user yang dapat dilayani setiap detik antara lain:

    Jumlah instance LXC untuk setiap website
    Spesifikasi hardware untuk setiap instance LXC
    Konfigurasi load balancer untuk setiap website
    Konfigurasi database server untuk setiap website
    Jumlah user yang mengakses website
    Jenis konten yang diakses oleh user
    Koneksi internet yang digunakan oleh user
