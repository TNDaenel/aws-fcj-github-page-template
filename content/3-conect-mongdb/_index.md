---
title : "Connect EC2 with MongoDB Atlas"
date: 2025-07-30

weight : 4
chapter : false
pre : " <b> 4. </b> "
---

After creating your MongoDB Atlas cluster and whitelisting your EC2 IP address, you can now connect your Node.js backend running on EC2 to MongoDB Atlas.

## Get the MongoDB Connection URI

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Open your cluster > Click **Connect**
3. Select **Drivers** > **Node.js**
4. Copy the connection URI example:

```bash
mongodb+srv://<username>:<password>@cluster0.mongodb.net/<dbname>?retryWrites=true&w=majority
````

![mongodb](/images/2.prerequisite/Db8.png)

### Update the `.env` or `config.js` file

On your EC2 instance, go to your Node.js project directory and create or edit the `.env` file:

```env
PORT=8080
MONGODB_URI=mongodb+srv://admin:admin123@cluster0.mongodb.net/ecommerce?retryWrites=true&w=majority
```


## Test the connection from EC2

1. SSH into your EC2 instance:

```bash
ssh -i "your-key.pem" ubuntu@<EC2_PUBLIC_IP>
```

2. Install the MongoDB library if needed:

```bash
npm install mongoose
```

