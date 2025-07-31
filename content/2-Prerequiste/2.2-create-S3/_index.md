---
title : "Create S3 Bucket"
date: 2025-07-29
 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### Create an S3 Bucket

In this step, we will **create an S3 Bucket** to store the static files of our frontend (ReactJS) application. We will then enable **Static Website Hosting** and configure a **Bucket Policy** to allow public access from browsers.

1. Go to the [S3 service console](https://s3.console.aws.amazon.com/s3/).
2. Click **Create bucket**.

![s3-create-bucket](/images/2.prerequisite/S3.png)

3. Configure the fields as follows:

   * **Bucket name**: `webbanhang`
   * **Region**: choose your preferred region, e.g., `ap-southeast-1` (Singapore)
   * Uncheck **Block all public access**

![s3-config](/images/2.prerequisite/S3-1.png)

![s3-config](/images/2.prerequisite/S3-2.png)

4. Scroll down and click **Create bucket**.

![s3-config](/images/2.prerequisite/S3-3.png)

---

### Configure Bucket Policy for Public Access

1. Go to the newly created bucket → **Permissions** tab → click **Bucket policy**.

![s3-config](/images/2.prerequisite/S3-4.png)

2. Paste the following JSON into the policy editor:

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
````

![s3-policy](/images/2.prerequisite/S3-6.png)

---

### Enable Static Website Hosting

1. Go to the **Properties** tab of your bucket.

![s3-policy](/images/2.prerequisite/S3-7.png)

2. Scroll down to **Static website hosting** → click **Edit**.

3. ![s3-hosting](/images/2.prerequisite/S3-8.png)

4. Select **Enable** and fill in:

   * **Index document**: `index.html`
   * **Error document**: `index.html`

5. Click **Save changes**.

![s3-hosting](/images/2.prerequisite/S3-9.png)

---

After completing these steps, your bucket will be able to serve your static ReactJS website. The default URL will look like:

```
http://webbanhangg.s3-website-ap-southeast-1.amazonaws.com
```

