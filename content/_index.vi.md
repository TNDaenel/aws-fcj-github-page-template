title : "Session Management"
weight : 1 
chapter : false
weight : 1 
chapter : false
---
# Triển khai hệ thống thương mại điện tử trên EC2 + S3 + MongoDB

### Tổng quan


Dự án này nhằm triển khai một hệ thống **thương mại điện tử fullstack** sử dụng **ReactJS (frontend)**, **NodeJS/Express (backend)** và **MongoDB (database)** trên nền tảng **hạ tầng AWS**. Quy trình triển khai tuân theo phương pháp **CI/CD tự động với GitHub Actions**, đảm bảo việc build – test – deploy được thực hiện mượt mà, có kiểm soát.

Kiến trúc triển khai bao gồm:

* **Frontend (ReactJS)** được build và **host trên Amazon S3** như một trang web tĩnh.
* **Backend (NodeJS/Express)** được triển khai trên **EC2 Instance**, xử lý API và giao tiếp với database.
* **MongoDB** có thể được cài đặt trên EC2 hoặc sử dụng MongoDB Atlas (nếu cloud-managed).
* **Amazon Route 53** được sử dụng để quản lý tên miền và routing đến frontend/backend.
* **GitHub Actions** tự động hóa quy trình kiểm thử và triển khai ngay khi có thay đổi mã nguồn.

Dự án phản ánh một quy trình DevOps chuẩn, kết hợp triển khai tự động, tích hợp dịch vụ AWS, phù hợp với môi trường thực tế trong doanh nghiệp.


![ConnectPrivate](/images/arc1.png) 

### Nội dung

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-Prerequiste/)
 3. [Kết nối máy chủ EC2 voớ MongDB Atlas](3-conect-mongdb/)
 4. [GitHub CI/Cd](4-cofigure-cicd/)
 5. [Port Forwarding](5-Portfwd/)
 6. [Dọn dẹp tài nguyên](6-cleanup/)
