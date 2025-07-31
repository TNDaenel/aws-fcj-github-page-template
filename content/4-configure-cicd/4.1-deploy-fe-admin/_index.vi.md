---
title : "Triển khai CI/CD Frontend React lên AWS S3"
date: 2025-07-30

weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

## Cấu trúc thư mục

Đảm bảo frontend ReactJS của bạn có cấu trúc:

```
free007-fe-customer-ban-hang/
├── public/
├── src/
├── package.json
├── .gitignore
```

## Thiết lập Secrets trong GitHub

Vào repo frontend > **Settings** > **Secrets and variables > Actions**, tạo các biến:
```
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION` – ví dụ: `ap-southeast-1`
- `S3_BUCKET_NAME` – tên bucket S3 của bạn
```
![git](/images/4.deploy/git1.png)
![git](/images/4.deploy/git2.png)

## Tạo file workflow GitHub Actions

Trong repo `free007-fe-admin`, tạo file tại: `.github/workflows/deploy.yml`

```yaml
name: Deploy React Admin to S3

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Build React App
        run: npm run build

      - name: Deploy to S3
        uses: jakejarvis/s3-sync-action@master
        with:
          args: --delete
        env:
          AWS_S3_BUCKET: ${{ secrets.S3_BUCKET_NAME }}
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: ${{ secrets.AWS_REGION }}
          SOURCE_DIR: "build"
```
