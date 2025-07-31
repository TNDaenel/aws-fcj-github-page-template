---
title : "Chuẩn bị mã nguồn và cấu trúc dự án"
date: 2025-07-29
 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---


Trong bước này, chúng ta sẽ cần chuẩn bị **mã nguồn frontend (ReactJS)**, **backend (NodeJS)** và kết nối với **MongoDB**. Đồng thời, cần đảm bảo cấu trúc thư mục rõ ràng để phục vụ cho quá trình triển khai và cấu hình CI/CD.

Tổng quan cấu trúc dự án của bạn sau khi hoàn tất bước chuẩn bị sẽ như sau:

```
project-root/
├── free007-fe-customer-ban-hang/    # Frontend dành cho khách hàng
├── free007-fe-admin/                # Frontend dành cho quản trị viên
├── free007-backend-ban-hang/       # Backend API với NodeJS + Express
├── .github/workflows/              # Thư mục cấu hình CI/CD GitHub Actions
```

Để hiểu rõ cách tổ chức và chuẩn bị mã nguồn, bạn có thể tham khảo các link mẫu:

* [Tổ chức project ReactJS](https://reactjs.org/docs/faq-structure.html)
* [Tổ chức project NodeJS](https://expressjs.com/en/starter/structure.html)



### Nội dung

* [Setup mã nguồn ReactJS Frontend](2.1.1-setup-react/)
* [Tạo backend NodeJS với Express](2.1.2-setup-backend/)


