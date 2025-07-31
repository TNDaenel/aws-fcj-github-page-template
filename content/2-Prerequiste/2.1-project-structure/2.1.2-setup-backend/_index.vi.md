---
title : "Thiết Lập Node.js Backend"
date: 2025-07-29
 
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---


1. Mở Terminal hoặc Visual Studio Code. Tạo thư mục backend mới và khởi tạo project NodeJS:

```bash
mkdir free007-backend-ban-hang
cd free007-backend-ban-hang
npm init -y
```


2. Cài đặt các thư viện cần thiết cho một REST API cơ bản:

```bash
npm install express mongoose dotenv cors
npm install --save-dev nodemon
```

3. Tạo cấu trúc thư mục ban đầu như sau:

```
free007-backend-ban-hang/
├── node_modules/
├── src/
│   ├── Schemas/
│   ├── controllers/
│   ├── middlewares/
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── app.js
├── .env
├── .gitignore
├── package.json
└── README.md
```
![ReactJS](/images/2.prerequisite/BE.png)

4. Tạo file **`.env`** chứa cấu hình MongoDB (sẽ kết nối sau):

```env
PORT = 8080
API_DB = 
SECRET_CODE = 
EMAIL_USERNAME = 
EMAIL_PASSWORD = 
VNP_HASHSECRET = 
VNP_URL=
VNP_TMNCODE = 
```

5. Mở file `src/index.js` và viết nội dung cơ bản:

```js
const express = require('express');
const mongoose = require('mongoose');
const dotenv = require('dotenv');
const cors = require('cors');

dotenv.config();
const app = express();
const PORT = process.env.PORT || 5000;

// Middleware
app.use(cors());
app.use(express.json());

// Connect DB
mongoose.connect(process.env.MONGODB_URI)
  .then(() => console.log('Connected to MongoDB'))
  .catch((err) => console.error('MongoDB connection error:', err));

// Routes
app.get('/', (req, res) => {
  res.send('API is running...');
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

6. Cập nhật file **`package.json`** để hỗ trợ chạy bằng `nodemon`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```

7. Chạy thử backend bằng lệnh:

```bash
npm run dev
```

Bạn sẽ thấy thông báo:

```
Connected to MongoDB
Server is running on port 5000
```


