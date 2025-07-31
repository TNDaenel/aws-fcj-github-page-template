---
title : "Các bước chuẩn bị"
date: 2025-07-29
 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
Bạn cần chuẩn bị sẵn mã nguồn của hệ thống web (ReactJS + NodeJS + MongoDB) cùng với các tài nguyên AWS để triển khai dự án này.
{{% /notice %}}

Để triển khai hệ thống thương mại điện tử fullstack trên AWS, bạn cần chuẩn bị sẵn:

* Mã nguồn frontend (ReactJS) và backend (NodeJS/Express)
* Cấu hình môi trường CI/CD với GitHub Actions
* Các dịch vụ AWS: EC2, S3, IAM, Route 53
* (Tuỳ chọn) MongoDB Atlas nếu không muốn host MongoDB trên EC2

Bạn có thể tham khảo thêm cách tạo các tài nguyên cần thiết qua các bài lab:

* [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
* [Làm việc với Amazon S3 và Route 53](https://000005.awsstudygroup.com/vi/)
* [Triển khai CI/CD với GitHub Actions](https://000006.awsstudygroup.com/vi/)

Để cho phép CI/CD pipeline và các instance hoạt động hiệu quả và bảo mật, bạn cần tạo một **IAM Role/User** có quyền cụ thể để truy cập EC2, S3 và các dịch vụ khác.


### Nội dung

* [Chuẩn bị mã nguồn và cấu trúc dự án](2.1-project-structure/)
* [Tạo S3 Bucket cho frontend](2.2-create-s3/)
* [Tạo EC2 Instance để host backend](2.3-create-ec2/)
* [Tạo IAM Role để cấp quyền deploy](2.4-create-iam/)
* [Tạo MongDB Atlas](2.5-mongDB-Atlas/)





  
