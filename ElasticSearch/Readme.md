### Langkah-Langkah Konfigurasi ElasticSeach
1. Masuk ke server EC2 menggunakan SSH dengan kunci pribadi (elastic.pem). <br>
```
ssh -i "C:/Users/aqilf/Downloads/elastic.pem" ubuntu@ec2-54-236-122-226.compute-1.amazonaws.com -p 22000
```
![Screenshot 2024-12-11 122253](https://github.com/user-attachments/assets/7c1d34b1-d9c2-44c5-bc8f-76ec5650afbf)
<br>

2. Memperbarui daftar paket dari repositori untuk memastikan versi terbaru tersedia serta memperbarui semua paket yang terinstal ke versi terbaru dan mengkonfirmasi pembaruan secara otomatis. <br>
```
sudo apt-get update
sudo apt-get upgrade -y
```
![Screenshot 2024-12-11 122312](https://github.com/user-attachments/assets/0a03327e-c077-4862-a94b-bd0cc29c883f)
![Screenshot 2024-12-11 122312](https://github.com/user-attachments/assets/5d20f294-4769-4582-8ed7-859153fa0f57)
<br>

3. Menginstal Java Development Kit (JDK) versi 11, yang diperlukan untuk menjalankan Elasticsearch. <br>
```
sudo apt-get install openjdk-11-jdk -y
```
![Screenshot 2024-12-11 122312](https://github.com/user-attachments/assets/5d9dcca8-610d-4dad-8e0f-4d82a0b357c3)
<br>

4. Menginstal curl, gnupg, dan apt-transport-https yang diperlukan untuk mengunduh dan mengelola repositori Elasticsearch. <br>
```
sudo apt-get install curl gnupg apt-transport-https
```
![Screenshot 2024-12-11 122312](https://github.com/user-attachments/assets/3acbd45b-23a1-4d37-9d1c-9fca8f2d9235)
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
![Screenshot 2024-12-11 122757](https://github.com/user-attachments/assets/17704cbe-8976-4563-9202-39b77f80bc2f)
<br>

9. Memperbarui daftar paket dengan repositori Elasticsearch yang baru ditambahkan. <br>
```
sudo apt-get update
```
![Screenshot 2024-12-11 122822](https://github.com/user-attachments/assets/2c241b0f-76eb-45dc-8e48-9d7234844f1b)
<br>

10. Menginstal Elasticsearch. <br>
```
sudo apt-get install elasticsearch
```
![Screenshot 2024-12-11 122949](https://github.com/user-attachments/assets/9c1a4aeb-d8ba-47bc-8b76-36c14ee8fe24)
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
![Screenshot 2024-12-11 123040](https://github.com/user-attachments/assets/7ef8d4ea-0070-4b05-8fee-bfb109c3f067)
![Screenshot 2024-12-11 123110](https://github.com/user-attachments/assets/e4f67caa-796a-41e9-a3ba-cec8c86cd232)
![Screenshot 2024-12-11 123208](https://github.com/user-attachments/assets/3d25ddae-5fec-4f3b-b12a-cd645b62052f)
![Screenshot 2024-12-11 123258](https://github.com/user-attachments/assets/79e80453-4a31-483c-8f69-6adcffc7d465)
<br>

12. Memeriksa apakah Elasticsearch berjalan dengan benar. <br>
```
sudo systemctl status elasticsearch
```
![Screenshot 2024-12-11 123340](https://github.com/user-attachments/assets/3756d2c4-0059-4e65-98fe-ffaecc4b349e)
<br>

13. Melihat detail indeks raydium, termasuk konfigurasi, mapping, dan data lainnya. <br>
```
curl -X GET "http://54.236.122.226:9200/raydium?pretty" -H 'Content-Type: application/json'
```
![{32BDAF6E-6FCA-4214-8C08-1CB814D1A37C}](https://github.com/user-attachments/assets/bd2edad1-4bd6-4a40-8552-25c8cfbfba37)
<br>

14. Menampilkan semua indeks yang ada di Elasticsearch dengan statusnya. <br>
```
curl -X GET "54.236.122.226:9200/_cat/indices"
```
![{39A84ADE-5038-465A-943A-C3F70737B123}](https://github.com/user-attachments/assets/41c62689-e466-4c2e-86f2-ca9cd4eb06fa)
<br>
