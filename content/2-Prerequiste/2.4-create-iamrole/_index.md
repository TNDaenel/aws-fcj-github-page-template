---
title : "Create IAM Role"
date: 2025-07-29

weight : 4 
chapter : false
pre : " <b> 2.4 </b> "
---

### Create IAM Role

1. Go to [IAM Console - Roles](https://console.aws.amazon.com/iam/home#/roles)  
   ![role](/images/2.prerequisite/role1.png)

2. Click **Create role**

3. Under **Trusted entity type**, select `AWS service`

4. In the **Use case** section, choose `EC2`

5. Click **Next**  
   ![role](/images/2.prerequisite/role2.png)

#### Attach permissions policy

At the **Add permissions** step, choose one of the following:

- Select `AmazonS3FullAccess` if you want the EC2 instance to have full access to all S3 buckets

Then click **Next**  
![role](/images/2.prerequisite/role3.png)

#### Name and create the role

1. Set role name: `ec2-s3-access-role`

2. Click **Create role**  
   ![role](/images/2.prerequisite/role4.png)


#### Attach IAM Role to EC2 instance

1. Go to the EC2 Console

2. Select the EC2 instance running your backend

3. Click **Actions → Security → Modify IAM Role**  
   ![role](/images/2.prerequisite/role5.png)

4. Choose the role you just created: `ec2-s3-access-role`

5. Click **Update IAM Role**  
   ![role](/images/2.prerequisite/role6.png)


#### Verify IAM Role  
You should now see the attached role on the instance details tab.  
![role](/images/2.prerequisite/role7.png)
