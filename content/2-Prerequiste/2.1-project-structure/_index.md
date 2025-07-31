---
title : "Prepare the Source Code and Project Structure"
date: 2025-07-29

weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

In this step, we need to prepare the **frontend source code (ReactJS)**, **backend (NodeJS)**, and connect to **MongoDB**. Additionally, it’s important to ensure a clean project structure to support deployment and CI/CD configuration.

After completing this step, your project structure should look like this:

```
project-root/
├── free007-fe-customer-ban-hang/    # Frontend for customer users
├── free007-fe-admin/                # Frontend for administrators
├── free007-backend-ban-hang/        # Backend API built with NodeJS + Express
├── .github/workflows/               # CI/CD configuration for GitHub Actions
```

To better understand how to organize your source code, refer to the following official guides:

* [ReactJS Project Structure](https://reactjs.org/docs/faq-structure.html)
* [NodeJS Express Project Structure](https://expressjs.com/en/starter/structure.html)


### Contents

* [Clone or Create ReactJS Projects (Customer/Admin)](2.1.1-setup-react/)
* [Create Backend using NodeJS and Express](2.1.2-setup-backend/)

