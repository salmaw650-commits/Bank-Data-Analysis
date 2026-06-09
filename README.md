Banking Transactions Data Analysis Project
📌 Overview

This project focuses on Exploratory Data Analysis (EDA) and data cleaning for a banking transactions dataset.
The goal is to explore customer behavior, understand transaction patterns, and identify relationships between features such as payment methods, transaction time, and account activity.

📂 Dataset

The dataset contains banking transaction records including:

Transaction details
Account behavior
Payment channels
Authentication methods
Transaction timing
Risk-related indicators
🛠️ Tools & Libraries Used
Python 🐍
Pandas
NumPy
Matplotlib
Seaborn
📥 Data Loading

The dataset is loaded using Pandas:

df = pd.read_csv("banking_transactions.csv")
🔍 Exploratory Data Analysis (EDA)
1. Basic Understanding
Display dataset shape
Check data types using info()
Summary statistics using describe()
View columns and sample data using head() and tail()
2. Data Filtering

Performed filtering to analyze specific conditions:

Filtering by payment channel (e.g., ATM)
Filtering based on account age and transaction behavior

Example:

df[df['payment_channel'] == 'ATM']
3. Value Analysis
Count unique values using value_counts()
Identify number of unique categories using nunique()

Applied to:

payment_channel
authentication_type
geo_distance_km
daily_transaction_count
4. Missing Values & Duplicates
Checked missing values using isnull().sum()
Detected duplicate rows
Removed duplicates from dataset
df = df.drop_duplicates()
5. Data Type Cleaning

Converted incorrect data types:

df['avg_monthly_balance'] = pd.to_numeric(df['avg_monthly_balance'], errors='coerce')
6. Feature Engineering / Column Removal

Removed irrelevant or precomputed risk features:

df.drop([
    'transaction_velocity_score',
    'anomaly_score',
    'device_risk_score',
    'transfer_frequency'
], axis=1)
7. Data Visualization
Correlation Analysis

Used heatmap to understand relationships between numerical features:

sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
Relationship Visualization

Scatter plot example:

plt.scatter(df['transfer_frequency'], df['transaction_time_hour'])
📊 Key Insights
Payment channels show different transaction patterns.
Account age and transaction behavior are related.
Some precomputed risk scores were removed to focus on raw data.
Correlation analysis helps identify relationships between features.
Duplicate data was successfully removed to improve data quality.
🧹 Data Cleaning Steps Summary
Removed duplicate rows
Handled incorrect data types
Dropped irrelevant features
Checked missing values
Ensured dataset consistency
