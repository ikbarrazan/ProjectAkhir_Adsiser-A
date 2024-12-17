### Langkah-Langkah Konfigurasi ElasticSeach
1. Masuk ke server EC2 menggunakan SSH dengan kunci pribadi (elastic.pem). <br>
```
ssh -i "C:/Users/aqilf/Downloads/elastic.pem" ubuntu@ec2-54-236-122-226.compute-1.amazonaws.com -p 22000
```

<br>

2. Memperbarui daftar paket dari repositori untuk memastikan versi terbaru tersedia serta memperbarui semua paket yang terinstal ke versi terbaru dan mengkonfirmasi pembaruan secara otomatis. <br>
```
sudo apt-get update
sudo apt-get upgrade -y
```

<br>

3. Menginstal Java Development Kit (JDK) versi 11, yang diperlukan untuk menjalankan Elasticsearch. <br>
```
sudo apt-get install openjdk-11-jdk -y
```

<br>

4. Menginstal curl, gnupg, dan apt-transport-https yang diperlukan untuk mengunduh dan mengelola repositori Elasticsearch. <br>
```
sudo apt-get install curl gnupg apt-transport-https
```

<br>

5. Membuat folder khusus untuk menyimpan kunci GPG Elasticsearch.
6. Mengunduh dan mengimpor kunci GPG Elasticsearch ke sistem untuk memverifikasi paket dari repositori resmi.
7. Mengatur izin agar keyring Elasticsearch dapat diakses oleh sistem.
8. Menambahkan repositori Elasticsearch versi 7.x ke daftar repositori sistem. <br>
```
#5
sudo mkdir -p /etc/apt/keyrings

#6
curl --silent --location https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/keyrings/elasticsearch.gpg --import

#7
sudo chmod 644 /etc/apt/keyrings/elasticsearch.gpg

#8
echo "deb [signed-by=/etc/apt/keyrings/elasticsearch.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main
```

<br>

9. Memperbarui daftar paket dengan repositori Elasticsearch yang baru ditambahkan. <br>
```
sudo apt-get update
```

<br>

10. Menginstal Elasticsearch. <br>
```
sudo apt-get install elasticsearch
```

<br>

11. Mengedit Konfigurasi Elasticsearch <br>
```
#Konfigurasi utama Elasticsearch, seperti node name, network host, dan lainnya.
sudo nano /etc/elasticsearch/elasticsearch.yml

#Menyesuaikan opsi JVM pada bagian heap size.
sudo nano /etc/elasticsearch/jvm.optionsa

#Mengatur batasan sistem untuk Elasticsearch
sudo nano /etc/security/limits.conf

#Mengatur parameter kernel, yaitu vm.max_map_count
sudo nano /etc/sysctl.conf
```

<br>

12. Memeriksa apakah Elasticsearch berjalan dengan benar. <br>
```
sudo systemctl status elasticsearch
```

<br>
