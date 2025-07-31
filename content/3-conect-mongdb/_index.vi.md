---
title : "Kết nối EC2 với MongoDB Atlas"
date: 2025-07-30

weight : 3
chapter : false
pre : " <b> 3. </b> "
---

Sau khi đã tạo cluster MongoDB và thêm IP EC2 vào whitelist, bạn có thể bắt đầu kết nối Node.js backend trên EC2 với MongoDB Atlas.


## Lấy chuỗi kết nối MongoDB URI

1. Truy cập [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Mở Cluster của bạn > Click **Connect**
3. Chọn **Drivers** > **Node.js**
4. Copy URI kết nối ví dụ:

```bash
mongodb+srv://<username>:<password>@cluster0.mongodb.net/<dbname>?retryWrites=true&w=majority
````

![mongodb](/images/2.prerequisite/Db8.png)


### Cập nhật file cấu hình `.env` hoặc `config.js`

Trên EC2, vào thư mục Node.js project, bạn tạo hoặc chỉnh sửa file `.env`:

```env
PORT=8080
MONGODB_URI=mongodb+srv://admin:admin123@cluster0.mongodb.net/ecommerce?retryWrites=true&w=majority
```

---

## Kiểm tra kết nối từ EC2

1. SSH vào EC2 của bạn:

```bash
ssh -i "your-key.pem" ubuntu@<EC2_PUBLIC_IP>
```

2. Cài đặt thư viện MongoDB nếu cần:

```bash
npm install mongoose
```


