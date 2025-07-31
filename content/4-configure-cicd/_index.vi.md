---
title : "GitHub CI/CD"
date: 2025-07-29

weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Trong phần này, bạn sẽ học cách triển khai CI/CD từ GitHub Actions để **deploy toàn bộ hệ thống web** gồm:

- ✅ Frontend Admin (`free007-fe-admin`)
- ✅ Frontend Customer (`free007-fe-customer-ban-hang`)
- ✅ Backend Node.js (`free007-backend-ban-hang`) kết nối MongoDB Atlas, triển khai trên EC2

![CI/CD Diagram](/images/4.s3/001-s3.png)

CI/CD giúp tự động hóa toàn bộ quy trình build – test – deploy mỗi khi code được cập nhật lên GitHub, đảm bảo triển khai nhanh chóng và đồng bộ.

---

### Nội dung hướng dẫn CI/CD:

* [Triển khai **CI/CD ReactJS Admin lên S3**](./4.1-deploy-fe-admin/)
* [Triển khai **CI/CD ReactJS Customer lên S3**](./4.2-deploy-fe-customer/)
* [Triển khai **CI/CD Node.js Backend lên EC2**](./4.3-deploy-backend/)



