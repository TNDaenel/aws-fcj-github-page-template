---
title : "Tạo IAM Role"
date: 2025-07-29
 
weight : 4 
chapter : false
pre : " <b> 2.4 </b> "
---


### Tạo IAM Role

1. Truy cập [IAM Console - Roles](https://console.aws.amazon.com/iam/home#/roles)
![role](/images/2.prerequisite/role1.png) 
2. Nhấn **Create role**
3. Trong mục **Trusted entity type**, chọn `AWS service`
4. Trong phần **Use case**, chọn `EC2`
5. Nhấn **Next**
![role](/images/2.prerequisite/role2.png) 
#### Gán quyền truy cập

Tại bước **Add permissions**, có thể chọn một trong hai cách sau:

- Chọn `AmazonS3FullAccess` nếu bạn muốn EC2 có toàn quyền với tất cả các bucket

Sau đó nhấn **Next**
![role](/images/2.prerequisite/role3.png) 
#### Đặt tên và tạo role

1. Đặt tên role: `ec2-s3-access-role`
2. Nhấn **Create role**
![role](/images/2.prerequisite/role4.png) 

#### Gán IAM Role vào EC2
1. Truy cập EC2 Console

2. Chọn EC2 instance đang chạy backend

3. Nhấn Actions → Security → Modify IAM Role
![role](/images/2.prerequisite/role5.png) 
4. Chọn role vừa tạo: ec2-s3-access-role

5. Nhấn Update IAM Role
![role](/images/2.prerequisite/role6.png)

#### Kiểm tra role
![role](/images/2.prerequisite/role7.png)
