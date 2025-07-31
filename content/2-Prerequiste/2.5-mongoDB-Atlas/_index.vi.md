---
title : "Kết nối MongoDB Atlas"
date: 2025-07-29

weight : 5 
chapter : false
pre : " <b> 2.5 </b> "
---


### Tạo MongoDB Atlas Cluster

1. Truy cập trang [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
![mongodb](/images/2.prerequisite/Db1.png)
2. Đăng nhập hoặc đăng ký tài khoản MongoDB Atlas
![mongodb](/images/2.prerequisite/Db2.png)
3. Tại dashboard, nhấn **Build a Database**

4. Trong mục **Cloud Provider & Region**, chọn:
   - **Provider**: AWS
   - **Region**: Singapore (ap-southeast-1) hoặc theo region EC2 của bạn

5. Nhấn **Create Deployment**
![mongodb](/images/2.prerequisite/Db3.png)


###  Tạo Database và Collections

1. Truy cập cluster vừa tạo trong MongoDB Atlas
2. Chọn tab **Browse Collections**
3. Nhấn **Add My Own Data**
![mongodb](/images/2.prerequisite/Db4.png)

4. Nhập:
   - **Database name**: e.g. `ecommerce`
   - **Collection name**: e.g. `users`
5. Nhấn **Create**
![mongodb](/images/2.prerequisite/Db5.png)


### Tạo người dùng MongoDB

1. Vào tab **Database Access**
2. Nhấn **Add New Database User**


3. Nhập thông tin:
   - **Username**: e.g. `admin`
   - **Password**: e.g. `admin123`
   - **Database User Privileges**: chọn **Read and write to any database**

4. Nhấn **Add User**
![mongodb](/images/2.prerequisite/Db6.png)

Lưu lại thông tin user để sử dụng khi cấu hình backend.


### Thêm địa chỉ IP EC2 vào whitelist

1. Vào tab **Network Access**
2. Nhấn **Add IP Address**

3. Trong cửa sổ Add IP Address:
   - Nhập **Public IP của EC2** 

4. Nhấn **Confirm**
![mongodb](/images/2.prerequisite/Db7.png)


Sau khi hoàn tất các bước trên, bạn đã có thể kết nối từ backend NodeJS (chạy trên EC2) đến MongoDB Atlas bằng connection string cung cấp trong tab **Connect > Drivers > Node.js** của MongoDB.
![mongodb](/images/2.prerequisite/Db8.png)

```bash
mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<dbname>?retryWrites=true&w=majority
````
