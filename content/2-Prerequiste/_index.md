---
title : "Preparation "
date: 2025-07-29

weight : 2
chapter : false
pre : " <b> 2.4 </b> "
---


{{% notice info %}}
You need to prepare the source code for your web system (ReactJS + NodeJS + MongoDB) along with necessary AWS resources to deploy this project.
{{% /notice %}}

To deploy the fullstack e-commerce system on AWS, you should have:

* Source code for the frontend (ReactJS) and backend (NodeJS/Express)
* CI/CD configuration using GitHub Actions
* AWS services ready: EC2, S3, IAM, Route 53
* *(Optional)* MongoDB Atlas if you don't want to host MongoDB on EC2

You can refer to the following lab guides to help you set up the required resources:

* [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)
* [Working with Amazon S3 and Route 53](https://000005.awsstudygroup.com/vi/)
* [Implementing CI/CD with GitHub Actions](https://000006.awsstudygroup.com/vi/)

To allow your CI/CD pipeline and instances to operate securely and effectively, you need to create an **IAM Role/User** with proper permissions to access EC2, S3, and other AWS services.


### Content

* [Prepare project source and structure](2.1-project-structure/)
* [Create S3 Bucket for frontend hosting](2.2-create-s3/)
* [Launch EC2 Instance to host backend](2.3-create-ec2/)
* [Create IAM Role for deployment permission](2.4-create-iam/)
* [Create MongDB Atlas](2.5-mongDB-Atlas/)



