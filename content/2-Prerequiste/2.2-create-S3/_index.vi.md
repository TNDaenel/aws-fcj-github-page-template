---
title : "Tạo S3 Bucket"
date: 2025-07-29
 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---


### Tạo S3 Bucket 

Trong bước này, chúng ta sẽ tiến hành **tạo một S3 Bucket** để chứa mã nguồn tĩnh (static files) của ứng dụng frontend (ReactJS). Sau đó bật tính năng **Static Website Hosting**, cấu hình **Bucket Policy** để cho phép truy cập công khai từ trình duyệt.

1. Truy cập vào [giao diện quản trị dịch vụ S3](https://s3.console.aws.amazon.com/s3/).
2. Click **Create bucket**.

![s3-create-bucket](/images/2.prerequisite/S3.png)
1. Cấu hình các trường như sau:

   * **Bucket name**: `webbanhang` 
   * **Region**: chọn khu vực như `ap-southeast-1` (Singapore)
   * Bỏ chọn **Block all public access**

![s3-config](/images/2.prerequisite/S3-1.png)

![s3-config](/images/2.prerequisite/S3-2.png)

1. Kéo xuống cuối và click **Create bucket**.

![s3-config](/images/2.prerequisite/S3-3.png)

### Cấu hình Bucket Policy cho public access

1. Truy cập bucket vừa tạo → Tab **Permissions** → click **Bucket policy**.
   
![s3-config](/images/2.prerequisite/S3-4.png)   

2. Thêm đoạn cấu hình sau vào ô policy editor:

![s3-config](/images/2.prerequisite/S3-5.png)
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::webbanhangg/*"
    }
  ]
}
```

![s3-policy](/images/2.prerequisite/S3-6.png)


### Bật Static Website Hosting

1. Vào Tab **Properties** của bucket.
   
![s3-policy](/images/2.prerequisite/S3-7.png)

2. Kéo xuống mục **Static website hosting** → click **Edit**.
3. ![s3-hosting](/images/2.prerequisite/S3-8.png)
4. Chọn **Enable** và điền:

   * **Index document**: `index.html`
   * **Error document**: `index.html` 

5. Click **Save changes**.

![s3-hosting](/images/2.prerequisite/S3-9.png)

Sau khi hoàn tất, bucket của bạn sẽ có thể hoạt động như một website ReactJS tĩnh. URL mặc định có dạng:

```
http://webbanhangg.s3-website-ap-southeast-1.amazonaws.com
```

