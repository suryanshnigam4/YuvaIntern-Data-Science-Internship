
Task 6 – Integrative Capstone Project and Evaluation
End-to-End Customer Analytics and Repeat-Purchase Prediction

This final capstone project integrates the key Data Science techniques developed throughout the internship into a complete end-to-end workflow using the Online Retail transaction dataset.

The project covers data acquisition, data cleaning, exploratory data analysis, customer segmentation, supervised machine learning, deep learning, model evaluation, integrated customer analysis, and recommendations.

📌 Project Objective

The main objective is to demonstrate a complete Data Science pipeline using Python, starting from raw transaction data and ending with meaningful analytical insights and recommendations.

The project addresses two major customer-analytics questions:

What different customer behavior patterns exist?
Can historical customer behavior be used to predict whether a customer will purchase again?
🔄 Complete Data Science Pipeline
Data Acquisition
       ↓
Data Cleaning & Preprocessing
       ↓
Feature Engineering
       ↓
Exploratory Data Analysis
       ↓
RFM Analysis
       ↓
K-Means Customer Segmentation
       ↓
Repeat-Purchase Target Creation
       ↓
Logistic Regression
       ↓
Random Forest
       ↓
Artificial Neural Network
       ↓
Model Evaluation & Comparison
       ↓
Integrated Customer Analysis
       ↓
Insights & Recommendations
📊 Dataset

The project uses the public Online Retail dataset containing retail transaction records.

Original Dataset
Rows: 541,909
Columns: 8
Original Columns
InvoiceNo
StockCode
Description
Quantity
InvoiceDate
UnitPrice
CustomerID
Country
🧹 Data Cleaning

The raw dataset contained several data-quality issues, including missing values, duplicate records, cancellation transactions and invalid quantities/prices.

The following preprocessing steps were performed:

Removed duplicate rows.
Removed records with missing Description.
Removed records with missing CustomerID.
Removed cancellation invoices.
Removed transactions with Quantity <= 0.
Removed transactions with UnitPrice <= 0.
Converted InvoiceDate to datetime.
Converted CustomerID to integer.
Created TotalAmount = Quantity × UnitPrice.
Final Cleaned Dataset
Rows: 392,692
Columns: 13
Retention: 72.46%

Additional engineered columns:

TotalAmount
Year
Month
Day
Hour
📈 Exploratory Data Analysis

EDA was performed to understand transaction, customer, product and geographic patterns.

The analysis included:

Overall transaction and customer statistics
Monthly transaction trends
Country-level transaction amounts
Product quantity analysis
Customer purchase frequency
Correlation analysis
Key findings
Total transaction amount: approximately £8.89 million
Total quantity sold: 5,152,002 units
Unique customers: 4,338
Unique invoices: 18,532
Unique products: 3,665
Countries represented: 37
Highest monthly transaction amount occurred in November 2011.
The United Kingdom contributed the largest transaction amount.
Customer purchase frequency showed a long right-tailed distribution.
👥 Customer Segmentation

Customer segmentation was performed using RFM analysis and K-Means clustering.

RFM Components
Metric	Meaning
Recency	How recently a customer purchased
Frequency	Number of unique invoices
Monetary	Total transaction amount

Because RFM variables were skewed, log1p() transformation and StandardScaler were applied before clustering.

Cluster Selection

K-Means models were tested for multiple values of K using:

Elbow Method
Silhouette Score

The selected model used:

K = 2
Silhouette Score = 0.4328
Cluster Profile
Cluster	Customers	Avg Recency	Avg Frequency	Avg Monetary
0	2,672	134.09	1.67	£495.59
1	1,666	25.89	8.44	£4,539.60

The clusters represent different patterns of customer engagement and historical purchasing value.

🎯 Repeat-Purchase Prediction

A second analytical objective was to predict whether a customer would make another purchase.

A chronological cutoff of:

1 September 2011

was used.

Historical Period
2010-12-01 → 2011-08-31

Used for feature engineering.

Future Period
2011-09-01 → 2011-12-09

Used only to define the target.

This approach prevents future purchase behavior from being included in the predictive features.

Target
Value	Meaning
0	No future purchase
1	At least one future purchase

Modeling dataset:

3,317 customers
1,952 repeat customers (58.85%)
1,365 non-repeat customers (41.15%)
🔧 Predictive Features

Six historical customer-level features were used:

Recency
Frequency
Monetary
TotalQuantity
UniqueProducts
AvgOrderValue

The features were log-transformed using:

X_log = np.log1p(X)

and standardized using StandardScaler.

🤖 Machine Learning Models

Three predictive approaches were evaluated.

1. Logistic Regression

Used as a classical linear classification baseline.

2. Random Forest

Used to capture nonlinear relationships and provide feature-importance information.

3. Artificial Neural Network

Implemented using TensorFlow/Keras to provide a deep-learning approach.

🧠 Artificial Neural Network

Architecture:

Input: 6 Features
       ↓
Dense: 128 neurons + ReLU
       ↓
Dropout: 30%
       ↓
Dense: 64 neurons + ReLU
       ↓
Dropout: 20%
       ↓
Dense: 32 neurons + ReLU
       ↓
Dense: 1 neuron + Sigmoid
Training Configuration
Parameter	Value
Framework	TensorFlow / Keras
Optimizer	Adam
Loss	Binary Cross-Entropy
Maximum epochs	100
Batch size	32
Early stopping	Enabled
Patience	10
Total parameters	11,265

The best validation-loss epoch was 13, and training stopped after 23 epochs due to early stopping.

📊 Final Model Evaluation
Model	Accuracy	Precision	Recall	F1-Score	ROC-AUC
Logistic Regression	68.52%	73.95%	71.87%	72.89%	73.44%
Random Forest	63.86%	69.31%	69.31%	69.31%	70.01%
Artificial Neural Network	68.22%	73.94%	71.10%	72.49%	74.02%
ANN Test Results
Accuracy  : 68.22%
Precision : 73.94%
Recall    : 71.10%
F1-Score  : 72.49%
ROC-AUC   : 74.02%

The ANN achieved the highest recorded ROC-AUC in this experiment, while Logistic Regression produced slightly higher accuracy and F1-score.

These results demonstrate that greater model complexity does not automatically guarantee a large performance improvement on a relatively small, engineered tabular dataset.

🔗 Integrated Customer Analysis

The capstone combines the segmentation results with repeat-purchase behavior to create a more complete customer view.

This allows the project to examine:

Customer engagement patterns
Historical customer value
Repeat-purchase behavior
Differences between customer segments
Potential customer-retention opportunities

This integrated analysis is the main additional component that distinguishes the capstone from the individual internship tasks.

💼 Business Insights and Recommendations

The findings can potentially support:

Customer retention analysis
Customer prioritization
Personalized marketing campaigns
Re-engagement strategies
Customer segmentation
Combining RFM segments with predicted repeat-purchase probabilities

Model outputs should be treated as decision-support information rather than automatic decisions.

Predictions alone do not establish that a particular marketing action will cause a customer to purchase. Controlled experiments such as A/B testing would be needed to evaluate causal impact.

✅ Strengths
Complete end-to-end Data Science workflow.
Consistent use of the Online Retail dataset across the internship.
Systematic data cleaning and validation.
Comprehensive EDA.
Both supervised and unsupervised learning.
Deep-learning implementation using TensorFlow/Keras.
Leakage-aware temporal target construction.
Multiple model evaluation metrics.
Integration of customer segmentation and predictive modeling.
Clear discussion of limitations and future improvements.
⚠️ Limitations
The modeling dataset contains only 3,317 customers.
Only six customer-level predictive features were used.
The repeat-purchase target is based on a specific time cutoff.
Model performance may change with a different prediction horizon.
The final predictive evaluation uses one held-out test split.
A fixed 0.50 classification threshold may not be suitable for every business objective.
Neural-network predictions require additional explainability techniques for easier interpretation.
🚀 Future Improvements

Potential future improvements include:

Multiple chronological validation periods.
Hyperparameter tuning for all predictive models.
Threshold optimization based on business costs.
Additional temporal customer features.
Product-category and basket-level features.
Probability calibration.
Explainability techniques such as SHAP or permutation importance.
Evaluation on larger and more recent customer datasets.
🛠️ Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
TensorFlow
Keras
Google Colab / Jupyter Notebook
📁 Project Structure
Task-6-Integrative-Capstone/
│
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
🎓 Learning Outcomes

This capstone strengthened practical skills in:

Data acquisition and data cleaning
Exploratory data analysis
Data visualization
Feature engineering
RFM analysis
K-Means clustering
Supervised machine learning
Artificial neural networks
Model evaluation
Data leakage prevention
Overfitting control
Business-oriented interpretation
Technical documentation and reporting
📌 Final Outcome

This capstone demonstrates a complete Data Science workflow, from raw transaction data to customer insights and predictive modeling.

The project combines:

Data Preparation → EDA → Customer Segmentation → Machine Learning → Deep Learning → Evaluation → Integrated Analysis → Recommendations

The final results show that customer purchasing behavior contains useful predictive and descriptive information, while also demonstrating the importance of careful preprocessing, leakage control, model evaluation and critical interpretation.

Internship Task

YuvaIntern Data Science Internship — Week 6: Integrative Capstone Project and Evaluation
