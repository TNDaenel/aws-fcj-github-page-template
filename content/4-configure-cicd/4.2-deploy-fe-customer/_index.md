---
title : "Deploy React Customer Frontend to AWS S3 via CI/CD"
date: 2025-07-30

weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

## Project Structure

Make sure your customer-facing ReactJS frontend project has the following structure:

```

free007-fe-customer-ban-hang/
├── public/
├── src/
├── package.json
├── .gitignore

```

### Configure GitHub Secrets

Go to the `free007-fe-customer-ban-hang` repository > **Settings** > **Secrets and variables > Actions**, and create the following secrets:

```

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`
* `AWS_REGION` – e.g., `ap-southeast-1`
* `S3_BUCKET_NAME` – the S3 bucket name for the customer frontend

```

![git](/images/4.deploy/git1.png)  
![git](/images/4.deploy/git2.png)

## Create GitHub Actions Workflow File

In your `free007-fe-customer-ban-hang` repo, create the file: `.github/workflows/deploy.yml`

```yaml
name: Deploy React Customer to S3

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

