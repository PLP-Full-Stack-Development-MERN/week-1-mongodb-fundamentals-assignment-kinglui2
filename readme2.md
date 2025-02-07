# 📘 MongoDB Assignment Documentation

## 📖 Introduction
This document provides step-by-step instructions for setting up, configuring, and running a MongoDB database. It will guide you through installing MongoDB, creating a database, performing CRUD operations, implementing indexing, and utilizing aggregation queries. By following these instructions, you will gain hands-on experience with MongoDB's powerful database management features.

---

## 🛠 Setting Up MongoDB

### 1️⃣ **Install MongoDB**
- Download MongoDB from the [official MongoDB website](https://www.mongodb.com/try/download/community).
- Follow the installation steps for your operating system.
- Ensure MongoDB is added to your system **PATH** to access it via the terminal.

### 2️⃣ **Start MongoDB Server**
To start MongoDB locally, run:
```sh
mongod
```
For MongoDB Atlas, create a free cluster and connect via:
```sh
mongosh "your-cluster-url"
```

### 3️⃣ **Verify Installation**
Run the following command to check if MongoDB is installed correctly:
```sh
mongosh --version
```
If successful, the version number will be displayed.

---

## 📂 Creating and Managing the Database

### 1️⃣ **Create a New Database**
```javascript
use library
```

### 2️⃣ **Create a Collection**
```javascript
db.createCollection("books")
```

### 3️⃣ **Insert Data into the Collection**
```javascript
db.books.insertMany([
   { title: "The Great Gatsby", author: "F. Scott Fitzgerald", publishedYear: 1925, genre: "Classic", ISBN: "9780743273565" },
   { title: "To Kill a Mockingbird", author: "Harper Lee", publishedYear: 1960, genre: "Fiction", ISBN: "9780061120084" }
])
```

---

## 🔍 Retrieving Data

### **Retrieve All Books**
```javascript
db.books.find().pretty()
```

### **Query Books by Author**
```javascript
db.books.find({ author: "Harper Lee" }).pretty()
```

---

## ✏️ Updating Data

### **Update a Book's Published Year**
```javascript
db.books.updateOne(
   { title: "The Great Gatsby" },
   { $set: { publishedYear: 1930 } }
)
```

### **Add a `rating` Field to All Books**
```javascript
db.books.updateMany({}, { $set: { rating: 5 } })
```

---

## 🗑️ Deleting Data

### **Delete a Book by ISBN**
```javascript
db.books.deleteOne({ ISBN: "9780743273565" })
```

### **Remove All Books of a Specific Genre**
```javascript
db.books.deleteMany({ genre: "Classic" })
```

---

## 📊 Aggregation Queries

### **Count Books by Genre**
```javascript
db.books.aggregate([
   { $group: { _id: "$genre", count: { $sum: 1 } } }
])
```

### **Average Published Year of Books**
```javascript
db.books.aggregate([
   { $group: { _id: null, avgPublishedYear: { $avg: "$publishedYear" } } }
])
```

---

## ⚡ Indexing for Performance Optimization

### **Create an Index on Author Field**
```javascript
db.books.createIndex({ author: 1 })
```

### **Why Use Indexing?**
- Improves query speed.
- Enhances performance when dealing with large datasets.

---

## 🔎 Testing Your Database
- Use `mongosh` or **MongoDB Compass** to verify data.
- Run all queries to check expected results.

---

## 📜 Submission Steps

### 1️⃣ **Push Code to GitHub**
```sh
git init
git add .
git commit -m "MongoDB Assignment"
git branch -M main
git remote add origin <your-github-repo-link>
git push -u origin main
```

### 2️⃣ **Include This README.md in Your Repository**
Ensure your repository contains:
✅ **All MongoDB queries**
✅ **README.md file with setup & instructions**
✅ **Data models for the assignment**

---

🎉 **Congratulations! Your MongoDB setup is complete!** 🚀
