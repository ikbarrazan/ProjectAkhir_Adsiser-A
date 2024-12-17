*Baca untuk perintah Logstash*

#### 1. Menghubungkan instance melalui CMD <br>
```
ssh -i “C:\Users\bhann\Downloads\logstashBhan.pem” ubuntu@ec2-18-233-241-75.compute-1.amazonaws.com -p 22000
```

#### 2. Melakukan update dan upgrade pada ubuntu <br>
```
sudo apt update && sudo apt upgrade -y
``` 

#### 3. Setelah update, langsung instalasi java <br>

```
# Instalasi Java
sudo apt install openjdk-11-jdk -y

# Verifikasi Java sudah terinstall
java -version
```

#### 4. Setelah java terinstall, tambah repository Logstash untuk instalasi <br>
```
# Menambahkan GPG key dari elastic ke sistem
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

# Menambahkan repository ke source.list
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

# Memperbarui paket
sudo apt update
```

#### 5. Instalasi logstash <br>
```
# Instalasi Logstash
sudo apt install logstash -y

# Verifikasi Logstash sudah terinstall
logstash –version
```

#### 6. Masuk ke konfigurasi pipeline dan masukkan kode yang ada di github <br>
```
sudo nano /etc/logstash/conf.d/logstash-pipeline.conf
```

#### 7. Masuk ke konfigurasi yml pada Logstash utama dan sesuaikan seperti di bawah <br>
```
# Bind ke semua network interface
http.host: "0.0.0.0"

# Jalankan pipeline otomatis
path.config: "/etc/logstash/conf.d/*.conf"
```

#### 8. Setelah itu jalankan Logstash dan cek apakah sudah berjalan <br>
```
sudo systemctl enable logstash

sudo systemctl start logstash

sudo systemctl status logstash
```

#### 9. Cek apakah pipeline logstash benar-benar sudah mengambil data
```
sudo /usr/share/logstash/bin/logstash -f /etc/logstash/conf.d/logstash-pipeline.conf
```
