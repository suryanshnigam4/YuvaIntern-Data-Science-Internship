
# Task 1 – Data Acquisition, Cleaning & Preprocessing

## 📌 Objective

The objective of this task was to acquire a public dataset and perform data cleaning and preprocessing to prepare it for further analysis and machine learning applications.

## 📊 Dataset

**Dataset:** Online Retail Dataset

The dataset contains transaction-level information from an online retail business.

### Original Dataset
- Rows: 541,909
- Columns: 8

### Main Columns
- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

## 🛠️ Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

## 🔍 Work Performed

The following data preprocessing steps were performed:

1. Loaded and inspected the dataset.
2. Analyzed missing values.
3. Identified and removed duplicate records.
4. Checked invalid and non-positive quantities.
5. Checked invalid and non-positive unit prices.
6. Identified cancellation transactions.
7. Converted `InvoiceDate` into datetime format.
8. Investigated potential outliers using the IQR method.
9. Applied business rules to clean the dataset.
10. Validated the cleaned dataset.
11. Created additional features for further analysis.

## 🧹 Cleaning Rules

The final dataset was cleaned using the following rules:

- Removed duplicate rows.
- Removed records with missing `Description`.
- Removed records with missing `CustomerID`.
- Removed cancellation transactions.
- Removed transactions with `Quantity <= 0`.
- Removed transactions with `UnitPrice <= 0`.

Outliers were investigated using statistical methods, but valid high-value transactions were not blindly removed.

## ⚙️ Feature Engineering

The following features were created:

- `TotalAmount` = Quantity × UnitPrice
- `Year`
- `Month`
- `Day`
- `Hour`

## 📈 Final Dataset

After cleaning and preprocessing:

- **Rows:** 392,692
- **Columns:** 13
- **Unique Customers:** 4,338
- **Unique Invoices:** 18,532
- **Countries:** 37
- **Missing Values:** 0
- **Duplicate Rows:** 0

## 📁 Files

| File | Description |
|------|-------------|
| `Task_1_Data_Cleaning.ipynb` | Complete Python analysis and preprocessing workflow |
| `Internship_Task_1_Data_Cleaning_Preprocessing_Report.docx` | Detailed final report |

## 🎯 Outcome

The raw Online Retail dataset was successfully transformed into a clean and structured dataset suitable for exploratory data analysis and further data science tasks.

This cleaned dataset will also serve as the foundation for **Task 2 – Exploratory Data Analysis and Visualization**.

## 👨‍💻 Internship Task

**Program:** Data Science Internship  
**Task:** Week 1 – Data Acquisition, Cleaning & Preprocessing
