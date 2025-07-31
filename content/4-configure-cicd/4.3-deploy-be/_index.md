---
title : "Deploy Node.js Backend to AWS EC2 via CI/CD"
date: 2025-07-30

weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

##  Backend Project Structure

Make sure your Node.js backend project has the following structure:

```

free007-backend-ban-hang/
├── src/
├── .env
├── package.json
├── ecosystem.config.js  # if using PM2
├── server.js / app.js

```

---

##  Setup SSH Key and GitHub Secrets

### Step 1: Generate a dedicated SSH key for CI/CD

On your local machine, run:

```bash
ssh-keygen -t rsa -b 4096 -C "github-actions-ci" -f ./github-actions-ci
```

This will generate:

* `github-actions-ci` (PRIVATE KEY)
* `github-actions-ci.pub` (PUBLIC KEY)

### Step 2: Add the public key to your EC2 instance

```bash
cat github-actions-ci.pub
```

Copy the content and paste it into the `~/.ssh/authorized_keys` file on your EC2 instance.

### Step 3: Add GitHub Secrets in `free007-backend-ban-hang` repo

Go to **Settings > Secrets and variables > Actions**, and add the following secrets:

```
- `EC2_HOST`            = Your EC2 public IP address
- `EC2_USERNAME`        = ubuntu (or ec2-user depending on your AMI)
- `EC2_SSH_PRIVATE_KEY` = Content of the `github-actions-ci` private key
- `APP_DIR`             = Absolute path to your backend project on EC2 (e.g., /home/ubuntu/backend)
```

---

## GitHub Actions Workflow File `.github/workflows/deploy.yml`

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

## – Initial Setup on EC2 (run once only)

On your EC2 instance:

```bash
# Install Git, Node.js, and PM2
sudo apt update && sudo apt install -y git
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
sudo npm install -g pm2

# Clone your backend repo for the first time
git clone https://github.com/your-username/free007-backend-ban-hang.git
cd free007-backend-ban-hang
npm install

# Create ecosystem.config.js if not already present
pm2 start app.js --name backend-app
pm2 save
```
