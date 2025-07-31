---
title : "ReactJS Frontend Setup Guide"
date: 2025-07-30

weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---


#### 1. Verify ReactJS Project Structure

1. Navigate to your project's frontend folder:

```bash
cd free007-fe-admin
```
```bash
cd free007-fe-customer-ban-hang
```
2. Ensure the following files and folders exist:

```bash
free007-fe-customer-ban-hang/
├── public/
├── src/
├── package.json
├── .gitignore
└── README.md
```

![ReactJS](/images/2.prerequisite/FE-customer.png)



```bash
free007-fe-admin
├── public/
├── src/
├── package.json
├── .gitignore
└── README.md
```

![ReactJS](/images/2.prerequisite/FE-admin.png)

3. Install project dependencies:

```bash
npm install
```

#### 2. Build the ReactJS Project

1. Run the build command:

```bash
npm run build
```

2. After building, a `/build` folder will be created containing static assets:

```bash
free007-fe-customer-ban-hang/
└── build/
    ├── index.html
    ├── static/
    ├── ...
```
```bash
free007-fe-admin
└── build/
    ├── index.html
    ├── static/
    ├── ...
```

This `build` folder is what you will **deploy to AWS S3** or via a CI/CD pipeline.


 #### 3. Create `.gitignore`

Create a `.gitignore` file if it doesn’t already exist, with the following example content:

```
node_modules/
build/
.env
.DS_Store
```


#### 4. Push Source Code to GitHub

1. Initialize a Git repository:

```bash
git init
git add .
git commit -m "fe-customer vs fe-admin"
```

2. Create a repository on GitHub, for example:

```
https://github.com/TNDaenel/web-King-Foot-Mart

```

3. Add the remote and push the code:

```bash
git remote add origin https://github.com/TNDaenel/web-King-Foot-Mart.git
git branch -M main
git push -u origin main
```

