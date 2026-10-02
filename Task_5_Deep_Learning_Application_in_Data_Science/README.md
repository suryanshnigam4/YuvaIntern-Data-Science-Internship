
Task 5 – Deep Learning Application in Data Science

Customer Repeat-Purchase Prediction using an Artificial Neural Network

This project implements a Deep Learning classification model using TensorFlow/Keras to predict whether a customer will make a repeat purchase based on historical purchasing behavior.

The project continues the same Online Retail analysis developed in the previous internship tasks:

Task 1 → Data Cleaning → Task 2 → EDA & Visualization → Task 3 → Customer Segmentation → Task 4 → Supervised Learning → Task 5 → Deep Learning

📌 Objective

The objective of this task is to:

Understand the fundamentals of deep learning.

Design and implement an Artificial Neural Network (ANN).

Apply the ANN to a real-world customer analytics problem.

Train, validate and evaluate the neural network using appropriate metrics.

Analyze overfitting and apply regularization techniques.

Compare the ANN with classical machine-learning models from Task 4.

Discuss practical business implications, limitations and possible improvements.

🧩 Problem Statement

The problem is formulated as a binary classification task.

The model uses customer purchasing behavior observed before 1 September 2011 to predict whether the customer makes at least one purchase during the future period beginning 1 September 2011.

Target

Value

Meaning

0

Customer did not make another purchase

1

Customer made another purchase

The temporal split ensures that future purchase information is not used as an input feature, helping reduce target leakage.

📊 Dataset

The project uses the public Online Retail transaction dataset.

Original dataset

Rows: 541,909

Columns: 8

After cleaning and preprocessing

Rows: 392,692

Columns: 13

Unique customers: 4,338

Unique invoices: 18,532

Unique countries: 37

Modeling dataset

After applying the historical/future time split and creating customer-level features:

Customers: 3,317

Repeat purchasers: 1,952 (58.85%)

Non-repeat customers: 1,365 (41.15%)

🧹 Data Preparation

The same validated preprocessing pipeline from the earlier internship tasks was used.

The cleaning process included:

Removing duplicate rows.

Removing records with missing Description.

Removing records with missing CustomerID.

Removing cancellation invoices.

Removing transactions with non-positive Quantity.

Removing transactions with non-positive UnitPrice.

Converting CustomerID to integer.

Creating TotalAmount = Quantity × UnitPrice.

Extracting date/time features from InvoiceDate.

🕒 Leakage-Controlled Temporal Split

A cutoff date of:

2011-09-01

was used.

Period

Rows

Purpose

Historical period

224,036

Feature engineering

Future period

168,656

Target construction only

Historical customer behavior was used as the model input, while future activity was used only to define RepeatPurchase.

🔧 Features Used

Six customer-level behavioral features were created.

Feature

Description

Recency

Days since the customer's latest historical purchase

Frequency

Number of unique historical invoices

Monetary

Total historical transaction amount

TotalQuantity

Total quantity purchased

UniqueProducts

Number of distinct products purchased

AvgOrderValue

Monetary value divided by purchase frequency

📐 Feature Transformation

The customer-level variables were highly right-skewed, particularly monetary and quantity-based features.

A log transformation was applied:

X_log = np.log1p(X)

The transformed data was then standardized using:

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

The scaler was fitted only on the training data to avoid information leakage.

🧠 ANN Architecture

The neural network used in this project is:

Input Layer
6 Features
      ↓
Dense Layer
128 neurons + ReLU
      ↓
Dropout
30%
      ↓
Dense Layer
64 neurons + ReLU
      ↓
Dropout
20%
      ↓
Dense Layer
32 neurons + ReLU
      ↓
Output Layer
1 neuron + Sigmoid

Architecture summary

Layer

Configuration

Input

6 features

Dense 1

128 neurons, ReLU

Dropout 1

30%

Dense 2

64 neurons, ReLU

Dropout 2

20%

Dense 3

32 neurons, ReLU

Output

1 neuron, Sigmoid

Total parameters: 11,265
Trainable parameters: 11,265
Non-trainable parameters: 0

⚙️ Training Configuration

Hyperparameter

Value

Framework

TensorFlow / Keras

Optimizer

Adam

Loss function

Binary Cross-Entropy

Maximum epochs

100

Batch size

32

Activation

ReLU + Sigmoid

Early stopping

Enabled

Patience

10 epochs

Restore best weights

True

Early Stopping Result

Total epochs trained: 23

Best epoch: 13

Best validation loss: 0.59217

Early stopping prevented unnecessary training after validation loss stopped improving.

📈 Final ANN Test Results

The model was evaluated on a completely held-out test set containing 664 customers.

Metric

ANN Result

Test Loss

0.5798

Accuracy

68.22%

Precision

73.94%

Recall

71.10%

F1-Score

72.49%

ROC-AUC

74.02%

Classification Report

Class

Precision

Recall

F1-Score

Support

No Repeat (0)

0.61

0.64

0.62

273

Repeat (1)

0.74

0.71

0.72

391

Overall Accuracy

—

—

0.68

664

🔄 Comparison with Task 4 Models

The ANN was compared with the Logistic Regression and Random Forest models developed in Task 4.

Model

Accuracy

Precision

Recall

F1-Score

ROC-AUC

Logistic Regression

68.52%

73.95%

71.87%

72.89%

73.44%

Random Forest

63.86%

69.31%

69.31%

69.31%

70.01%

Artificial Neural Network

68.22%

73.94%

71.10%

72.49%

74.02%

Key Observation

The ANN achieved the highest recorded ROC-AUC (74.02%), while Logistic Regression produced slightly higher accuracy and F1-score.

This indicates that the six engineered customer-level features already contain considerable predictive signal, so increasing model complexity does not automatically produce a large improvement.

🔍 Overfitting and Regularization

Several techniques were used to control overfitting:

Dropout

Two dropout layers were added:

30% after the first dense layer.

20% after the second dense layer.

Early Stopping

Validation loss was monitored during training.

EarlyStopping(
    monitor="val_loss",
    patience=10,
    restore_best_weights=True
)

The model stopped at epoch 23, while the best validation-loss weights came from epoch 13.

Log Transformation

log1p() reduced the influence of highly skewed customer values.

Validation Set

A separate validation set was used for monitoring generalization during training.

✅ Strengths

Complete end-to-end deep-learning workflow.

Leakage-aware temporal target construction.

Appropriate ANN architecture for binary classification.

Log transformation for skewed customer features.

Standardized inputs.

Dropout and early stopping for regularization.

Multiple evaluation metrics instead of accuracy alone.

Direct comparison with classical machine-learning models.

Includes training-history and diagnostic analysis.

⚠️ Limitations

The modeling dataset contains only 3,317 customers, which is relatively small for deep learning.

Only six engineered customer-level features were used.

The prediction target depends on a single historical cutoff and future period.

Performance may vary under a different prediction horizon.

Only one held-out test split was used for the final evaluation.

The 0.50 classification threshold may not be optimal for every business objective.

ANN predictions are less interpretable than simple linear-model coefficients without additional explainability methods.

🚀 Possible Improvements

Future versions of the project could include:

Rolling or multiple temporal validation windows.

Hyperparameter tuning for layer sizes, dropout rates, learning rate and batch size.

Threshold optimization based on business costs.

Additional temporal features such as purchase intervals and recent purchase trends.

Product-category and basket-level features.

Probability calibration.

Explainability methods such as SHAP or permutation importance.

More advanced architectures if a larger feature set or larger customer dataset becomes available.

💼 Business Implications

The predicted repeat-purchase probability could potentially support:

Customer retention analysis.

Marketing campaign prioritization.

Personalized offers.

Customer follow-up strategies.

Combining predicted behavior with RFM customer segments from Task 3.

However, the model only predicts future behavior. It does not establish that a marketing intervention will cause a customer to purchase. Controlled experiments such as A/B testing would be required to measure the causal impact of model-driven campaigns.

🛠️ Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

TensorFlow

Keras

Scikit-learn

Jupyter Notebook / Google Colab

📁 Project Files

Recommended repository structure:

Task-5-Deep-Learning/
│
├── README.md
├── Task_5_Deep_Learning_ANN.ipynb
├── task5_customer_repeat_purchase_ann.keras
├── task5_ann_predictions.csv
├── task5_ann_architecture_diagram.png
└── YuvaIntern_Task_5_Deep_Learning_Report.docx

▶️ How to Run

Open the notebook in Google Colab or Jupyter Notebook.

Upload the Online Retail.xlsx dataset.

Install/import the required Python libraries.

Run the cells sequentially from data loading through model evaluation.

The notebook performs preprocessing, feature engineering, model training, validation and testing.

Save the trained model and predictions after successful execution.

📌 Final Outcome

This task demonstrates a complete application of deep learning to tabular customer analytics, from data preparation and leakage prevention to ANN design, training, evaluation, diagnostic analysis and comparison with traditional machine-learning approaches.

The final ANN achieved:

68.22% Accuracy | 72.49% F1-Score | 74.02% ROC-AUC

The project demonstrates that neural networks can provide useful predictive performance on engineered customer-behavior data while also highlighting the importance of model validation, regularization, interpretability and critical comparison with simpler models.

Internship Task

YuvaIntern Data Science Internship — Week 5: Deep Learning Application in Data Science
