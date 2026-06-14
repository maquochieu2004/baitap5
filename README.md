# baitap5
# Triển khai hệ thống Monitor & Alert Data Real-Time bằng Docker

## Giới thiệu

Hệ thống được xây dựng nhằm giám sát dữ liệu Bitcoin theo thời gian thực. Dữ liệu được thu thập tự động, lưu trữ trên cơ sở dữ liệu và cung cấp qua API để hiển thị trên giao diện Web.

## Thành phần hệ thống

* MariaDB: Lưu dữ liệu thời gian thực.
* InfluxDB: Lưu dữ liệu lịch sử.
* Flask API: Thu thập và cung cấp dữ liệu.
* Nginx: Web Server và Reverse Proxy.
* Grafana (mở rộng): Hiển thị Dashboard giám sát.

## Triển khai bằng Docker Compose

Khởi động toàn bộ hệ thống:

```bash
docker compose up -d
```

Kiểm tra trạng thái các container:

```bash
docker ps
```

Truy cập giao diện:

```text
http://IP_SERVER
```

Kiểm tra API:

```bash
curl http://IP_SERVER/api/price
```

## Triển khai trên máy chủ Offline

### Bước 1: Xuất Docker Image

```bash
docker save mariadb:10.6 > mariadb.tar
docker save influxdb:1.8 > influxdb.tar
docker save nginx:latest > nginx.tar
docker save python:3.10 > python.tar
```

### Bước 2: Sao chép dữ liệu

Chép các file `.tar`, mã nguồn và file `docker-compose.yml` sang máy chủ bằng USB hoặc mạng LAN.

### Bước 3: Nạp Image

```bash
docker load < mariadb.tar
docker load < influxdb.tar
docker load < nginx.tar
docker load < python.tar
```

### Bước 4: Khởi động hệ thống

```bash
docker compose up -d
```

## Kết quả

* Thu thập dữ liệu Bitcoin thời gian thực.
* Lưu trữ dữ liệu trên MariaDB và InfluxDB.
* Hiển thị dữ liệu trên giao diện Web.
* Cung cấp API cho ứng dụng bên ngoài.
* Có khả năng mở rộng Dashboard Grafana và gửi cảnh báo Telegram.

Hệ thống được đóng gói bằng Docker giúp triển khai nhanh, đồng nhất môi trường và hoạt động được cả trên máy chủ không có kết nối Internet.
## Kết quả

<img width="1630" height="821" alt="image" src="https://github.com/user-attachments/assets/9618fc80-2c22-4fb7-b3f8-1dd9ac18e301" />

<img width="1908" height="893" alt="image" src="https://github.com/user-attachments/assets/dc827481-6065-40f1-9203-e00ece30864a" />

<img width="1312" height="725" alt="image" src="https://github.com/user-attachments/assets/46a22e68-5e62-45a7-8aa0-98f0286c31ae" />

<img width="1515" height="1038" alt="image" src="https://github.com/user-attachments/assets/296dd298-a0ab-4bca-8044-9181c9b7cb22" />

<img width="1499" height="1049" alt="ca445c70-3e30-48a4-9c1a-a7884b2559d0" src="https://github.com/user-attachments/assets/4812995f-ddd0-4fc5-9677-e5186d099e0e" />


