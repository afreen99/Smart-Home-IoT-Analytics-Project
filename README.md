# Smart-Home-IoT-Analytics-Project
A data science and analytics project on a pre-built SQLite database (.db) representing a realistic business domain (smart home IoT) integrating database skills, SQL analytics, data engineering logic, machine learning, and business storytelling.

## 📋 Project Overview
This project explores smart home IoT device data to:
- Predict device failures using various machine learning models and advanced SQL-based feature engineering
- Identify patterns in sensor readings and alerts and visualize insights in an interactive Plotly dashboard

## 🗂️ Project Structure
```
📂 Smart-Home-IoT-Analytics-Project/
├── 📄 README.md
├── 📁 Code/
│ ├── 📄 AD599_Smart_Home_IoT_project.ipynb
├── 📁 Data/
│ ├── 💾 smart_home.db
│ └── 📄 About SMART HOME IoT.pdf
└── 📄 requirements.txt
```

## 📊 Database Schema
The smart_home.db SQLite database contains four main tables:
- homes (200 records): Home information including city, type, and ownership details
- devices (925 records): Smart home devices with installation dates and status
- sensor_readings (222,000 records): Time-series sensor data from devices
- alerts (77 records): Alert notifications with severity levels

## 🤖 Machine Learning Models
### Models Implemented

1. Logistic Regression (Baseline) ⭐ Best Performance
   - Accuracy: 80.0%
   - AUC-ROC: 0.815
   - F1-Score: 0.554

2. Random Forest
   - Accuracy: 73.0%
   - AUC-ROC: 0.780
   - F1-Score: 0.07

3. Gradient Boosting
   - Accuracy: 76.8%
   - AUC-ROC: 0.789
   - F1-Score: 0.394
     
### Key Features

The model uses multiple SQL-engineered features including:
- Device age
- Sensor reading statistics
- Alert history
- Home-level metrics
- Recent activity patterns

## 📈 Key Insights
### Building The Models
- Stratified K-Fold cross-validation was used with GridSearchCV for hyperparameter tuning while ensuring that each fold maintains the same class distribution as the original dataset (important for our imbalanced dataset), which is crucial for classification models like Random Forest and Gradient Boost. This prevents bias and leads to a more reliable estimate of the model's performance.
### Feature Importance

- Home-level metrics are strongest predictors
- Recent activity patterns (last 7 days) highly informative
- Device type and location play secondary roles
- Device age is a significant but not dominant predictor

### Model Analysis - Why may Logistic Regression have outperformed?
- Better Generalization on Small Data
    - Decision trees (the building blocks of Random Forest and Gradient Boosting) require a sufficient number of observations in both classes to make stable splits. Since the dataset was highly imbalanced and small, the tree-based models may have struggled to form meaningful rules for the minority class (failed device), leading to poor generalization and potential overfitting.

## 🎨 Visualizations

As part of the project an interactive Plotly dashboard was generated which provides business insights such as:
- Failure rates by device type
- Alerts by city and home type
- Daily alert trends
- Device installation patterns

## 🚀 Getting Started
### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook
- SQLite3

### Installation

1. Clone the repository:
```git clone https://github.com/afreen99/Smart-Home-IoT-Analytics-Project.git```

3. Install required packages:
```pip install -r requirements.txt```

4. Launch Jupyter Notebook:
```jupyter notebook Code/AD599_Smart_Home_IoT_project.ipynb```

### Running the Analysis
1. Open ```AD599_Smart_Home_IoT_project.ipynb``` in Jupyter
2. Ensure ```smart_home.db``` is in the Data folder (or update the DB_PATH variable)
3. Run all cells sequentially (Cell → Run All)

The notebook will:

- Connect to the database
- Perform SQL-based feature engineering
- Train and evaluate ML models
- Generate Plotly dashboard
