---
title : "Triển khai CI/CD Backend Node.js lên AWS EC2"
date: 2025-07-30

weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

##  Cấu trúc thư mục backend

Đảm bảo thư mục Node.js backend của bạn như sau:

```

free007-backend-ban-hang/
├── src/
├── .env
├── package.json
├── ecosystem.config.js  # nếu dùng PM2
├── server.js / app.js

```

---

## Thiết lập SSH Key và Secrets GitHub

### Bước 1: Tạo SSH Key dùng riêng cho CI/CD

Trên máy của bạn:

```bash
ssh-keygen -t rsa -b 4096 -C "github-actions-ci" -f ./github-actions-ci
````

Sau khi tạo sẽ có:

* `github-actions-ci` (PRIVATE KEY)
* `github-actions-ci.pub` (PUBLIC KEY)

### Bước 2: Copy `github-actions-ci.pub` lên EC2

```bash
cat github-actions-ci.pub
```

Trên EC2, mở file `~/.ssh/authorized_keys` và dán nội dung trên vào.

### Bước 3: Tạo GitHub Secrets trong repo `free007-backend-ban-hang`

Vào **Settings > Secrets and variables > Actions**, tạo các secrets:

```
- `EC2_HOST`           = IP public EC2
- `EC2_USERNAME`       = ubuntu (hoặc ec2-user tùy hệ AMI)
- `EC2_SSH_PRIVATE_KEY` = nội dung file `github-actions-ci` (private key)
- `APP_DIR`            = thư mục chứa project backend trên EC2, ví dụ: /home/ubuntu/backend
```

---

## Cấu hình file workflow `.github/workflows/deploy.yml`

```yaml
name: Deploy Node.js Backend to EC2

on:
  push:
    branches:
      - main

jobs:
  deploy:
    name: Deploy to EC2
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup SSH
        uses: webfactory/ssh-agent@v0.7.0
        with:
          ssh-private-key: ${{ secrets.EC2_SSH_PRIVATE_KEY }}

      - name: Deploy code to EC2
        run: |
          ssh -o StrictHostKeyChecking=no ${{ secrets.EC2_USERNAME }}@${{ secrets.EC2_HOST }} << 'EOF'
            cd ${{ secrets.APP_DIR }}
            git pull origin main
            npm install
            pm2 restart ecosystem.config.js || pm2 start ecosystem.config.js
          EOF
```

---

## Cài đặt ban đầu trên EC2 (chỉ thực hiện 1 lần)

Trên EC2:

```bash
# Cài Git, Node.js, PM2
sudo apt update && sudo apt install -y git
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
sudo npm install -g pm2

# Clone repo lần đầu
git clone https://github.com/your-username/free007-backend-ban-hang.git
cd free007-backend-ban-hang
npm install

# Tạo file ecosystem.config.js nếu chưa có
pm2 start app.js --name backend-app
pm2 save
```

