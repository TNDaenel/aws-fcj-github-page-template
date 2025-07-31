---
title : "Session Management"
date: 2025-07-29
 
weight : 1 
chapter : false
---
# Deploy e-commerce stack on EC2 + S3 + MongoDB

### Overall
  This project aims to deploy a fullstack e-commerce system using ReactJS (frontend), NodeJS/Express (backend), and MongoDB (database) on the AWS cloud infrastructure. The deployment process follows a CI/CD pipeline powered by GitHub Actions, ensuring smooth, automated, and controlled build–test–deploy cycles.

The deployment architecture includes:

 - Frontend (ReactJS) is built and hosted on Amazon S3 as a static website.
 - Backend (NodeJS/Express) is deployed on an Amazon EC2 instance, handling API services and communication with the database.
 - MongoDB is hosted either on an EC2 instance or using MongoDB Atlas (cloud-managed).
 - Amazon Route 53 is used for domain management and routing requests to the frontend/backend.
 - GitHub Actions automates testing and deployment whenever code changes are pushed to the repository.
 - This project demonstrates a standard DevOps workflow, integrating automated deployment and AWS services — suitable for real-world business applications.

![ConnectPrivate](images/arc1.png) 

### Content
 1. [Introduction ](1-introduce/)
 2. [Preparation](2-prerequiste/)
 3. [Connect to EC2 instance](3-accessibilitytoinstances/)
 4. [Manage session logs](4-s3log/)
 5. [Port Forwarding](5-Portfwd/)
 6. [Clean up resources](6-cleanup/)
