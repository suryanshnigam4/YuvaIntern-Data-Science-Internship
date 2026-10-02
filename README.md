YuvaIntern Data Science Internship
End-to-End Data Science with Python

This repository contains the complete work completed during the YuvaIntern Data Science Internship, covering the full Data Science lifecycle from data acquisition and preprocessing to exploratory analysis, machine learning, deep learning, and an integrative capstone project.

The internship was structured across six tasks, with each task building upon the previous one. The Online Retail transaction dataset was used as the primary dataset throughout the project, allowing the individual tasks to form one continuous customer-analytics workflow.

🚀 Internship Project Journey
Task 1
Data Cleaning & Preprocessing
        ↓
Task 2
Exploratory Data Analysis
        ↓
Task 3
Customer Segmentation
        ↓
Task 4
Supervised Machine Learning
        ↓
Task 5
Deep Learning
        ↓
Task 6
Integrative Capstone

The overall project focuses on understanding customer purchasing behavior, identifying customer segments, predicting repeat purchases, and combining descriptive and predictive analytics into a complete Data Science solution.

🎯 Internship Objectives

The internship provided practical experience in:

Data acquisition and preprocessing
Data cleaning and validation
Exploratory Data Analysis (EDA)
Data visualization
Feature engineering
Unsupervised learning
Supervised learning
Deep learning
Model evaluation
Business-oriented interpretation
Technical documentation
End-to-end Data Science project development
📊 Dataset

The primary dataset used in the internship is the Online Retail transaction dataset.

Original dataset
Rows: 541,909
Columns: 8
Columns
InvoiceNo
StockCode
Description
Quantity
InvoiceDate
UnitPrice
CustomerID
Country

The dataset contains retail transactions with information about invoices, products, quantities, prices, customers and countries.

📁 Internship Tasks
Task 1 — Data Acquisition, Cleaning & Preprocessing
Objective

Clean and preprocess the raw Online Retail dataset so that it can be reliably used for further analysis and modeling.

Major activities
Loaded the raw dataset.
Inspected data types and structure.
Analyzed missing values.
Detected duplicate rows.
Identified invalid quantities and prices.
Identified cancellation transactions.
Removed problematic records according to defined business rules.
Converted date fields to datetime.
Created transaction-level features.
Cleaning results
Original rows: 541,909
Cleaned rows: 392,692
Rows removed: 149,217
Retention: 72.46%
New features
TotalAmount
Year
Month
Day
Hour
Output

The cleaned transaction dataset was used as the foundation for the remaining internship tasks.

Task 2 — Exploratory Data Analysis & Visualization
Objective

Explore the cleaned dataset to identify important business and customer patterns through statistical analysis and visualization.

Analysis performed
Descriptive statistics
Monthly transaction trends
Country-level transaction analysis
Product quantity analysis
Product transaction-value analysis
Customer purchasing behavior
Purchase frequency analysis
Correlation analysis
Key results
Total transaction amount: approximately £8.89 million
Total quantity sold: 5,152,002
Unique customers: 4,338
Unique invoices: 18,532
Unique products: 3,665
Countries: 37
Important findings
November 2011 recorded the highest monthly transaction amount.
The United Kingdom contributed the largest transaction amount.
Customer purchase frequency showed a long right-tailed distribution.
Quantity and TotalAmount showed a strong relationship because TotalAmount is mathematically derived from quantity and unit price.
Task 3 — Customer Segmentation using RFM & K-Means
Objective

Identify different customer behavior patterns using RFM analysis and K-Means clustering.

RFM Metrics
Metric	Meaning
Recency	How recently a customer purchased
Frequency	Number of unique invoices
Monetary	Total transaction amount

The RFM features were log-transformed and standardized before clustering.

Cluster selection

K-Means models were evaluated using:

Elbow Method
Silhouette Score

Final configuration:

Number of clusters: 2
Silhouette Score: 0.4328
Cluster profile
Cluster	Customers	Avg Recency	Avg Frequency	Avg Monetary
0	2,672	134.09	1.67	£495.59
1	1,666	25.89	8.44	£4,539.60

The clustering results provide a descriptive view of different customer engagement and purchasing-value patterns.

Task 4 — Supervised Learning Model Implementation
Objective

Predict whether a customer will make a future purchase using supervised machine-learning techniques.

The problem was formulated as a binary classification task.

Target
0 → No future repeat purchase
1 → Future repeat purchase

A chronological cutoff of 1 September 2011 was used to separate historical customer behavior from future purchasing activity.

Features
Recency
Frequency
Monetary
TotalQuantity
UniqueProducts
AvgOrderValue
Models
Logistic Regression
Random Forest
Results
Model	Accuracy	Precision	Recall	F1-Score	ROC-AUC
Logistic Regression	68.52%	73.95%	71.87%	72.89%	73.44%
Random Forest	63.86%	69.31%	69.31%	69.31%	70.01%

The models were evaluated using multiple metrics to provide a more complete assessment of classification performance.

Task 5 — Deep Learning Application
Objective

Apply deep learning to the same repeat-purchase prediction problem using TensorFlow/Keras.

ANN Architecture
Input Layer
6 Features
      ↓
Dense Layer
128 Neurons + ReLU
      ↓
Dropout
30%
      ↓
Dense Layer
64 Neurons + ReLU
      ↓
Dropout
20%
      ↓
Dense Layer
32 Neurons + ReLU
      ↓
Output Layer
1 Neuron + Sigmoid
Training configuration
Parameter	Value
Framework	TensorFlow / Keras
Optimizer	Adam
Loss	Binary Cross-Entropy
Maximum Epochs	100
Batch Size	32
Early Stopping	Enabled
Dropout	30% and 20%
Total Parameters	11,265
Training
Best validation-loss epoch: 13
Total epochs trained: 23
Best validation loss: 0.5922
Final ANN test results
Metric	Result
Accuracy	68.22%
Precision	73.94%
Recall	71.10%
F1-Score	72.49%
ROC-AUC	74.02%

The ANN provides a deep-learning benchmark for the same customer prediction problem and allows comparison with the classical models from Task 4.

Task 6 — Integrative Capstone Project
Objective

Combine the complete Data Science workflow developed during the internship into one end-to-end capstone project.

The capstone integrates:

Data acquisition
Data cleaning
Feature engineering
Exploratory analysis
RFM analysis
K-Means clustering
Logistic Regression
Random Forest
Artificial Neural Network
Model evaluation
Integrated customer analysis
Business insights
Recommendations
Capstone workflow
Raw Online Retail Data
        ↓
Data Cleaning
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
RFM Customer Segmentation
        ↓
K-Means Clustering
        ↓
Repeat-Purchase Target
        ↓
Logistic Regression
        ↓
Random Forest
        ↓
Artificial Neural Network
        ↓
Unified Evaluation
        ↓
Segment + Repeat-Purchase Analysis
        ↓
Insights & Recommendations
Integrated analysis

The capstone combines customer segmentation with repeat-purchase behavior to provide a more complete view of customer activity.

This makes it possible to examine relationships between:

Customer engagement
Historical purchasing value
Purchase frequency
Recency
Future repeat purchasing
📈 Overall Model Comparison

The final predictive models produced the following recorded test-set results:

Model	Accuracy	Precision	Recall	F1-Score	ROC-AUC
Logistic Regression	68.52%	73.95%	71.87%	72.89%	73.44%
Random Forest	63.86%	69.31%	69.31%	69.31%	70.01%
Artificial Neural Network	68.22%	73.94%	71.10%	72.49%	74.02%

The results show that the three approaches capture the customer behavior signal differently. The ANN achieved the highest recorded ROC-AUC, while Logistic Regression produced slightly higher accuracy and F1-score.

This comparison also demonstrates that increased model complexity does not automatically result in a large performance improvement on a relatively small, engineered tabular dataset.

💼 Business Insights

The complete internship project provides several customer-analytics insights that could potentially support business decision-making.

Customer segmentation

RFM and K-Means clustering reveal groups with different purchasing engagement and monetary behavior.

Repeat-purchase prediction

Historical customer behavior contains predictive information about future purchasing activity.

Customer retention

Predicted repeat-purchase probabilities can potentially support customer-retention analysis and prioritization.

Personalized marketing

Different customer segments may require different engagement strategies.

Data-driven decision support

Combining segmentation and prediction can provide a more detailed customer profile than either approach alone.

Model outputs should be treated as decision-support information rather than automatic decisions, and controlled experiments would be required to determine whether specific interventions actually cause improved customer outcomes.

⚠️ Challenges Encountered

Several practical challenges were addressed throughout the internship:

Data quality

The raw dataset contained missing values, duplicate records, cancellation transactions and invalid numerical values.

Skewed distributions

Customer monetary values, purchase frequency and quantities were highly skewed.

Data leakage

Repeat-purchase prediction required strict separation of historical and future information.

Overfitting

The ANN was monitored using a validation set, dropout and early stopping.

Model comparison

Multiple evaluation metrics were used instead of relying only on accuracy.

Interpretability

The project considered the trade-off between the flexibility of more complex models and the interpretability of simpler models.

✅ Skills Developed

Through the internship, practical experience was developed in:

Python programming
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
TensorFlow
Keras
Data cleaning
Exploratory Data Analysis
Data visualization
Feature engineering
RFM analysis
K-Means clustering
Classification
Artificial Neural Networks
Model evaluation
Data leakage prevention
Overfitting control
Business-oriented data interpretation
Technical documentation
🛠️ Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
TensorFlow
Keras
Google Colab
Jupyter Notebook
Microsoft Word
GitHub
📁 Repository Structure
YuvaIntern-Data-Science-Internship/
│
├── README.md
│
├── Task-1-Data-Cleaning/
│   ├── README.md
│   ├── Task_1_Data_Cleaning.ipynb
│   └── Internship_Task_1_Data_Cleaning_Preprocessing_Report.docx
│
├── Task-2-EDA-Visualization/
│   ├── README.md
│   ├── Task_2_EDA.ipynb
│   └── Task_2_EDA_Report.docx
│
├── Task-3-Clustering-Analysis/
│   ├── README.md
│   ├── Task_3_Customer_Segmentation_KMeans.ipynb
│   ├── customer_rfm_clusters.csv
│   └── YuvaIntern_Task_3_Customer_Segmentation_KMeans_Report.docx
│
├── Task-4-Supervised-Learning-Model-Implementation/
│   ├── README.md
│   ├── Task_4_Supervised_Learning.ipynb
│   └── YuvaIntern_Task_4_Supervised_Learning_Report.docx
│
├── Task-5-Deep-Learning/
│   ├── README.md
│   ├── Task_5_Deep_Learning_ANN.ipynb
│   ├── task5_customer_repeat_purchase_ann.keras
│   ├── task5_ann_predictions.csv
│   ├── task5_ann_architecture.png
│   └── YuvaIntern_Task_5_Deep_Learning_Report.docx
│
└── Task-6-Integrative-Capstone/
    ├── README.md
    ├── Task_6_Integrative_Capstone_Customer_Analytics.ipynb
    ├── YuvaIntern_Task_6_Integrative_Capstone_Report.docx
    │
    ├── data/
    │   └── task6_cleaned_online_retail.csv
    │
    └── outputs/
        ├── task6_customer_segments.csv
        ├── task6_model_comparison.csv
        ├── task6_segment_repeat_purchase_analysis.csv
        ├── task6_integrated_customer_profile.csv
        └── task6_recommendations.csv
📌 Key Project Statistics
Category	Result
Original transaction rows	541,909
Cleaned transaction rows	392,692
Customers analyzed	4,338
Unique products	3,665
Unique invoices	18,532
Countries	37
K-Means clusters	2
K-Means silhouette score	0.4328
Predictive modeling customers	3,317
ANN parameters	11,265
ANN test accuracy	68.22%
ANN test F1-score	72.49%
ANN test ROC-AUC	74.02%
🔬 Future Improvements

Potential extensions to the project include:

More advanced feature engineering
Multiple chronological validation windows
Hyperparameter optimization
Better probability calibration
Product-category and basket-level features
Customer purchase-interval features
Model explainability using SHAP or permutation importance
Evaluation on larger and more recent datasets
Testing model-driven customer strategies using controlled experiments
🎓 Final Outcome

This internship provided practical experience in designing and implementing a complete Data Science workflow using Python.

The project progressed from:

Data → Cleaning → Exploration → Segmentation → Prediction → Deep Learning → Evaluation → Business Insights

The final capstone demonstrates how different Data Science methods can be combined to understand customer behavior, identify meaningful customer segments, predict repeat purchasing behavior, and communicate analytical results through structured documentation.

Internship

YuvaIntern – Data Science Internship

Tasks Completed

Task 1: Data Acquisition, Cleaning & Preprocessing
Task 2: Exploratory Data Analysis & Visualization
Task 3: Unsupervised Learning & Customer Segmentation
Task 4: Supervised Learning Model Implementation
Task 5: Deep Learning Application in Data Science
Task 6: Integrative Capstone Project & Evaluation

⭐ Repository Focus

Customer Analytics | Machine Learning | Deep Learning | Python | End-to-End Data Science
