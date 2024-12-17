*Baca untuk perintah Kibana*

#### 1. menginstall Kibana pada instance kibana-dashboard <br>
```ubuntu 22.04
# Import the Elasticsearch public GPG key
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

# Add the Elastic source list to sources.list.d directory
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

# Update package list
sudo apt-get update

# Install Kibana
sudo apt-get install kibana
```

#### 2. Mengkonfigurasi Kibana. File konfigurasi utama berada di <br>
```/etc/kibana/kibana.yml``` <br>

Masukkan/modifikasi file konfigurasi pada ```kibana.yml``` sesuai pada file ```Kibana.yml``` di folder *Kibana* Github ini

#### 3. Setelah konfigurasi, kita perlu mengatur permission dan memulai service: <br>

```
# Set proper permissions
sudo chown -R kibana:kibana /etc/kibana/
sudo chown -R kibana:kibana /var/log/kibana/

# Enable Kibana service to start on boot
sudo systemctl enable kibana

# Start Kibana service
sudo systemctl start kibana

# Check status
sudo systemctl status kibana
```

#### 4. Verifikasi log untuk memastikan tidak ada error: <br>
```
# Check logs
sudo tail -f /var/log/kibana/kibana.log
```

#### 5. Verifikasi koneksi ke Elasticsearch:
```
# Test Elasticsearch connection
curl -X GET "http://YOUR_ELASTICSEARCH_IP:9200/_cat/health"
```

#### 6. Untuk memverifikasi bahwa Kibana berjalan dengan baik, akses melalui browser: <br>
```
http://localhost:5601
```

#### 7. Modifikasi dashboard sesuai kebutuhan anda
*contoh: *
<img width="713" alt="ASSRES" src="https://github.com/user-attachments/assets/71e12d4d-a886-4d2e-983d-b0f744a40f16" />
