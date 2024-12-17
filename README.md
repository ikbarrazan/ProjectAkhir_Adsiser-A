#Centralized Logging and Monitoring System Coin Raydium Menggunakan API Coinmarketcap

<img width="713" alt="ASSRES" src="https://github.com/user-attachments/assets/56974c8a-5159-43e4-aaea-1bab63a44ac1" />

Elastic Stack (ELK) adalah platform analitik yang terdiri dari Elasticsearch, Logstash, dan Kibana. ELK digunakan untuk mengelola, menganalisis, dan memvisualisasikan data secara real-time. Dalam proyek ini, ELK dirancang untuk mencatat perubahan harga dan metrik lainnya dari salah satu koin crypto, Raydium

### Logstash Instance:
- EC2 Instance dengan Ubuntu 22.04.
- Elastic IP untuk memungkinkan akses publik.
- Konfigurasi Logstash untuk mengambil data dari API Raydium dan mengirimnya ke Elasticsearch.
### Elasticsearch Instance:
- EC2 Instance dengan Ubuntu 22.04.
- Elastic IP untuk memungkinkan akses publik.
Dikonfigurasi untuk menyimpan dan mengindeks data yang diterima dari Logstash.
### Kibana Client:
- Laptop Lenovo V14 dengan OS Linux.
- Dikonfigurasi untuk menghubungkan Kibana ke Elasticsearch di AWS.

## Prerequisite
### Logstash:
- Sudah membuat AWS EC2 Instance dengan spek minimum menggunakan t3 Large
### Elastic Seach:
- Sudah membuat AWS EC2 Instance dengan spek minimum menggunakan t3 Large atau m5 Large
### Kibana:
- Memiliki device dengan spesifikasi minimal 4gb ram dengan OS Ubuntu 22.04
