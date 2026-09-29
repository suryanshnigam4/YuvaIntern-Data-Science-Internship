
# Task 4 — Supervised Learning Model Implementation

## 📌 Project Title

**Customer Repeat-Purchase Prediction using Supervised Machine Learning**

## 🎯 Objective

The objective of this task is to design and implement a supervised machine learning model to predict whether a customer will make a repeat purchase in a future period.

The project uses the **Online Retail transaction dataset** and builds customer-level behavioral features from historical transaction data. Two classification algorithms are implemented and compared:

- Logistic Regression
- Random Forest Classifier

The models are evaluated using multiple classification metrics and cross-validation.

---

## 📊 Dataset

The project uses the **Online Retail dataset**, containing transaction records from a retail business.

### Original Dataset

- Rows: **541,909**
- Columns: **8**
- Customers: **4,338** after preprocessing
- Countries: **37**
- Products: **3,665**

### Original Features

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

The dataset was cleaned and prepared during the previous internship tasks.

---

## 🔄 Project Continuity

This task continues the analysis performed in the previous weeks:

```text
Task 1 → Data Cleaning & Preprocessing
          ↓
Task 2 → Exploratory Data Analysis & Visualization
          ↓
Task 3 → Customer Segmentation using RFM + K-Means
          ↓
Task 4 → Customer Repeat-Purchase Prediction
