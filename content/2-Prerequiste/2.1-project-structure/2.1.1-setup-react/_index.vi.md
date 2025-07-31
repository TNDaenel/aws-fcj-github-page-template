---
title : "Thiết lập mã nguồn ReactJS Frontend"
date: 2025-07-30
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---


#### 1. Kiểm tra mã nguồn ReactJS

1. Truy cập thư mục frontend dự án của bạn:

```bash
cd free007-fe-customer-ban-hang
```
```bash
cd free007-fe-admin
```

2. Đảm bảo tồn tại các file sau:


```bash
free007-fe-customer-ban-hang/
├── public/
├── src/
├── package.json
├── .gitignore
└── README.md
```

![ReactJS](/images/2.prerequisite/FE-customer.png)



```bash
free007-fe-admin
├── public/
├── src/
├── package.json
├── .gitignore
└── README.md
```



![ReactJS](/images/2.prerequisite/FE-admin.png)

3. Cài đặt các dependencies:

```bash
npm install
```

#### 2. Build dự án ReactJS

1. Thực hiện build:

```bash
npm run build
```

2. Sau khi build, một thư mục `/build` sẽ được tạo ra, chứa mã tĩnh:

```bash
free007-fe-customer-ban-hang/
└── build/
    ├── index.html
    ├── static/
    ├── ...
```

```bash
free007-fe-admin
└── build/
    ├── index.html
    ├── static/
    ├── ...
```

Đây là thư mục sẽ **deploy lên AWS S3** hoặc qua CI/CD pipeline.


#### 3. Tạo `.gitignore`

Tạo file `.gitignore` nếu chưa có, nội dung mẫu:

```
node_modules/
build/
.env
.DS_Store
```

---

#### 4. Đẩy mã nguồn lên GitHub

1. Khởi tạo Git repo:

```bash
git init
git add .
git commit -m "fe-customer vs fe-admin"
```

2. Tạo repository trên GitHub, ví dụ:

```
https://github.com/TNDaenel/web-King-Foot-Mart

```

3. Thêm remote và push:

```bash
git remote add origin https://github.com/TNDaenel/web-King-Foot-Mart
git branch -M main
git push -u origin main
```

