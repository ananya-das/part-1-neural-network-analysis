# part-1-neural-network-analysis
Bitsom part-1-neural-network-analysis assignment for Ananya Das

# Customer Churn Prediction Using Neural Networks

## Project Overview

This project shows how to use a neural network for supervised learning on structured data.
The dataset used in this project contains customer information and the target variable `churn`, which indicates whether a customer left the service.

## Dataset File
`customer_churn_nn.csv`

## Dataset Source link: https://drive.google.com/drive/folders/1Aihn49cUYMjCgeCTFBTyprjrgZO3UY6r

## Target Variable
- `churn`
    - `1` = Customer churned
    - `0` = Customer retained

## Feature Types

### Categorical Features
- region
- plan_type
- contract_type
- payment_method

### Numerical Features
- tenure_months
- monthly_charges_inr
- avg_login_days_per_month
- support_tickets_last_90_days
- payment_delay_days
- data_usage_gb
- satisfaction_score
- last_complaint_days_ago
- discount_percent
- autopay_enabled
- referral_count

### Identifier Column
- customer_id

The `customer_id` column was removed because it does not help in prediction.

# Task 1 - Dataset Understanding

The first step involved exploring the dataset to understand its structure and contents.

## Steps Performed

- Loaded the dataset using Pandas
- Checked:
    - Number of rows and columns
    - Data types
    - Missing values
    - Statistical summary
- Analyzed the target variable distribution

## Findings

- The dataset contains both categorical and numerical features.
- No missing values were found.
- The target variable was highly imbalanced:
    - Most customers were retained
    - Only a small number churned

This imbalance affects model learning and evaluation.

---

# Task 2 - Data Preprocessing

Data preprocessing was performed to prepare the dataset for neural network training.

## Preprocessing Steps

### 1. Removed Identifier Column
The `customer_id` column was dropped.

### 2. Handled Missing Values
Although no missing values existed, preprocessing pipelines were created using:
- Median imputation for numerical features
- Most frequent value imputation for categorical features

### 3. Encoded Categorical Variables
Categorical columns were converted into numerical format using:
- One-Hot Encoding

Example:

| Plan Type | Encoded |
|------------|----------|
| Basic | [1,0,0] |
| Premium | [0,1,0] |

### 4. Feature Scaling
Numerical features were standardized using:
- StandardScaler

This improves neural network convergence because all features become comparable in scale.

### 5. Train-Test Split
The dataset was divided into:
- 80% Training Data
- 20% Testing Data

---

# Task 3 - Neural Network Model Building

A feed-forward neural network was built using:
- Scikit-learn `MLPClassifier`

## Model Architecture

### Input Layer
Receives all processed features.

### Hidden Layer
- 32 neurons
- ReLU activation function

### Output Layer
- Single output node for binary classification

## Activation Function Used
- ReLU (`Rectified Linear Unit`)

Formula:

f(x) = max(0, x)

ReLU introduces non-linearity, allowing the model to learn complex patterns.

## Optimizer
The model internally uses gradient-based optimization for learning.

---

# Task 4 - Training and Evaluation

The neural network was trained using the training dataset and evaluated on the testing dataset.

## Evaluation Metrics Used

- Training Accuracy
- Testing Accuracy
- Confusion Matrix
- Classification Report

## Observations

- The model achieved high accuracy.
- Most retained customers were correctly predicted.
- Churn prediction was slightly difficult because of dataset imbalance.

## Confusion Matrix
The confusion matrix was used to visualize:
- Correct predictions
- Incorrect predictions
- False positives
- False negatives

---

# Task 5 - Hyperparameter Experimentation

Three different experiments were performed to understand how neural network parameters affect performance.

---

## Experiment 1 - Baseline Model

### Configuration
- Hidden Layers: (32)
- Activation: ReLU
- Learning Rate: 0.001
- Batch Size: 32
- Epochs: 100

### Purpose
This experiment served as the baseline model with a simple architecture.

---

## Experiment 2 - Deeper Network

### Configuration
- Hidden Layers: (64, 32)
- Activation: ReLU
- Learning Rate: 0.001
- Batch Size: 32
- Epochs: 150

### Purpose
This experiment tested whether adding more hidden layers improves learning capability.

### Observation
- Higher training accuracy
- Slight drop in testing accuracy
- Mild overfitting observed

---

## Experiment 3 - Different Activation Function

### Configuration
- Hidden Layers: (64)
- Activation: tanh
- Learning Rate: 0.01
- Batch Size: 64
- Epochs: 100

### Purpose
This experiment tested:
- Different activation function
- Higher learning rate

### Observation
- Faster learning
- Slight reduction in generalization performance

---

# Experiment Comparison

| Experiment | Hidden Layers | Activation | Learning Rate | Batch Size | Epochs |
|------------|---------------|------------|---------------|------------|--------|
| Exp 1 | (32) | relu | 0.001 | 32 | 100 |
| Exp 2 | (64,32) | relu | 0.001 | 32 | 150 |
| Exp 3 | (64) | tanh | 0.01 | 64 | 100 |

---

# Task 6 - Final Reflection

## Role of Weights and Biases

### Weights
Weights determine how strongly each input feature affects the prediction.

### Biases
Biases help shift activation values and improve model flexibility.

---

## Why Activation Functions Are Required

Activation functions introduce non-linearity.

Without activation functions:
- The neural network behaves like a linear model
- Complex patterns cannot be learned

---

## Learning Rate Effects

### Learning Rate Too High
- Training becomes unstable
- Loss fluctuates

### Learning Rate Too Low
- Training becomes very slow
- Convergence takes longer

---

## Underfitting vs Overfitting

### Underfitting
Occurs when the model is too simple and fails to learn patterns.

### Overfitting
Occurs when the model memorizes training data instead of generalizing.

Some experiments showed mild overfitting because:
- Training accuracy became extremely high
- Testing accuracy slightly decreased

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

---

# Files Included

| File | Description |
|------|-------------|
| customer_churn_nn.csv | Dataset |
| notebook.ipynb | Jupyter Notebook implementation |
| README.md | Project explanation |
