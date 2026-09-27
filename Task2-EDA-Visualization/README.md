
# Task 2 — Exploratory Data Analysis & Visualization

## 📌 Overview

This project focuses on performing **Exploratory Data Analysis (EDA)** and visualization on the cleaned **Online Retail Transaction Dataset**.

The objective was to identify important patterns, trends, distributions, relationships, and business insights using **Python, Pandas, Matplotlib, and Seaborn**.

This task builds directly on **Task 1 — Data Acquisition, Cleaning & Preprocessing**, where the raw dataset was cleaned and transformed before being used for analysis.

---

## 🎯 Objectives

The main objectives of this task were to:

- Understand the structure and statistical characteristics of the dataset.
- Analyze transaction trends over time.
- Identify countries generating the highest transaction revenue.
- Identify top-performing products by quantity and revenue.
- Analyze customers based on their transaction value.
- Study customer purchase frequency.
- Examine the relationship between unit price and quantity sold.
- Analyze correlations between numerical variables.
- Identify important patterns, anomalies, and limitations.
- Communicate findings through clear and meaningful visualizations.

---

## 📊 Dataset

The project uses the **Online Retail Transaction Dataset**.

### Dataset Information

| Metric | Value |
|---|---:|
| Original Records | 541,909 |
| Cleaned Records | 392,692 |
| Columns after preprocessing | 13 |
| Customers | 4,338 |
| Invoices | 18,532 |
| Products | 3,665 |
| Countries | 37 |
| Total Quantity Sold | 5,152,002 |
| Transaction Revenue | £8,887,208.89 |
| Date Range | Dec 2010 – Dec 2011 |

The dataset contains retail transaction information such as:

- Invoice Number
- Stock Code
- Product Description
- Quantity
- Invoice Date
- Unit Price
- Customer ID
- Country

Additional analytical features were created during preprocessing:

- `TotalAmount`
- `Year`
- `Month`
- `Day`
- `Hour`

---

## 🛠️ Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook / Google Colab**

---

## 🔄 Data Preparation

The cleaned dataset generated during Task 1 was used as the starting point for EDA.

The preprocessing included:

- Removing duplicate records.
- Removing records with missing required values.
- Removing cancellation transactions.
- Removing non-positive quantities.
- Removing non-positive unit prices.
- Converting `InvoiceDate` to datetime.
- Converting `CustomerID` to integer.
- Creating `TotalAmount`.

### Total Amount Calculation

```python
clean_df["TotalAmount"] = (
    clean_df["Quantity"] * clean_df["UnitPrice"]
)
