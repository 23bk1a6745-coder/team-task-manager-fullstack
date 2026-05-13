# team-task-manager-fullstack
mkdir backend
cd backend
npm init -y
npm install express mongoose bcryptjs jsonwebtoken cors dotenv express-validator
npm install -D nodemon
backend/
 ├── controllers/
 ├── middleware/
 ├── models/
 ├── routes/
 ├── config/
 ├── .env
 ├── server.js
 └── package.json
 const express = require("express");
const mongoose = require("mongoose");
const cors = require("cors");
require("dotenv").config();

const app = express();

app.use(cors());
app.use(express.json());

mongoose.connect(process.env.MONGO_URI)
.then(() => console.log("MongoDB Connected"))
.catch((err) => console.log(err));

app.get("/", (req, res) => {
  res.send("API Running");
});

const PORT = process.env.PORT || 5000;

app.listen(PORT, () => {
  console.log(`Server running on ${PORT}`);
});
