---
title : "Connect to MongoDB Atlas"
date: 2025-07-29

weight : 5 
chapter : false
pre : " <b> 2.5 </b> "
---

### Create a MongoDB Atlas Cluster

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)  
![mongodb](/images/2.prerequisite/Db1.png)

2. Log in or sign up for a MongoDB Atlas account  
![mongodb](/images/2.prerequisite/Db2.png)

3. On the dashboard, click **Build a Database**

4. In the **Cloud Provider & Region** section, select:
   - **Provider**: AWS  
   - **Region**: Singapore (ap-southeast-1) or your EC2's region

5. Click **Create Deployment**  
![mongodb](/images/2.prerequisite/Db3.png)


### Create Database and Collections

1. Access the cluster you just created in MongoDB Atlas
2. Go to the **Browse Collections** tab
3. Click **Add My Own Data**  
![mongodb](/images/2.prerequisite/Db4.png)

4. Fill in the following:
   - **Database name**: e.g. `ecommerce`  
   - **Collection name**: e.g. `users`

5. Click **Create**  
![mongodb](/images/2.prerequisite/Db5.png)


### Step 3 – Create a MongoDB Database User

1. Go to the **Database Access** tab
2. Click **Add New Database User**

3. Fill in the following:
   - **Username**: e.g. `admin`  
   - **Password**: e.g. `admin123`  
   - **Database User Privileges**: Select **Read and write to any database**

4. Click **Add User**  
![mongodb](/images/2.prerequisite/Db6.png)
**Note:** Save the username and password to use in your backend configuration.


### Whitelist Your EC2 IP Address

1. Go to the **Network Access** tab
2. Click **Add IP Address**

3. In the **Add IP Address** dialog:
   - Enter your EC2 **Public IP**

4. Click **Confirm**  
![mongodb](/images/2.prerequisite/Db7.png)

After completing the steps above, you're ready to connect your Node.js backend (running on EC2) to MongoDB Atlas using the connection string from the **Connect > Drivers > Node.js** tab.

![mongodb](/images/2.prerequisite/Db8.png)

```bash
mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<dbname>?retryWrites=true&w=majority
````

