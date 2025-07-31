---
title : "Node.js Backend Setup Guide"
date: 2025-07-29

weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---


### 1. Initialize a New Node.js Project

Open **Terminal** or **Visual Studio Code**, then run:

```bash
mkdir free007-backend-ban-hang
cd free007-backend-ban-hang
npm init -y
```


### 2. Install Required Dependencies

Install the necessary libraries for building a basic REST API:

```bash
npm install express mongoose dotenv cors
npm install --save-dev nodemon
```

### 3. Create the Initial Project Structure

```
free007-backend-ban-hang/
├── node_modules/
├── src/
│   ├── Schemas/
│   ├── controllers/
│   ├── middlewares/
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── app.js
├── .env
├── .gitignore
├── package.json
└── README.md
```
![ReactJS](/images/2.prerequisite/BE.png)

### 4. Create the `.env` File

```env
PORT = 8080
API_DB = 
SECRET_CODE = 
EMAIL_USERNAME = 
EMAIL_PASSWORD = 
VNP_HASHSECRET = 
VNP_URL=
VNP_TMNCODE = 
```


###  5. Create the Entry File: `src/index.js`

Add the following basic backend server code:

```js
const express = require('express');
const mongoose = require('mongoose');
const dotenv = require('dotenv');
const cors = require('cors');

dotenv.config();
const app = express();
const PORT = process.env.PORT || 5000;

// Middleware
app.use(cors());
app.use(express.json());

// Connect to MongoDB
mongoose.connect(process.env.MONGODB_URI)
  .then(() => console.log('Connected to MongoDB'))
  .catch((err) => console.error('MongoDB connection error:', err));

// Routes
app.get('/', (req, res) => {
  res.send('API is running...');
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```


### 6. Update `package.json` Scripts

Enable automatic reloading with `nodemon`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```


### 7. Run the Backend Server

Start the development server with:

```bash
npm run dev
```

If everything is configured correctly, you should see:

```
Connected to MongoDB
Server is running on port 5000
```



